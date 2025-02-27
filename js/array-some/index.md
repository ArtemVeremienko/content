---
title: "`[].some`"
authors:
  - windrushfarer
contributors:
  - skorobaeus
tags:
  - doka
---

## Кратко

Метод массива `Array.some` позволяет узнать, есть ли в массиве хотя бы один элемент, удовлетворяющий условию в функции-колбэке. Колбэк-функция будет вызвана для каждого элемента массива до тех пор пока не вернётся `true`, либо пока не закончатся элементы массива.

Результатом вызова метода `Array.some` будет boolean-значение `true` или `false`. Если ни один элемент в массиве не удовлетворит условию, то результат будет `false`.

## Пример

```js
const nums = [3, 5, 7, 8, 9, 11]

// Проверим, что в массиве есть хотя бы одно четное число
const hasEvenNumber = nums.some(num => {
  return num % 2 === 0
})
console.log(hasEvenNumber)
// true

const oddNums = [3, 5, 7, 9, 11]

// Здесь четного нет
const noEvenNumber = oddNums.some(num => {
  return num % 2 === 0
})
console.log(noEvenNumber)
// false
```

Интерактивный пример

<iframe title="Используем some для проверки массива — Array.some — Дока" src="demos/index/" height="930"></iframe>

## Как пишется

Чтобы использовать метод `Array.some` ему необходимо передать колбэк-функцию, которая должна возвращать boolean-значение, аналогично методам [Array.filter](/js/array-filter) и [Array.every](/js/array-every). Возвращать можно и другие truthy и falsy значения, они [преобразуются согласно типу](/js/typecasting/).

Функция, которую мы передаём в метод `Array.some`, может принимать три параметра:

- `item` — элемент массива в текущей итерации
- `index` — индекс текущего элемента
- `arr` — сам массив, который мы перебираем

```js
const balls = ['🎾', '🏈', '🎾', '🎾']

const areAllBallsGreen = balls.some((ball, index, arr) => ball === '🏈')
console.log(areAllBallsGreen)
// true
```

## Как это понять

Метод `Array.some` позволяет упростить написание кода в случае, когда мы хотим проверить наличие определённого элемента в массиве. В отличие от [Array.every](/js/array-every), чтобы результат выражения стал `true` достаточно, чтобы хотя бы один элемент удовлетворил условию функции-предиката.

Для сравнения напишем пример через `for` или `while`.

```js
const food = ['🍗', '🍖', '🥓', '🥬', '🥩', '🍔']

let hasAnySalad = false

for (let i = 0; i < food.length; i++) {
  if (food[i] === '🥬') {
    hasAnySalad = true
    break
  }
}
```

Метод `Array.some` позволит написать меньше кода и сделать его понятнее.

```js
const food = ['🍗', '🍖', '🥓', '🥬', '🥩', '🍔']

const hasAnySalad = food.some(item => item === '🥬')
console.log(hasAnySalad)
// true
```

<aside>

💡 В примерах код был написан с помощью [двух разных подходов](/js/programming-paradigms): императивный и декларативный. Использование метода `Array.some` делает код декларативнее.

</aside>
