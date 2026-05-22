[em construção...]

**Object Oriented Programming** **(OOP**) is really useful, so let's take a look at how you would actually go about implementing OOP. So in the last lesson we talked of this example of the restaurant, where we hired three types of staff, and we had a manager who would then manage all of these three different types of staff.  Now, the reason why OOP is called that is because **it's trying to model a real world object**.

So let's say that we are creating a virtual restaurant. Well, in this case, we probably have to model a virtual chef, waiter, cleaner, and manager.

Let's say that we were going to model a `waiter`. In order to model our waiter, there's probably two things we need to think about: **what it has and what it does**. In terms of what it **has**, well, it might have variables like, is it holding a plate, true or false? Or which tables is it responsible for? Maybe table 4, 5 and 6. Now it also has things that it **does**. Maybe they're able to take an order to the chef and maybe they also need to take payments and add money to the restaurant. This can be translated in the code below:

```python
# what he HAS:
is_holding_plate = True
tables_responsible = [4, 5, 6]

# what he DOES:
def take_order(table, order):
	# takes order to chef

def take_payment(amount):
	# add money to the restaurant
```

So these two different things, what the waiter has and what the waiter does are the two most important things that make up an object: its **attributes** (what he has)and its **methods** (what he does).

Updated code:
```python
-> # attributes:
is_holding_plate = True
tables_responsible = [4, 5, 6]

-> # methods:
def take_order(table, order):
	# takes order to chef

def take_payment(amount):
	# add money to the restaurant
```

By looking at the code, you can pretty much see that the attributes is basically a variable (or more). An `attribute` is just a fancy word for a variable that's associated with a modeled object like our waiter here. Because it's not just a free floating bit of a variable, right? It's not just somewhere in our `main.py`. It's actually a variable that's attached to a particular object - **it's the waiter's tables responsible**.

Now the method goes along the same vein. These, as you can clearly see, are just functions but we call it a `method` because it's a function that a particular **modeled object** can do. We need a waiter object to take the order and we need a waiter object to take payment. Again, these are not just free-floating functions.

Now, there's a lot of new words that are part of OOP and programming in general, we're going to see them again and again, and eventually it's going to become a word that's going to be in your dictionary. But for now, just remember that in OOP, we're trying to model real-life objects and those objects have things and they also can do things. The things that they have are their attributes and these are usually modeled with variables, and the things that they can do are called methods and they are modeled by functions.

Essentially...
... an object is just a way of combining some piece of data and some functionality altogether in the same thing.

But we can actually have multiple objects generated from the same type. So when we've modeled a particular job in our virtual restaurant like the waiter's job, and we figured out what are the things that the waiter have and what are the things that it can do, well, **we can actually generate multiple versions of the same object**.

So we could have Henry who's a waiter and we can also have Betty who's a waiter, and we can generate as many of these as we want from the same blueprint. And in OOP we call this blueprint, or this type, a `class`. And we call these individual objects that are generated from the blueprint an `object`.

So now let's take a look at how you use these class blueprints to create an actual object.


### Constructing objects

So here's a blueprint for a car. And that blueprint that specifies what the color of the car is, how many wheels it should have, what its mileage is, how much fuel it has, all of those bits of data combined with all of its functionality like the ability to drive, the ability to stop and break. And that blueprint which models a real-life car is known as the class. And it's from this blueprint, this class, that we can generate as many objects as we want.

Now, the object is the actual thing that we're going to be using in our code. The code equivalent of what just happened, creating a new object from a blueprint,
looks like this in Python:
```python
car = CarBlueprint()
```

You have the class, `CarBlueprint()`,  which is normally written with the first letter of each word capitalized, which is known as **Pascal case**. This is to differentiate it from all the variable and function names that we give in Python, where each word is separated by underscores.

So in this case, the `car` is the object and it gets created from this `CarBlueprint`. All we have to do to create the object from the class is to give the object a name, it can be anything you want, set it equal to the name of the class, and then the parentheses, which in the same way as it activates the function, it activates the construction of this object from the blueprint.
