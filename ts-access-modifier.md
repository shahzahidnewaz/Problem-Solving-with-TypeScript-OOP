# Access Modifiers in TypeScript

## Introduction
Access modifiers control who can use the properties and methods of a class. They work like locks on the doors of a house, keeping your data safe from accidental changes.

## Using public
`public` members can be used from anywhere. This is the default.

```ts
class Account {
    public owner: string = "Rahim";
}
const account = new Account();
console.log(account.owner); //Ok
```

## Using private
`private` members can only be used inside the same class.

```ts
class Account {
    private balance: number = 1000;
}
const account = new Account();
console.log(account.balance); //Error
```

## Using protected
`protected` members can be used inside the class and its child classes, but not outside.

```ts
class Account {
    protected type: string = "Savings";
}
class StudentAccount extends Account {
    getType(): string {
        return this.type; //Ok
    }
}
```

## Using readonly
`readonly` members can be set once, in the declaration or constructor, and never changed.

```ts
class Account {
    readonly id: number;

    constructor(id: number) {
        this.id = id;
    }
}
const account = new Account(1);
account.id = 2; //Error
```

## Conclusion
Keep members `private` by default, use `protected` for child classes, open up `public` only when needed, and mark values that must never change as `readonly`. These checks happen at compile time only.