---
created: 20220915-1346
tags:
  - Archive/course
---

# Intro to web dev notes

It seems to be structured in Html, CSS and JS as it should.
I'm interested in the js part because it's the most difficult, the one I'm revisiting and the one I hope to explain to Lau later.

---
## Javascript
#### Intro
- Things are harder here compared to HTML and CSS
- Code is written for us humans first and computers second
- Clear code > Clever code
#### Variables
Example
```javascript
const monthlyRent = 21000;
const yearlyRent = monthlyRent * 12;
console.log(yearlyRent);
```
Ways of describing one
```javascript
const monthlyRent = 21000; //Constant, immutable
let monthlyRent = 21000;   //variable, changeable
var monthlyRent = 21000;   //Old way of writing variables
```

#### Numbers, Strings & Booleans
Strings
```javascript
const aString = "this is a string of text and nothing more";
const anotherString = 'single quotes are valid';
const thirdString = 'using one type of "quotes" inside the other is valid';
const lastString = `backticks are for strings too

they let you write multiline and have some other tricks ;)

`;
```

```javascript
const firstName = 'Guillermo';
const lastName = 'del Toro';
const phrase = `My name is ${firstName} ${lastName} and you
killed my father.
Prepare to die!!`;
```

Booleans
```javascript
const franIsAwesome = true;
const catsAreMerciful = false;
```

Numbers
```javascript
const myAge = 29;
const myAgeAgain = 29.0000000000000; 
const pi = 3.141592;
```


#### Control Flow
```javascript
const rosesAreRed = true;

if (rosesAreRed) {
	console.log('Yes they are');
} else {
	console.log('You sir, you are wrong');
}

if (2 + 2 === 4) {
	console.log('Math rules!');
} else {
	console.log('You sir, you are wrong');
}
```

#### Loops
This is the ugly way of doing something repetitive
``` JavaScript
let friendsAtYourParty = 0;
friendsAtYourParty = friendsAtYourParty + 1; //Cada uno suma sobre
friendsAtYourParty = friendsAtYourParty + 1; //el anterior
friendsAtYourParty = friendsAtYourParty + 1;
friendsAtYourParty = friendsAtYourParty + 1;
```

Now this is proper looping
``` JavaScript
let friendsAtYourParty = 0;
while(friendsAtYourParty <= 10) {
	friendsAtYourParty = friendsAtYourParty + 1;
} //this will be done until friendsAtYourParty is 10 or more
```



##### About equals
`=` is Assignment
`==` is simple equality, it checks the compared values
`===` is strict equality, it checks compared values AND types
``` JavaScript
2 + 2 //The result is a number
2 + 2 === 4; //True
2 + 2 == 4;  //Also true
2 + 2 == '4'; //True becuase both values are 4
2 + 2 === '4'; //False because one is number the other string
```

---
# References
[Frontend Master's Intro to web dev, v3](https://frontendmasters.com/courses/web-development-v3/javascript-intro/)
