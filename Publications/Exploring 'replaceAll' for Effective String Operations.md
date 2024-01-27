# Ինպե՞ս տեքստի մեջ որոնել և փոխել բոլոր միանման բառերը՝ օգտվելով String.prototype-ի replaceAll մեթոդից:

Օգտագործելով **String.prototype**-ի **replace** մեթոդը, մենք կարող ենք տրված տեքստի մեջ որոնել և փոխել անհրաժեշտ բառը, սակայն այդ մեթոդը գտնում և փոխում է միայն առաջին համընկնումը։ Օրինակ՝

```
const text = "Java is awesome. Java is fun.";
const newText = text.replace("Java", "JavaScript");
console.log(newText); // "JavaScript is awesome. Java is fun."
```

Որպեսզի **replace** մեթոդով հնարավոր լինի փոխել ոչ միայն առաջին, այլ նաև հաջորդ համընկնումները՝ մենք պետք է օգտագործենք **_RegExp_**։ Վերևում բերված օրինակում դա կունենա հետևյալ տեսքը՝

```
const text = "Java is awesome. Java is fun.";
const newText = text.replace(/Java/gi, "JavaScript");
console.log(newText); // "JavaScript is awesome. JavaScript is fun."
```

**_JavaScript_** ծրագրավորման լեզվում համեմատաբար վերջերս ավելացված **replaceAll** մեթոդը թույլ է տալիս այդ աշխատանքը կատարել առանց _RegExp_֊ի օգտագործման։ Օրինակ՝

```
const text = "Java is awesome. Java is fun.";
const newText = text.replaceAll("Java", "JavaScript");
console.log(newText); // "JavaScript is awesome. JavaScript is fun"
```

Մեթոդն աջակցվում է ժամանակակից հանրաճանաչ վեբ դիտարկիչների կողմից (_Chrome, Firefox, Opera, Safari, Edge_), ինչպես նաև _node.js_-ի 15.0.0֊ից բարձր տարբերակներում։ Ի դեպ մեթոդը շատ ավելի ճկուն է, այն որպես առաջին արգումենտ կարող է ստանալ ոչ միայն String տիպի արժեք, այլ նաև RegExp, իսկ որպես երկրորդ արգումենտ՝ ֆունկցիա։ Մեթոդի նկարագրությանն ու հնարավորություններին ավելի մանրամասն կարելի է ծանոթանալ սկզբնաղբյուրում՝ [TC39 Proposal for String `replaceAll`](https://github.com/tc39/proposal-string-replaceall), [ECMAScript Specification for `String.prototype.replaceAll`](https://tc39.es/ecma262/multipage/text-processing.html#sec-string.prototype.replaceall)
