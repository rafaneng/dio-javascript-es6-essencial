# Introdução e orientação a objetos

## Herança

- baseada em protótipos
- prototype (variável que armazena as informações do objeto)
- __proto__ (todas as variaveis criadas no JavaScript tem essa referencia que aponta para o prototype do tipo criado)
- constructor (tipo criado, ou seja, baseado no constructor é criado um prototype e nessa variável  é armazenada a referência para o __proto__)

```jsx
const myText = 'Hello prototype!';
myText.split(''); // <- de onde vem esse "split"?

// Mesma declaracao de cima
// Ao criar o const myText é usada a função construtora chamada String e toda função construtora possui um prototype atrelado a ela e a referência do __proto__ nela
const myText = String('Hello prototype!');
console.log(myText.__proto__.split);

// Ou seja, ficaria mesma coisa que:
console.log(String.prototype.split)

// Se eu comparar os dois, teremos a afirmação verdadeira
// Basicamente, o __proto__ aponta para o prototype de String
const myText = 'Hello prototype!';
console.log(myText.__proto__.split === String.prototype.split)
// true

console.log(myText.constructor === String);
// true

// Presume-se entao que:
__proto__ -> prototype -> constructor

const myText = 'Hello prototype!';
myText.constructor -> String
myText.__proto__ -> String.prototype
```

```jsx
function Animal() {}

console.log(Animal.constructor)
// [Function: Function]

// Entenda o porque na imagem abaixo
```

![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled.png)

```jsx
function Animal(){
	this.qtdePatas = 4;
}

const cachorro = new Animal();

console.log(cachorro.qtdePatas);
// 4

/*
O que é esse new, o que ocorre quando chamamos ele?

1 - Um novo objeto é criado, herdando Animal.prototype

2-A função construtora Animalé chamada com os argumentos especificados e com o '"this'
vinculado ao novo objeto criado.

3 - Caso a função construtora tenha uma retorno explícito, será respeitado o seu
'return'. Senão, será retornado o objeto criado no passo 1.
*/

// Então, sabemos que é verdade que:
console.log(cachorro.__proto__ === Animal.prototype);
// true

console.log(Animal.__proto__ === Function.prototype);
// true

// Outra forma de comparar é pela instância:
console.log(cachorro instanceof Animal);
// true

console.log(cachorro instanceof Function);
// false

// Vendo a cadeia dos protos criada pelo new
console.log(cachorro)

/*

-- OUTPUT --

Animal {qtdePatas: 4}
qtdePatas: 4
__proto__:
constructor: ƒ Animal()
__proto__:
constructor: ƒ Object()
hasOwnProperty: ƒ hasOwnProperty()
isPrototypeOf: ƒ isPrototypeOf()
propertyIsEnumerable: ƒ propertyIsEnumerable()
toLocaleString: ƒ toLocaleString()
toString: ƒ toString()
valueOf: ƒ valueOf()
__defineGetter__: ƒ __defineGetter__()
__defineSetter__: ƒ __defineSetter__()
__lookupGetter__: ƒ __lookupGetter__()
__lookupSetter__: ƒ __lookupSetter__()
get __proto__: ƒ __proto__()
set __proto__: ƒ __proto__()

*/
```

```jsx
function Animal(qtdePatas){
	this.qtdePatas = qtdePatas;
}
function Cachorro(morde){
    Animal.call(this, 4);
    this.morde = morde;
}

const pug = new Cachorro(false)

console.log(pug)
// Cachorro { qtdePatas: 4, morde: false }
```

```jsx
function Animal(qtdePatas){
    this.qtdePatas = qtdePatas;
    this.movimentar = function(){}
}
function Cachorro(morde){
    Animal.call(this, 4);

    this.morde = morde;
    this.latir = function(){
        console.log('Au! au!');
    }
}

const pug = new Cachorro(false)
const pitbull = new Cachorro(true)

console.log(pug)
console.log(pitbull)

/*

-- OUTPUT --

Cachorro {
  qtdePatas: 4,
  movimentar: [Function],
  morde: false,
  latir: [Function]
}
Cachorro {
  qtdePatas: 4,
  movimentar: [Function],
  morde: true,
  latir: [Function]
}

*/

/* PROBLEMA: Toda vez que é dado um new Cachorro, a função latir e movimentar são
criadas novamente e isso acaba duplicando elas */

// Veja no método abaixo(mesma função do de cima) como contornar essa situação

/* Outro benefício é que ao inserir um anova propriedade(Objeto) ao prototype, a
variável mesmo que ja tenha sido instânciada, receberá a nova propriedade */

function Animal(){}

Animal.prototype.qtdePatas = 0;
Animal.prototype.movimentar = function(){}

function Cachorro(morde){
    this.qtdePatas = 4
    this.morde = morde;
}

Cachorro.prototype = Object.create(Animal);
Cachorro.prototype.latir = function(){
    console.log('Au! au!');
}

const pug = new Cachorro(false)
const pitbull = new Cachorro(true)

console.log(pug)
console.log(pitbull)
```

```jsx
// CURIOSIDADE PERIGOSA: podemos alterar implementações de prototipes nativos, exemplo do "split" do construtor String

String.prototype.split = function() {console.log('tudo nosso, perdeu playboy...');}

'123456'.split('')
// tudo nosso, perdeu playboy...
```

## Classes

- Criado no ES6
- simplificação da herança e protótipos
- palavra chave **class**
- açúcar sintático das funções

![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%201.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%201.png)

![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%202.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%202.png)

## Modificadores de acesso

- JavaScript ainda não possui
- Conhecendo um pouco de como funciona no NodeJS:

    ![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%203.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%203.png)

- Como é na versão 12 do JS:

    ![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%204.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%204.png)

## Encapsulamento

![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%205.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%205.png)

## Static

- acessar métodos/atributos sem instanciar uma classe.

    ![Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%206.png](Introduc%CC%A7a%CC%83o%20e%20orientac%CC%A7a%CC%83o%20a%20objetos%20634d0f5237c1424c923845d86b8d9f51/Untitled%206.png)