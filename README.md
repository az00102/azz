
# Why are Type Guards Necessary? Discuss Various Types of Type Guards and Their Use Cases

In our everyday lives, we often encounter situations where we need to meet specific criteria to gain access to something. For example, a person wanting to enroll in the Level-2 course of Programming Hero must complete the Level-1 course first. This kind of conditional access is equally essential when building websites. To handle these scenarios, TypeScript offers a powerful feature called **Type Guards**.

## Understanding the Need for Type Guards

Consider a scenario where we have two types of users: `NormalUser` and `LevelOneUser`. Only a `LevelOneUser` should be able to access certain features, such as enrolling in Level-2. Without type guards, managing the distinct requirements for each user type can be challenging, especially when the user’s type isn’t known in advance.

Here’s an example to illustrate this:

```typescript
type NormalUser = { role: "normal" };
type LevelOneUser = { role: "level-1"; completedLevelOne: boolean };

function enrollInLevelTwo(user: NormalUser | LevelOneUser) {
  if (user.role === "level-1" && user.completedLevelOne) {
    console.log("Enrolled in Level-2");
  } else {
    console.log("Enrollment failed. Requirements not met.");
  }
}
```

In this function, if the user is a `NormalUser`, they cannot enroll as they don’t meet the Level-1 requirements. However, if the user is a `LevelOneUser` who has completed Level-1, they successfully enroll. Here, type guards help us differentiate between user types and handle each case accordingly.

## Common Type Guards in TypeScript

### 1. **Typeof Operator**

The `typeof` operator serves as a type guard for primitive types like `number`, `string`, etc. It checks the type of a value at runtime, allowing us to handle different types effectively. Here’s an example:

```typescript
function enrollUser(id: number | string) {
  if (typeof id === "string") {
    console.log("Enrolling user by username:", id);
  } else {
    console.log("Enrolling user by ID:", id);
  }
}
```

In this example, `typeof id === "string"` checks if the input is a string and logs the corresponding enrollment method based on whether the input is a string or a number.

### 2. **Instanceof Operator**

The `instanceof` operator is useful for checking whether an object is an instance of a specific class. This type guard is particularly effective when working with class-based types. Here’s how it works:

```typescript
class LevelOneCourse {
  complete() {
    console.log("Level 1 completed");
  }
}

class LevelTwoCourse {
  complete() {
    console.log("Level 2 completed");
  }
}

function completeCourse(course: LevelOneCourse | LevelTwoCourse) {
  if (course instanceof LevelOneCourse) {
    course.complete();
  } else {
    course.complete();
  }
}
```

In this code, `instanceof` checks if `course` is an instance of `LevelOneCourse`. This allows us to determine the course level and manage completion accordingly.

## Conclusion

In conclusion, type guards are essential tools in TypeScript for handling complex conditions and ensuring type safety. By using type guards like `typeof` and `instanceof`, we can manage conditional logic based on types, leading to flexible, safe, and robust applications. Type guards simplify conditional checks, reduce runtime errors, and help make our TypeScript code both efficient and reliable.
