How do the four pillars of OOP—Inheritance, Polymorphism, Abstraction, and Encapsulation—help manage logic and reduce complexity in large-scale TypeScript projects?


Once a TypeScript project gets bigger, things start getting a little harder to keep in order. Object-Oriented Programming gives you a few basic ideas that help keep the whole thing from turning into a mess: Inheritance, Polymorphism, Abstraction, and Encapsulation.

Inheritance is basically one class borrowing stuff from another class. That sounds simple, and it is, but it saves you from repeating the same code all over the place.

```typescript
class Animal {
  constructor(public name: string) {}
  makeSound(): string {
    return "Some generic sound";
  }
}

class Dog extends Animal {
  makeSound(): string {
    return "Woof!";
  }
}
```

Dog gets the name property from Animal and can still change makeSound if it wants to. So the shared stuff stays in one place.

Polymorphism means you can treat different objects like they belong to the same group, even if they do their own thing under the hood.

```typescript
const animals: Animal[] = [new Animal("Generic"), new Dog("Rex")];
animals.forEach((animal) => console.log(animal.makeSound()));
```

Each object still does its own version of makeSound, and the code calling it doesn't really need to care which one it got.

Abstraction hides the ugly details and gives you something simpler to work with. Abstract classes are one way to set that up, because they tell subclasses what they have to provide.

```typescript
abstract class Shape {
  abstract calculateArea(): number;
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }
  calculateArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}
```

Code that uses Shape doesn't need to know the math behind every shape. It just knows it can ask for the area and get a result back.

Encapsulation is about not letting outside code poke at everything directly. You keep the important state private and give people a controlled way to use it.

```typescript
class BankAccount {
  private balance: number = 0;

  deposit(amount: number): void {
    if (amount > 0) {
      this.balance += amount;
    }
  }

  getBalance(): number {
    return this.balance;
  }
}
```

The balance value can't just be changed from outside the class, which helps stop weird or invalid updates.

These four ideas do a decent job of keeping larger TypeScript codebases from getting out of hand. Inheritance cuts down repetition, polymorphism keeps code flexible, abstraction hides the noisy parts, and encapsulation protects state from random changes. Used together, they make the codebase a lot easier to live with as it grows.