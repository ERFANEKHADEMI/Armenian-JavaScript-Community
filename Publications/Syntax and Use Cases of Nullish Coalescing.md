# ?? (nullish coalescing) օպերատորը JavaScript-ում: Ինչո՞վ է այն տարբերվում տրամաբանական || (OR)-ից:

**??** (_nullish coalescing_) օպերատորը **ECMAScript** ստանդարտի մեջ ավելացրել են վերջին տարիներին (_Edition 11, 2020 թվականի Հունիս ամիս_): Այդ իսկ պատճառով այն սպասարկվում է ոչ բոլոր բրաուզերների կողմից։ [Այս հղումով](https://caniuse.com/?search=nullish%20coalescing) կարող եք ծանոթանալ դրանց ցանկին։

**??** (_nullish coalescing_)-ը տրամաբանական օպերատոր է, որը վերադարձնում է աջ օպերանդի արժեքը, եթե ձախ օպերանդի արժեքը _null_ կամ _undefined_ է, հակառակ դեպքում այն վերադարձնում է ձախ օպերանդի արժեքը։ Օրինակ՝

```
const text = null ?? "default string"
console.log(text) // "default string"

const number = 0 ?? 42
console.log( number ) // 0
```

Ինչպես տեսնում ենք վերևում բերված օրինակների մեջ՝ ձախ կողմի օպերանդի արժեքը հաշվարկվում և վերադարձվում է անգամ այն դեպքում, երբ վերափոխվելով Բուլյան տիպի, ընդունում է _falsy_ արժեք՝ բացառությամբ _null_-ի և _undefined_-ի։ Հենց դրանով էլ ?? (_nullish coalescing_) տրամաբանական օպերատորը տարբերվում է || (_OR_) տրամաբանական օպերատորից։ Փորձենք վերևում բերված օրինակը կատարել OR (_||_) օպերատորի օգնությամբ՝

```
const text = null || "default string";
console.log(text) // "default string"
const number = 0 || 42;
console.log(number) // 42
```

Եվ այսպես առաջին օրինակում երկու տրամաբանական օպերատորներն էլ նույն կերպ են աշխատում, սակայն երկրորդ օրինակի մեջ նրանց վերադարձրած արժեքները տարբերվում են։ || օպերատորը վերադարձնում է առաջին _truthy_ արժեքը՝ _42_-ը, այն դեպքում երբ **??**-ը վերադարձնում է առաջին արժեքը, որը չի հանդիսանում _null_ կամ _undefined_, թեև այն կարող է նաև _falsy_ արժեք լինել, մեր օրինակում՝ _0_։

_falsy_ արժեքների (_0, -0, 0n, NaN, "", null, undefined, false_) և տիպերի վերափոխման մասին առավել մանրամասն կարող եք կարդալ [այս հղումով](https://github.com/h0vhann1syan/Armenian-JavaScript-Community/blob/master/Publications/Understanding%20JavaScript's%20Loose%20Typing.md)։

Ինչպես և && (AND) և || (OR) տրամաբանական օպերատորների դեպքում էր՝ **??** (nullish coalescing) օպերատորը նույնպես կարող է օգտագործվել շղթայի մեջ, օրինակ՝

```
let someValue; // ստեղծում ենք someValue փոփոխականը, սակայն նրան արժեք չենք վերագրում, ինչի արդյունքում այն հավասար է լինում undefined-ի:
const value = null ?? someValue ?? 42 ?? "default string";
console.log(value) // 42
```

**??** օպերատորն ունի ցածր առաջնահերթություն, առաջնահերթությունների աղյուսակի մեջ նրա ինդեքսը _5_ է, ինչը բարձր է = (_վերագրման օպերատոր_), ? (_պայմանական կամ թերնարի օպերատոր_)-ներից, սակայն ցածր է հաճախ օգտագործվող հիմնական օպերատորներից՝ +, \*, ++, \*\* և այլն։

Ի դեպ համանման օպերատոր կա ոչ միայն **JavaScript**-ի, այլ նաև մի շարք այլ ծրագրավորման լեզուների մեջ, օրինակ՝ C#-ի, Perl-ի (սկսած 5․10 տարբերակից), Swift-ի, PHP-ի (սկսած 7․0․0 տարբերակից ) և այլն։

_2019_ թվականի Նոյեմբերին թողարկված _TypeScript_ 3.7 տարբերակի մեջ այն արդեն առկա էր, և բազմաթիվ դրական արձագանքներից հետո երկար ժամանակ մշակման փուլում գտնվող այս նորույթը վերջնականապես որոշվեց ավելացնել **ECMAScript**-ի 2020 թվականին թողարկված ստանդարտի մեջ։

Ներքևում տեղադրված հղումներով կարող եք առավել մանրամասն ծանոթանալ այս նոր տրամաբանական օպերատորի նկարագրությանը, ինչպես նաև տեսնել կիրառության շատ այլ տարբեր մոդելներ։

[TC39 Proposal for Nullish Coalescing](https://tc39.es/proposal-nullish-coalescing/?fbclid=IwAR13_D_5cPGzLuy0IeYgO3C1DfsWxVqEpN1ug7V2Now3EWqKOnbdjnpeRV8)  
[Stack Overflow: Null Coalescing Operator in JavaScript](https://stackoverflow.com/questions/476436/is-there-a-null-coalescing-operator-in-javascript?fbclid=IwAR1naEao8jGVxlCLej_CYvHgxh2TRyQZLT93g8csVJxfIMfPHSg_eKHvqDY)  
[ES Discuss: Proposal for a Null Coalescing Operator](https://esdiscuss.org/topic/proposal-for-a-null-coalescing-operator?fbclid=IwAR2jDhzFE2pSL4N1Uwz0yCSSBr0AUKSDNAlMbynRh8rZLk4J7MFDqJ-k-t8)
