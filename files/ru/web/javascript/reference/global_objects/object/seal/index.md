---
title: Object.seal()
slug: Web/JavaScript/Reference/Global_Objects/Object/seal
tags:
  - ECMAScript5
  - JavaScript
  - JavaScript 1.8.5
  - Method
  - Object
  - Reference
translation_of: Web/JavaScript/Reference/Global_Objects/Object/seal
---
{{JSRef("Global_Objects", "Object")}}

Метод **`Object.seal()`** запечатывает объект, предотвращая добавление новых свойств к объекту и делая все существующие свойства не настраиваемыми. Значения представленных свойств всё ещё могут изменяться, поскольку они остаются записываемыми.

## Синтаксис

```
Object.seal(obj)
```

### Параметры

- `obj`
  - : Запечатываемый объект.

## Описание

По умолчанию, объекты являются {{jsxref("Object.isExtensible()", "расширяемыми", "", 1)}} (к ним могут добавляться новые свойства). Запечатывание объекта предотвращает добавление к нему новых свойств и делает все существующие свойства не настраиваемыми. Оно делает все свойства объекта фиксированными и неизменными. Пометка всех свойств объекта как не настраиваемых также предотвращает их преобразование из свойств данных в свойства доступа и наоборот, но не предотвращает изменение значения свойств данных. Попытки удаления или добавления свойств к запечатанному объекту, либо преобразования свойств данных в свойства доступа и наоборот, будут терпеть неудачу, либо молча, либо с выбрасыванием исключения {{jsxref("Global_Objects/TypeError", "TypeError")}} (как правило, но не обязательно, это происходит в {{jsxref("Strict_mode", "строгом режиме", "", 1)}}).

Цепочка прототипов не затрагивается. Однако, свойство {{jsxref("Object.proto", "__proto__")}} {{deprecated_inline}} также запечатываться.

## Примеры

```js
var obj = {
  prop: function() {},
  foo: 'bar'
};

// Новые свойства могу быть добавлены, существующие свойства могут быть изменены или удалены.
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

var o = Object.seal(obj);

assert(o === obj);
assert(Object.isSealed(obj) === true);

// Изменение значений свойств на запечатанном объекте всё ещё работает.
obj.foo = 'quux';

// Но вы не можете преобразовать свойства данных в свойства доступа и наоборот.
Object.defineProperty(obj, 'foo', { get: function() { return 'g'; } }); // выбросит TypeError

// Теперь любые изменения, кроме изменения значений свойств, не будут работать.
obj.quaxxor = 'дружелюбная утка'; // молча не добавит свойство
delete obj.foo; // молча не удалит свойство

// ...а в строгом режиме такие попытки будут выбрасывать исключения TypeError.
function fail() {
  'use strict';
  delete obj.foo; // выбросит TypeError
  obj.sparky = 'arf'; // выбросит TypeError
}
fail();

// Попытка добавить что-то через Object.defineProperty также выбросит исключение.
Object.defineProperty(obj, 'ohai', { value: 17 }); // выбросит TypeError
Object.defineProperty(obj, 'foo', { value: 'eit' }); // изменяем значение существующего свойства
```

## Примечания

В ES5, если аргумент метода не является объектом (является примитивным значением), будет выброшено исключение {{jsxref("Global_Objects/TypeError", "TypeError")}}. В ES6 такой аргумент будет рассматриваться, как простой запечатанный объект и метод его просто вернёт.

```js
> Object.seal(1)
TypeError: 1 is not an object // код ES5

> Object.seal(1)
1                             // код ES6
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{jsxref("Object.isSealed()")}}
- {{jsxref("Object.preventExtensions()")}}
- {{jsxref("Object.isExtensible()")}}
- {{jsxref("Object.freeze()")}}
- {{jsxref("Object.isFrozen()")}}
