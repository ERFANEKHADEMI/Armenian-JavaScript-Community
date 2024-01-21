2022 թվականի հունիսին հաստատվեց **ECMAScript 2022**-ի նոր ստանդարտը, որում կան մի քանի հետաքրքիր նորամուծություններ։ Դիտարկենք մի փոքրիկ նորամուծություն, որը թույլ է տալիս օգտագործել բացասական ինդեքս և ստանալ զանգվածի վերջին էլեմենտը ավելի կարճ ու հեշտ կարդացվող սինթաքսով։

```
const fruits = ['banana', 'apple', 'orange', 'kiwi'];
```

Նախկինում վերջին էլեմենտը կստանայինք հետևյալ տարբերակով՝

```
console.log(fruits[fruits.length -1])
```

Այժմ նույն գործողությունը կարող ենք անել այսպես՝

```
console.log(fruits.at(-1))
```

**_at_** մեթոդը կարող ենք օգտագործել նաև _String_-ների և _TypedArray_-ների հետ աշխատելու համար։ Օրինակ փորձենք ստանալ _fruit_ սթրինգի նախավերջին տառը՝

```
const fruit = 'orange';
console.log(fruit.at(-2)); // 'g'
```

**ECMAScript**-ի նոր, թարմացված ստանդարտը _PDF_ ֆորմատով կարելի է ներբեռնել [այստեղից:](https://www.ecma-international.org/wp-content/uploads/ECMA-262_13th_edition_june_2022.pdf?fbclid=IwAR2XnfqSoa5llW9bxc5jhJ0ChVhtbnR0h8IsP_mEzIsyJQh1VmuiRPDj060)
