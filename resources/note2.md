# Currying, Hoisting, Imutabilidade, Tipos e Variáveis

## Currying

É uma técnica, uma maneira de transformar uma função que recebe múltiplos parâmetros de forma que ela pode ser chamada com um parâmetro apenas e para cada parâmetro é retornada uma nova função

```jsx
// Função normal sem Currying.
function soma(a, b){
    return a + b;
}

//Perceba que estamos sempre repetindo o primeiro parametro
console.log(soma(2, 2));
console.log(soma(2, 3));
console.log(soma(2, 4));
console.log(soma(2, 5));
```

```jsx
// Mesma função usando Currying
function soma(a) {
    return function(b){
        return a + b;
    }
}

const soma2 = soma(2);

console.log(soma2(2));
console.log(soma2(3));
console.log(soma2(4));
console.log(soma2(5));
```

## Hoisting

Elevação(Hoisting) é nada mais, nada menos do que trazer para o início do escopo a declaração de variáveis e funções.

### Hoisting de variaveis

eleva somente a criação da variável e nao sua atribuição

```jsx
// Função comum
function fn() {
    console.log(text);

    var text = 'Exemplo';

    console.log(text);
}

fn();

// Hosting em ação
function fn() {
   
		// variável foi içada(elevada) 
	  var text;
    console.log(text);

    var text = 'Exemplo';

    console.log(text);
}

```

### Hoisting de função

eleva a função como um todo

```jsx
function fn() {
    log('Hoisting de função')

    function log(value){
        console.log(value);
    }
}

fn();

// Hosting em ação
function fn() {
    // Elevou a função toda para o início
		function log(value){
        console.log(value);
    }
    
		log('Hoisting de função');
}
```

## Imutibilidade

Conceito de programação funcional mas presente no JavaScript. Em linguagens funcionais, dados são imutáveis. 

```jsx
const user = {
    name: 'Rafael',
    lastName: 'Santos'
};

function getUserWithFullName(user){
    return {
        ...user,
        fullName: `${user.name} ${user.lastName}`
    }
}

const userWithFullName = getUserWithFullName(user);
console.log(userWithFullName);

/*
-- Output --
{ name: 'Rafael', lastName: 'Santos', fullName: 'Rafael Santos' }
*/
```

```jsx
const students = [
    {
        name: 'Grace',
        grade: 6
    },
    {
        name: 'Jennifer',
        grade: 4
    },
    {
        name: 'Paul',
        grade: 10
    },
];

function getApprovedStudents(studentsList){
    return studentsList.filter(student => student.grade >= 7);
}

console.log('Alunos aprovados:');
console.log(getApprovedStudents(students));

console.log('\nLista de aluno:');
console.log(students);

/*
-- Output --
Alunos aprovados:
[ { name: 'Paul', grade: 10 } ]

Lista de aluno:
[
  { name: 'Grace', grade: 6 },
  { name: 'Jennifer', grade: 4 },
  { name: 'Paul', grade: 10 }
]
*/
```

## Tipos e variáveis

### Escopo

É o contexto atual de execução, em que valores e expressões são "visíveis" ou podem ser referenciadas. Se uma variável ou outra expressão não estiver "no escopo atual", então não está disponível para uso. Os escopos também podem ser em camadas em uma hierarquia, de modo que os escopos filhos tenham acesso aos escopos pais, mas não vice-versa.

```jsx
// escopo global

{
	// escopo de bloco
}

function test(){
	// escopo de função
}
```

### var

só aceita escopo de função ou escopo global, ele não respeita escopo de bloco.

```jsx
var test = 'example';

(() => {
    console.log(`Valor dentro da função "${test}"`);

    if(true){
        var test = 'example';
        console.log(`Valor dentro do if "${test}"`);
    }

    console.log(`Valor após a execução do if "${test}"`);
})();

/*
-- Output --
Valor dentro da função "undefined"
Valor dentro do if "example"
Valor após a execução do if "example"
*/
```

### let

respeitam escopo de bloco

```jsx
(() => {
    let test = 'valor da função'
    console.log(`Valor dentro da função "${test}"`);

    if(true){
        let test = 'valor if';
        console.log(`Valor dentro do if "${test}"`);
    }

    console.log(`Valor após a execução do if "${test}"`);
})();

/*
-- Output --
Valor dentro da função "valor da função"
Valor dentro do if "valor if"
Valor após a execução do if "valor da função"
*/

```

### const

o const é para ser constante porém possue algumas peculiaridades, exemplo:

- tipos primitivos não podem ter o valor alterado
- tipos por referência (objetos e arrays) que apontam pra um lugar, podem ter seus valores modificados.

```jsx

const name = 'Rafael';

// Não podemos altear o valor de tipos primitivos
name = 'Santos';

const user = {
    name: "Rafael"
};

// Mas se for um objeto(tipo por referência), podemos trocar sus propriedades
user.name = 'Outro nome';

// Não podemos fazer o objeto "apontar para outro lugar"
user = {
    name: 'Rafael'
}

// O mesmo acontece nos arrays que são tipo por referência.
const persons = ['Guilherme', 'Pedro', 'Jennifer'];

// Podemos adicionar novos itens
persons.push('João');

// Podemos remover algum item
persons.shift();

// Podemos alterar diretamente
persons[1] = 'James';
```