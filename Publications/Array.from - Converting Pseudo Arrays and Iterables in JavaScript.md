# Ինչպե՞ս փսևդոզանգվածներից և իտերացվող օբյեկտներից ստանալ զանգված՝ օգտվելով ES6 ստանդարտում ներդրված Array.from մեթոդից:

**_Array.from_** մեթոդը փսևդոզանգվածներից (_երբեմն անվանում են նաև զանգվածանման օբյեկտներ_) և իտերացվող օբյեկտներից ստեղծում և վերադարձնում է զանգված։ Նախ հասկանանք թե ինչ են իրենցից ներկայացնում փսևդոզանգվածները և իտերացվող օբյեկտները։

Փսևդոզանգվածները կամ ինչպես երբեմն ընդունված է անվանել զանգվածանման օբյեկտները դրանք սովորական օբյեկտներ են, որոնց հատկությունների անունները (_բանալիները_) իրենցից ներկայացնում են _String_ տիպի արժեքներ, որոնք սակայն հեշտությամբ կարող են վերափոխվել ամբողջ թվերի՝ այսպիսով հիշեցնելով զանգվածների ինդեքսները։ Նրանք նաև ունեն _length_ հատկություն, որը ցույց է տալիս օբյեկտում առկա հատկությունների քանակը։

Փսևդոզանգվածի դասական օրինակ է ֆունկցիաների ներսում հասանելի, և իր մեջ ֆունկցիային հաղորդված բոլոր արգումենտները կրող _arguments_-ը։ Այդ փսևդոզանգվածի մասին առավել մանրամասն [կարող եք ծանոթանալ այստեղ։](https://github.com/h0vhann1syan/Armenian-JavaScript-Community/blob/master/Publications/Unlocking%20the%20Power%20of%20Pseudo-Array%20Arguments%20in%20Functions.md)

Իտերացվող օբյեկտները պետք է պարտադիր ունենան **[Symbol.iterator]** հատկությունը, որը սահմանում և ապահովում է օբյեկտի իտերացիայի ճշգրիտ հերթականությունն ու անխափան աշխատանքը։ Եթե ավելի պարզ՝ բոլոր այն օբյեկտները, որոնց վրա հնարավոր է կանչել _for of_ ցիկլը, հանդիսանում են իտերացվող օբյեկտներ։ Օրինակ _Map-ն ու Set_-ն իտերացվող օբյեկտներ են։

Փսևդոզանգվածներից կամ իտերացվող օբյեկտներից զանգված ստանալու համար մենք նրանց որպես արգումենտ տալիս ենք **Array** կոնստրուկտորի **from** ստատիկ մեթոդին։ Օրինակ փորձենք **Array.from** մեթոդին որպես արգումենտ տալ _Map_ օբյեկտ.

```
const person = new Map();
person.set("name", "John");
person.set("age", 25);

console.log(person); // {"name" => "John", "age" => 25}

const arrFromMap = Array.from(person);
console.log(arrFromMap); // [["name", "John"], ["age", 25]]
```

_Set_-ը նույնպես կարող է օգտագործվել.

```
const fruits = new Set();
fruits.add("apple");
fruits.add("oranges");

console.log(fruits); // {"apple", "oranges"}

const arrFromSet = Array.from(fruits);
console.log(arrFromSet); // ["apple", "oranges"]
```

Մենք կարող ենք այս մեթոդի օգնությամբ զանգված ստանալ նաև _arguments_ փսևդոզանգվածից.

```
function foo() {
  return Array.from(arguments);
}

console.log(foo(1, 2, 3)); // [1, 2, 3]
console.log(foo("a", "b")); // ["a", "b"]
```

Այս մեթոդով կարելի է զանգված ստանալ անգամ _String_ տիպին պատկանող արժեքներից՝

```
const arrFromString = Array.from("hello");
console.log(arrFromString); // ["h", "e", "l", "l", "o"]
```

Հետաքրքիր է, որ _Array.from_ մեթոդն ունի նաև երկու ոչ պարտադիր պարամետրներ, մեթոդի լիարժեք սինթաքսն ունի հետևյալ տեսքը՝

```
Array.from(object, mapFunction, thisValue)
```

- object պարամետրին արդեն ծանոթ ենք, այն պարտադիր է և պետք է լինի փսևդոզանգված կամ իտերացվող օբյեկտ։
- mapFunction-ը հետադարձ կանչի (callback) ֆունկցիա է, որը կանչվում է զանգվածի յուրաքանչյուր էլեմենտի համար (_ինչպես արդեն ասվեց, այս պարամետրը պարտադիր չէ_): Այն իր գործառույթով նման է զանգվածների _map_ մեթոդին, և _Array.from(obj, mapFn, thisArg)_ կանչը համարժեք է _Array.from(obj).map(mapFn, thisArg)_ կանչին, միայն այն տարբերությամբ, որ միջանկյալ զանգված այլևս չի ստեղծվում։
- thisValue-ն սահմանում է _this_-ի արժեքը՝ _mapFunction_-ի կանչի համար (_նույնպես հանդիսանում է ոչ պարտադիր պարամետր_):

Մեթոդը **ECMAScript** ստանդարտում ներդրվել է _2015_ թվականին (_ES6_) և գործնականում աջակցվում է բոլոր ժամանակակից ցանցային դիտարկիչների կողմից: Խնդիրներ կարող են առաջանալ համեմատաբար հին _Internet Explorer_ դիտարկիչի վրա (_IE վերջին 11-րդ տարբերակը նույնպես այս մեթոդը չի ճանաչում և ապահովության համար կարելի է սքրիփթի մեջ ավելացնել մեթոդի պոլիֆիլը_): Պոլիֆիլի օրինակ՝

```
if (!Array.from) {
  Array.from = (function () {
    var toStr = Object.prototype.toString;
    var isCallable = function (fn) {
      return typeof fn === 'function' || toStr.call(fn) === '[object Function]';
    };
    var toInteger = function (value) {
      var number = Number(value);
      if (isNaN(number)) { return 0; }
      if (number === 0 || !isFinite(number)) { return number; }
      return (number > 0 ? 1 : -1) * Math.floor(Math.abs(number));
    };
    var maxSafeInteger = Math.pow(2, 53) - 1;
    var toLength = function (value) {
      var len = toInteger(value);
      return Math.min(Math.max(len, 0), maxSafeInteger);
    };
    return function from(arrayLike /*, mapFn, thisArg */) {
      var C = this;
      var items = Object(arrayLike);
      if (arrayLike == null) {
        throw new TypeError('Array.from requires an array-like object - not null or undefined');
      }
      var mapFn = arguments.length > 1 ? arguments[1] : void undefined;
      var T;
      if (typeof mapFn !== 'undefined') {
        if (!isCallable(mapFn)) {
          throw new TypeError('Array.from: when provided, the second argument must be a function');
        }
        if (arguments.length > 2) {
          T = arguments[2];
        }
      }
      var len = toLength(items.length);
      var A = isCallable(C) ? Object(new C(len)) : new Array(len);
      var k = 0;
      var kValue;
      while (k < len) {
        kValue = items[k];
        if (mapFn) {
          A[k] = typeof T === 'undefined' ? mapFn(kValue, k) : mapFn.call(T, kValue, k);
        } else {
          A[k] = kValue;
        }
        k += 1;
      }
      A.length = len;
      return A;
    };
  }());
}
```
