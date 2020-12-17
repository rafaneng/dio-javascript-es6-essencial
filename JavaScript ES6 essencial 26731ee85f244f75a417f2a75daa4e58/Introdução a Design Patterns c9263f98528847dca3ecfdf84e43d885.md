# Introdução a Design Patterns

## Definição

Design Patterns ou padrões de projetos são soluções generalistas para problemas recorrentes durante o desenvolvimento de um software. Não se trata de um framework ou um código pronto, mas de uma definição de alto nível de como um problema comum pode ser solucionado.

![Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled.png](Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled.png)

### A Pattern Language (livro)

- 1978
- Christopher Alexander, Sara Ishikawa e Murray Silverstein
- 253 tipos de problemas/desafios de projetos

### Formato de um pattern

- Nome
- Exemplo
- Contexto
- Problema
- Solução

---

![Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%201.png](Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%201.png)

![Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%202.png](Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%202.png)

### Using Pattern Languages for Object-Oriented Programs

- 1987
- Kent Beck (Responsavel pela eXtreme Programming e TDD) e Ward Cunningham
- 5 padrões de projetos

---

![Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%203.png](Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%203.png)

### Design Patterns: Elements of Reusable Object-Oriented
Software

- 1994
- Gang of four (GoF)

![Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%204.png](Introduc%CC%A7a%CC%83o%20a%20Design%20Patterns%20c9263f98528847dca3ecfdf84e43d885/Untitled%204.png)

- Erich Gamma, Richard Helm, Ralph Johnson e John Vlissides
- Tipos de design pattern → Criação, Estruturais e Comportamentais.

## Padrões de criação

Os padrões de criação são aqueles que abstraem e/ou adiam o processo criação dos objetos. Eles ajudam a tornar um sistema independente de como seus objetos são criados, compostos e representados.

- Abstract Factory
- Builder
- Singleton

- Factory Method
- Prototype

## Padrões estruturais

Os padrões estruturais se preocupam com a forma como classes e objetos são compostos para formar estruturas maiores.

- Adapter
- Bridge
- Composite
- Decorator

- Business Delegate
- Flyweight
- Proxy
- Facade

## Padrões comportamentais

Os padrões de comportamento se concentram nos algoritmos e atribuições de responsabilidades entre os objetos. Eles não descrevem apenas padrões de objetos ou de classes, mas também os padrões de comunicação entre os objetos.

- Chain os Responsibility
- Command
- Interpreter
- Iterator
- Mediator

- State
- Strategy
- Template Method
- Visitor
- Observer

## Patterns mais utilizados

### Factory

Todas as funções que retornam um objeto, sem a necessidade de chamá-las com o **new**, são consideradas funções Factory(fábrica).

```jsx
function Pessoa(customProperties){
    return {
        name: 'Rafael',
        lastName: 'Santos',
        ...customProperties
    }
}

const p = Pessoa({name: 'Custom Name', age: 27});
console.log(p);
// { name: 'Custom Name', lastName: 'Santos', age: 27 }
```

### Singleton

O objetivo desse pattern é criar uma única instância de uma função construtora e retorná-la toda vez em que for necessário utilizá-la.

O jQuery é um padrão de Singleton

```jsx
function Pessoa(){
    if(!Pessoa.instance){
        Pessoa.instance = this;
    }
    return Pessoa.instance;
}

const p = Pessoa.call({name: 'Rafael'});
const p2 = Pessoa.call({name: 'Vanessa'});

console.log(p);
console.log(p2);
/*
{ name: 'Rafael' }
{ name: 'Rafael' }
*/
```

### Decorator

Uma função Decorator recebe uma outra função como parâmetro e estende o seu comportamento sem modificá-la explicitamente.

```jsx
let loggedIn = false;

function callIfAuthenticated(fn){
    return !!loggedIn && fn();
}

function sum(a, b){
    return a + b;
}

console.log(callIfAuthenticated(() => sum(2, 3)));
loggedIn = true;
console.log(callIfAuthenticated(() => sum(2, 3)));
loggedIn = false;
console.log(callIfAuthenticated(() => sum(2, 3)));
/*
false
5
false
*/
```

### Observer

É um pattern muito popular em aplicações javascript. A instância (subscriber) mantém uma coleção de objetos (observers) e notifica todos eles quando ocorrem mudanças no estado.

```jsx
class Observable{
    constructor(){
        this.observables = [];
    }

    subscribe(fn){
        this.observables.push(fn);
    }

    notify(data) {
        this.observables.forEach(fn => fn(data));
    }

    unsubscrtbe(fn) {
        this.observables = this.observables.filter(obs => obs !==fn);
    }
}

const o = new Observable();

const logDatal = data => console.log(`Subscribe 1: ${data}`);
const logData2 = data => console.log(`Subscribe 2: ${data}`);
const logData3 = data => console.log(`Subscribe 3: ${data}`);

o.subscribe(logDatal);
o.subscribe(logData2);
o.subscribe(logData3);

o.notify('notifíied 1');

o.unsubscrtbe(logData2);

o.notify('notifíied 2');

/*
Subscribe 1: notifíied 1
Subscribe 2: notifíied 1
Subscribe 3: notifíied 1
Subscribe 1: notifíied 2
Subscribe 3: notifíied 2
*/
```

### Module

É um pattern que possibilita organizarmos melhor o nosso código, sem a necessidade de expor variáveis globais.

```jsx
// Arquivo que vai exportar as informações
let name = 'default';

function getName(){
    return name;
}

function setName(newName){
    name = newName;
}

module.exports = {
    getName,
    setName
};
```

```jsx
// Arquivo que vai importar as informações
const {getName, setName} = require('./javascript');

console.log(getName());
setName('Rafael');
console.log(getName())

/*
default
Rafael
*/
```