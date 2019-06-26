@title[topic]

### The Maybe Monad Functor

---

@title[spec]

### Fantasy Land Specification

(aka "Algebraic JavaScript Specification")

---?image=assets/fantasyland_1.png&size=contain

---?image=assets/fantasyland_2.png&size=contain
---
@title[the-what]

### Maybe is... Maybe means...

@css[text-blue fragment](Basically, is says that a value can be there, or not.)

---

@title[get-name-again]

```
function getFullName(person) {
    return person.firtName + ' ' + person.lastName;
}
```

@css[text-blue fragment](We figured out that person can be `null`...)

---

@title[explotion]

![boom](https://images2.minutemediacdn.com/image/upload/c_fill,g_auto,h_1248,w_2220/f_auto,q_auto,w_1100/v1554933379/shape/mentalfloss/nuclear-bomb-dirty-470309868.jpg)

---

@title[get-name-again]

```
type Person = { lastName: string, firstName: string };
function getFullName(person: Null | Person) {
    return person.firtName + ' ' + person.lastName;
}
```

@css[text-blue fragment](So... maybe we have a person, maybe we don't. Now it is clear.)
---
---

@title[get-name-again]

Maybe we can...

```
type Person = { lastName: string, firstName: string };
type Maybe<T> = Null | T;
function getFullName(person: Maybe<Person>) {
    return person.firtName + ' ' + person.lastName;
}
```

@css[text-blue fragment](Better, but the if is still there)
