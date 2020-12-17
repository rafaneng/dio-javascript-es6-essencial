# Iterar, buscar e transformar elementos

## Iterar elementos

### forEach

Iteração de cada item dentro de um array

```jsx
const arr = [1, 2, 3, 4, 5];

arr.forEach((value, index) => {
	console.log(`${index}: ${value}`);
});
/*
0: 1
1: 2
2: 3
3: 4
4: 5
*/
```

### map

Retorna um novo array, de mesmo tamanho, iterando cada item de um array

```jsx
const arr = [1, 2, 3, 4, 5];

arr.map(value => value * 2);
// [ 2, 4, 6, 8, 10 ]
```

### flat

Retorna um novo array com todos os elementos de um sub-array concatenados de forma recursiva de acordo com a profundidade especificada (depth)

```jsx
const arr = [1, 2, [3, 4]];
arr.flat();
// [1, 2, 3, 4]

const idades= [20, 34, [35, 60 [70, 40]]];
arr.flat(2);
// [20, 34, 35, 60 70, 40]
```

### flatMap

Retorna um novo array assim como a função map e executa um flat de profundidade 1

```jsx
const arr = [1, 2, 3, 4];

arr.flatMap(value => [value * 2]);
// [2, 3, 6, 8]

arr.flatMap(value => [[value * 2]]);
// [[2], [3], [6], [8]]

```

### keys

Retorna um **Array Iterator** que contém as chaves para cada elemento do array

```jsx
const arr = [1, 2, 3, 4];

const arrIterator = arr.keys();

arrIterator.next( );
// {value: O, done: false}

arrIterator.next();
// {value: 1, done: false}

arrIterator.next( );
// {value: 2, done: false}

arrIterator .next();
// {value: 3, done: true}
```

### values

Retorna um Array Iterator que contém os valores para cada elemento do array

```jsx
const arr = [1, 2, 3, 4];

const arrIterator = arr.values();

arrIterator.next( );
// {value: 1, done: false}

arrIterator.next();
// {value: 2, done: false}

arrIterator.next( );
// {value: 3, done: false}

arrIterator .next();
// {value: 4, done: true}
```

### entries

Retorna um Array Iterator que contém os pares chave/valor para cada elemento do array.

```jsx
const arr = [1, 2, 3, 4];

const arrIterator = arr.entries();

arrIterator.next( );
// {value: [0, 1], done: false}

arrIterator.next();
// {value: [1, 2], done: false}

arrIterator.next( );
// {value: [2, 3], done: false}

arrIterator .next();
// {value: [3, 4], done: true}
```

## Buscar elementos

### find

Retorna o primeiro item de um array que satisfaz a condição

```jsx
const arr = [1, 2, 3, 4];

const firstGreaterThanTwo = arr.find(value => value > 2);
console.log(firstGreaterThanTwo);
// 3
```

### findIndex

Retorna o índice do primeiro item de um array que satisfaz a condição

```jsx
const arr = [1, 2, 3, 4];

const firstIndexGreaterThanTwo = arr.findIndex(value => value > 2);
console.log(firstIndexGreaterThanTwo );
// 2
```

### filter

Retorna um novo array com todos os elementos que satisfazem a condição

```jsx
const arr = [1, 2, 3, 4];

const allValuesGreaterThanTwo = arr.filter(value => value > 2);
console.log(allValuesGreaterThanTwo );
// [3, 4]
```

### indexOf

Retorna o primeiro índice em que um elemento pode ser encontrado no array

```jsx
const arr = [1, 3, 3, 4, 3];

const firstIndexOfItem = arr.indexOf(3);
console.log(firstIndexOfItem );
// 1
```

### lastIndexOf

Retorna o último índice em que um elemento pode ser encontrado no array

```jsx
const arr = [1, 3, 3, 4, 3];

const lastIndexOfItem = arr.lastIndexOf(3);
console.log(lastIndexOfItem );
// 4
```

### includes

Retorna um booleano verificando se determinado elemento existe no array

```jsx
const arr = [1, 3, 3, 4, 3];

const hasItemOne = arr.includes(1);
// true

const hasItemTwo = arr.includes(2);
// false
```

### some

Retorna um booleano verificando se pelo menos um item de um array satisfaz a condição

```jsx
const arr = [1, 3, 3, 4, 3];

const hasSomeEvenNumber = arr.some(value => value % 2 === 0);
// true

// ----------------------------------------------------------------------

const students = [
	{name: 'John', grade: 7},
	{name: 'Jenny', grade: 5},
	{name: 'Peter', grade: 4}
]

students.some(student => student.grade >= 7);
// true

students.find(student => student.grade >= 7);
// {name: "John", grade: 7}

```

### every

Retorna um booleano verificando se todos os itens de um array satisfazem a condição

```jsx
const arr = [1, 3, 3, 4, 3]

const allEvenNumbers = arr.every(value => value % 2 === 0);
// false
```

## Ordenar elementos

### sort

Ordena os elementos de um array de acordo com a condição

```jsx
const arr = [1, 3, 2, 5, 4];

arr.sort();
// [1, 2, 3, 4, 5]

// ----------------------------------------------------------------------

const students = [
	{name: 'John', grade: 7},
	{name: 'Jenny', grade: 5},
	{name: 'Peter', grade: 4}
]

students.sort((current, next) => current.grade - next.grade);
/*
{name: "Peter", grade: 4}
{name: "Jenny", grade: 5}
{name: "John", grade: 7}
*/

students.sort((current, next) => next.grade - current.grade);
/*
{name: "John", grade: 7}
{name: "Jenny", grade: 5}
{name: "Peter", grade: 4}
*/
```

### reverse

Inverte os elementos de um array

```jsx
const arr = [1, 2, 3, 4, 5];

arr.reverse();
// [5, 4, 3, 2, 1]
```

## Transformar em outro tipo de dados

### join

Junta todos os elementos de um array, separados por um delimitador e retorna uma string

```jsx
const arr = [1, 2, 3, 4, 5];

arr.join('-');
// "1-2-3-4-5"
```

### reduce

Retorna um novo tipo de dado iterando cada posição de um array

```jsx
const arr = [1, 2, 3, 4, 5];

arr.reduce((total, value) => total += value, 0);
// 15

// ----------------------------------------------------------------------

const students = [
	{name: 'John', grade: 7},
	{name: 'Jenny', grade: 5},
	{name: 'Peter', grade: 4}
]

students.reduce((totalGrades, student) => totalGrades += student.grade, 0)
// 16

students.reduce((totalGrades, student) => totalGrades += student.grade, 0) / student.lenght
// 5.333333333333333
```