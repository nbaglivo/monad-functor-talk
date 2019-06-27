@title[topic]

### The Maybe Monad Functor

---

@title[what]

What's a Monad again?

@css[fragment](Monad is just a Monoid in the category of Endofunctors.)
---
---

@title[what]
Known fact about Monads:

@css[fragment](When you finally understand it, you’ll lose the ability to explain it to others)
---

@title[spec]

### Fantasy Land Specification

(aka "Algebraic JavaScript Specification")

---?image=assets/fantasyland_1.png&size=contain

---?image=assets/fantasyland_2.png&size=contain
---
@title[the-what]

### The Maybe Monad

@css[fragment](Maybe is... Maybe means...)
@css[fragment](Basically, it means that a value can be there, or not.)

---

@title[get-name-again]

```
function getAge(person) {
    return person.age;
}
```

@css[text-blue fragment](We figured out that person can be `null`...)

---

@title[explotion]

![boom](https://images2.minutemediacdn.com/image/upload/c_fill,g_auto,h_1248,w_2220/f_auto,q_auto,w_1100/v1554933379/shape/mentalfloss/nuclear-bomb-dirty-470309868.jpg)

---

@title[get-name-again]

```
type Person = { age: number };
function getAge(person: Null | Person) {
    return person.age;
}
```

@css[text-blue fragment](So... maybe we have a person, maybe we don't. Now it is clear.)
---

@title[get-name-again]

Maybe we can...

```
type Person = { age: number };
type Maybe<T> = Null | T;
function getAge(person: Maybe<Person>) {
    return person.age;
}
```
---
@title[get-name-again]

Maybe we can...

```
type Person = { age: number };
type Maybe<T> = Null | T;
function getAge(person: Maybe<Person>) {
    if (person) {
        return person.age;
    } else {
        return null; // well, we don't have an age dude.
    }
}
```

@css[text-blue fragment](Not so bad, does not explode. Easy to understand, I think I can go back to my planet now)
---
@title[get-name-again]

@css[fragment](But wait a minute, new wild requirement appeared...)
@css[fragment](Need also to know if the guy is legally able to drink)

---
@title[new-requirement]

```
type Person = { age: number };
type Maybe<T> = Null | T;
function getAge(person: Maybe<Person>) {
    if (person) {
        return person.age;
    } else {
        return null; // well, we don't have an age dude.
    }
}
function canBuyBooze(person: Maybe<person>) {
    const age = getAge(person);
    return age ? age > 18 : false;
}
```

@css[fragment](those ? are going to be everywhere)

---
```
const getAge: = (person: Person) => person.age;

function canBuyBooze(person: Null | Person) {
    Maybe.of(Person)
        .map(getAge)
        .map(age > 18)
        .valueOr(false);
}
```
---

If you are always passing around Maybe when a value can be null then you can simply do...

```
const getAge = (person: Person) => person.age;

function canBuyBoozeByAge(person: Maybe<Person>) {
    person.map(getAge).map((age) => age > 18).valueOr(false);
}
```
---

A few things to know about Functors

@ul

- It's a container, a container never modifies its value. Cool

- transformation can be apply via `map`, it always return a new Functor.

- you can get its value at any time by using `value`

@ulend
