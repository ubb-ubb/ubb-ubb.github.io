---
layout: post
title: Effective Java Chapter-1 Creating and Destroying objects
published: true
---

## 1.STATIC FACTORY METHOD INSTEAD CONSTRUCTORS
Good old traditional way to create object is using constructor. Another technique to create object is called ___static factory method___.
Static factory method is different than design pattern factory method.
Class can provide a public static factory method, simply static method that returns an instance of class.

```
public static Boolean valueOf(boolean b) {
    return b ? Boolean.TRUE : Boolean.FALSE;
}

Boolean bool = valueOf(false);

```
Advantages: 

- Static factory method has a name. Easier to use and understand.
- Static factory method does not require to create new object each time they are created.
- Static factory method can return object type unlike constructors.
- Static factories providing, returned object can vary from call to call as a function of the input parameters.
- Static factories providing, class of the returned object need not exist when the class containing the method is written.

Disadvantages:

- Providing only static factory method to create new object without public-protected constructors can not be subclassed.
- Hard to find by programmers.

## 2. CONSIDER BUILDER WHEN FACED WITH MANY CONSTRUCTOR PARAMETERS

Static factory and constructors has drawbacks when class has large number of parameters.
For example, Nutrition Facts labels must have =>serving size, serving per container,optional=> calories, total fat, trans fat, cholesterol etc..
Telescoping constructor pattern is a solution. But hard to write and read.

```
public class NutritionFacts {
private final int servingSize; // (mL)              required
private final int servings;    // (per container)   required
private final int calories;    // (per serving)     optional
private final int fat;         // (g/serving)       optional
private final int sodium;      // (mg/serving)      optional
private final int carbohydrate; // (g/serving)      optional

public NutritionFacts(int servingSize, int servings) {
this(servingSize, servings, 0);
}
public NutritionFacts(int servingSize, int servings,int calories) {
this(servingSize, servings, calories, 0);
}
public NutritionFacts(int servingSize, int servings,int calories, int fat) {
this(servingSize, servings, calories, fat, 0);
}
public NutritionFacts(int servingSize, int servings,int calories, int fat, int sodium) {
this(servingSize, servings, calories, fat, sodium, 0);
}

public NutritionFacts(int servingSize, int servings,int calories, int fat, int sodium, int carbohydrate) {
this.servingSize = servingSize;
this.servings = servings;
this.calories = calories;
this.fat = fat;
this.sodium = sodium;
this.carbohydrate = carbohydrate;
}
}
```

Second alternative is JavaBeans pattern. Parameterless constructor, then call setter methods to set each required parameters.
However JavaBeans pattern precludes possibility of making a class immutable. Programmers should ensure thread safety. 
Also constructing object without necessary attributes can cause problems after construction.


Builder pattern shows a solution for multiple constructor parameter classes. 
Instead creating object directly, client calls a consturctor with all required parameters and gets Builder object. 
Then client calls setter like methods on builder object for optional parameters. Then client calls build method to generate object.
```
public class Cat {
    private final String name;
    private final int age;
    private final double weight;
    private final double height;

    public static class Builder {
        // Necessary Parameters
        private final String name;
        private final int age;

        // Optional parameters
        private double weight = 0;
        private double height = 0;

        public Builder(String name, int age) {
            this.name = name;
            this.age = age;
        }

        public Builder weight(int val) {
            weight = val;
            return this;
        }

        public Builder height(int val) {
            height = val;
            return this;
        }

        public Cat build() {
            return new Cat(this);
        }
    }
    private Cat(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.weight = builder.weight;
        this.height = builder.height;
    }
}
```

```
Cat cat = new Cat.Builder("name", 15).build();
Cat cat2 = new Cat.Builder("name", 15).height(20).weight(10).build();
```

This pattern is easy to write and easy to read. Validity checks can be done in builders constructors and methods.
Pattern is well suited for class hierarchies. 

Disadvantage:
- In order to create object, Builder object must be created. It could be a problem in performance critical situations.
- Builder pattern is more verbose.
- It should be used only if there are enough parameters to make it worthwhile,___four or more___.

Builder pattern is good choice for creating class whose constructors or static factories would have more than a handful parameters.


