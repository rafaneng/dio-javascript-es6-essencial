# Operadores e Estruturas Condicionais

### Operador binário

```jsx
operador1 operador operador2
1 + 2
```

### Operador unário

```jsx
operando1 operador
operador operando1

x++
// Neste caso o x ja receve o valor incrementado
++x
```

### Aritméticos

```jsx
// Módulo (%)
// Operador binário. Retorna o inteiro restante da divisão dos dois operandos.

12 % 5 // retorna 2.

// Incremento (++) e Decremento (--)
++x
x++

const a = ++2; // 3
const b = 2++; // 2 (ele é incrementado depois que recebe o valor)

--x
x--

// Negação (-) e Adição (+)
-3
+"3"     // retorna 3
+true    // retorna 1
+false   // retorna 0
-true    // retorna -1

// Operador de exponenciação (**)
2 ** 3 // retorna 8
10 ** -1 //retorna 0.1

// Operador de agrupamento ( )
2 * (3 + 2)
```

### Atribuição

```jsx
// Atribuição
x = y

// Atribuição de adição
x = x + y // ou
x += y

// Atribuição de subtração
x = x - y // ou
x -= y

// Atribuição de multiplicação
x = x * y // ou
x *= y

// Atribuição de divisão
x = x / y // ou
x /= y

// Atribuição'de resto
x = x % y // ou
x %= y
```

### Comparação

```jsx
// Igual (==)
// Retorna verdadeiro caso os operandos sejam iguais. -3 == var1
"3" == var1
3 == '3'

// Não igual (!=)
// Retorna verdadeiro'caso'os operandos não sejam' iguais.-var1i !=4
var2 != "3"

// Estritamente igual (===)
// Retorna verdadeiro caso'os operandos sejam'iguais e do mesmo tipo. Veja também Object.is e igualdade
3 === var1

// Estritamente não igual (!==)
// Retorna verdadeiro caso os operandos não sejam iguais e/ou não sejam do mesmo tipo.
var1 !== "3"
3 !== '3'

// Maior que (>)
// Retorna verdadeiro caso o operando da esquerda seja maior que o da direita.
var2 > vari
"12" > 2

// Maior que ou igual (>=)
// Retorna verdadeiro caso o operando da esquerda seja maior ou igual ao da direita.
var2 >= var1
var1 >= 3

// Menor que (<)
// Retorna verdadeiro caso o operando da esquerda seja menor que o da direita.
var1 < var2
"12" < "2"

// Menor que ou igual (<=)
// Retorna verdadeiro caso o operando da esquerda seja menor ou igual ao da direita.
var1 <= var2
var2 <= 5
```

### Condicional

```jsx
// Ternário
condicao ? valor1 : valor2

true ? 'foo' :  'bar' // Retorna 'foo'
false ? 'foo' : 'bar' // Retorna 'bar'
```

### Lógico

```jsx
// AND lógico (&&)
exp1 && exp2

var a1 = true && true;      // t && t retorna true
var a2 = true && false;     // t && f retorna false
var a3 = false && true;     // f && t retorna false
var a4 = false && (3 == 4); // f && f retorna false
var a5 = "Gato" && "Cão";   // t && t retorna Cão
var a6 = false && "Gato";   // f && t retorna false
var a7 = "Gato" && false;   // t && f retorna false

// 0U lógico (||)

exp1 || exp2

var o1 = true || true;      // t || t retorna true
var o2 = false || true;     // f || t retorna true
var o3 = true || false;     // t || f retorna true
var o4 = false || (3 ==4);  // f || f retorna false
var o5 = "Gato" || "Cão";   // t || t retorna Gato
var o6 = false || "Gato";   // f || t retorna Gato
var o7 = "Gato" || false;   // t || f retorna Gato

// NOT lógico (!)

!exp1

var n1 = !true;     // !t retorna false
var n2 = !false;    // !f retorna true
var n3 = !"Gato";   // !t retorna false
```

### Spread

```jsx
// Spread ...
var partes = ['ombro', 'joelhos'];
var musica = ['cabeça', ...partes, 'e', 'pés'];

function fn(x, y, z){}
var args = [0, 1, 2];
fn(...args);
```

### Outros unários

```jsx
// Deletar algo
delete something;

// Determinar tipo
typeof something;
```

### Outros binários

```jsx
// in
something in somethingItems

// Arrays
var arvores = new Array("pau-brasil", "loureiro", "cedro", "carvalho", "sicômoro");
0 in arvores;                // retorna true
3 in arvores;                // retorna true
6 in arvores;                // retorna false
"cedro" in arvores;          //  retorna false (você deve especificar o número do índice, não o valor naquele índice)
"length" in arvores;         // retorna true (length' é uma propriedade de Array)

// Objetos predefinidos
"PI" in Math;                // retorna true
var minhaString = new String("coral");
"length" in minhaString;     // retorna true

// Objetos personalizados
var meucarro = {marca: "Honda", modelo: "Accord", ano: 1998};
"marca" in meucarro;         // retorna true
"modelo" in meucarro;        // retorna'true

// instaceof
objeto instanceof tipoobjeto

var dia = new Date(2018, 12, 17);
if (dia instanceof Date) {
// code here
}
```

## Estruturas condicionais

### If, else

```jsx
/*
if (condition){
    // code
}
*/

const array = [0, 1, 2, 3, 4, 5];

array.forEach(item => {
    if(item % 2 === 0){
        console.log(`O número ${item} é par.`);
    }else{
        console.log(`O número ${item} é ímpar.`);
    }
});

/*

-- OUTPUT --

O número 0 é par.
O número 1 é ímpar.
O número 2 é par.
O número 3 é ímpar.
O número 4 é par.
O número 5 é ímpar.

*/
```

### Else if

```jsx
/*
if (condition){
    // code
} else if(condition){
    // code
}
*/

const array = [2, 3, 4, 5, 6, 8, 10, 15];

console.log('\nelse if');
array.forEach(item => {
    if(item % 2 === 0){
        console.log(`O número ${item} é divisível por 2.`);
    }else if(item % 3 === 0){
        console.log(`O número ${item} é divisível por 3.`);
    }else if(item % 5 === 0){
        console.log(`O número ${item} é divisível por 5.`);
    }
});

console.log('\nif');
array.forEach(item => {
    if(item % 2 === 0){
        console.log(`O número ${item} é divisível por 2.`);
    }
    if(item % 3 === 0){
        console.log(`O número ${item} é divisível por 3.`);
    }
    if(item % 5 === 0){
        console.log(`O número ${item} é divisível por 5.`);
    }
});

/*
-- OUTPUT --

else if
O número 2 é divisível por 2.
O número 3 é divisível por 3.
O número 4 é divisível por 2.
O número 5 é divisível por 5.
O número 6 é divisível por 2.
O número 8 é divisível por 2.
O número 10 é divisível por 2.
O número 15 é divisível por 3.

if
O número 2 é divisível por 2.
O número 3 é divisível por 3.
O número 4 é divisível por 2.
O número 5 é divisível por 5.
O número 6 é divisível por 2.
O número 6 é divisível por 3.
O número 8 é divisível por 2.
O número 10 é divisível por 2.
O número 10 é divisível por 5.
O número 15 é divisível por 3.
O número 15 é divisível por 5.

*/
```

### Switch

```jsx
/*
switch (expressao){
    case valor1:
        [break;]
    case valor2:
        [break;]
    default:
        [break;]
}
*/

const fruit = 'banana';

switch(fruit){
    case 'banana':
        console.log('R$3,00 / kg');
        break;
    case 'mamão':
    case 'pera':
        console.log('R$2,00 / kg');
        break;  
    default:
        console.log('Produto não existe no estoque');
        break;     
}

/*
-- OUTPUT --

R$3,00 / kg

*/
```

## Estruturas de repetição

### For

```jsx
/*
for ([expressaoInicial]; [condicao]; [incremento]){
    declaracao
}
*/

const array = ['one', 'two', 'three'];

for(let index = 0; index < array.length; index++){
    const element = array[index];
    console.log(`Element #${index}: ${element}.`);
}

/*
-- OUTPUT --

Element #0: one.
Element #1: two.
Element #2: three.

*/
```

### While

```jsx
/*
while(condicao){
    declaracao
}
*/

var n = 0;
var x = 0;

while(n < 3){
    n++
    x += n;
    console.log(x);
}

/*
-- OUTPUT --

1
3
6

*/
```

### Do While

```jsx
/*
do{
    declaracao
}while(condicao)
*/

let i = 0;

do{
    i += 1;
    console.log(i);
} while(i < 5);

/*
-- OUTPUT --

1
2
3
4
5

*/
```

### For in e For of

```jsx
let arr = [3, 5, 7];
arr.foo = "hello";

for(let i in arr){
    console.log(i) // logs "0", "1", "2", "foo"
}

for(let i of arr){
    console.log(i) // logs "3", "5", "7"
}
```

## Controle de repetição

### Break

```jsx
// break
console.log('Exemplo de utilização de break');

var index = 0;

while(true){
    index++;

    if(index > 2){
        break;
    }

    console.log(index);
}

/*
-- OUTPUT --

Exemplo de utilização de break
1
2

*/
```

### Continue

```jsx
// continue
console.log('Exemplo de utilização de continue');

const array = [1, 2, 3, 4, 5, 6]

for(let index = 0; index < array.length; index++){
    const element = array[index];
    
    if(element % 2 === 0){
        continue;
    }
    console.log(element);
}

/*
-- OUTPUT --

Exemplo de utilização de continue
1
3
5

*/
```