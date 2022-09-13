# Polymorphism & Composition Homework - Quiz

# Polymorphism

1. What does the ___word___ 'polymorphism' mean?

    It literally refers to the property of taking multiple forms.

2. What does it mean when we apply polymorphism to OO design? Give a simple Java example.

    It means that different objects can have different forms, for example through inheritance they can use methods and properties of a superclass and at the same time have their own methods: a subclass 'MechanicalDog' may have the properties of a parent class 'Toy' and at the same time use the methods promised by an interface 'IRobot'. In addition to it, it may have their own methods or 'override' the inherited methods. 

3. What can we use to implement polymorphism in Java?

    Inheritance, with the use of SuperClasses, like Abstract Classes, and related child Classes. Also, different classes may inherit the same methods from the same Interface and implement them in different ways.

4. How many 'forms' can an object take when using polymorphism?

    A child of an abstract class can only refer to that class but can inherit from multiple interfaces. Interfaces do not provide specific instructions on how their methods will be implemented;on the other side, methods and properties inherited from superclasses con also be overridden, and subclasses can have their own methods - the convention is that subclasses should still be working with no disruption if a parent class is missing, coherently with the principles of loose coupling. 

5. Give an example of when you could use polymorphism.

    ```java

    package stalls;

    import behaviours.ISecurity;
    import people.Visitor;

    public class TobaccoStall extends Stall implements ISecurity {

        public TobaccoStall(String name, String ownerName, ParkingSpot parkingSpot, int rating) {
            super(name, ownerName, parkingSpot, rating);
            }

            public boolean isAllowedTo(Visitor visitor) {
                boolean isAllowed = false;
                if (visitor.getAge() < 18){
                    isAllowed = false;
                } else {
                    isAllowed = true;
                }
                return isAllowed;
            }
        }
    ```

    The screenshot shows the code of the TobaccoStall Class, child of an abstract Class Stall, and also implements the ISecurity Interface.
    
    All values passed to the class are defined in the super Class Stall, and this allows other Stall subclasses to do the same, avoiding to write the same code in each one of them. If changes have to be done, in such a context they will mainly happen in the parent class, allowing again to write much less code.

    The method isAllowedTo is passed from the ISecurity Interface and built into the subclass according to the specific functionality needed. Other Stall objects will build the same method according to different criteria.

    If necessary, TobaccoStall might have its own specific methods too.  



#
# Composition and Aggregation

6. What do we mean by 'composition' in reference to object-oriented programming?

    We refer to 'composition' when we see an object being PART OF another object (i.e. a Class being a component of another Class, like a Roof (that can be a Class on its own) being part of a House Class.

    Without the object owned by a Class, that Class is destroyed.

7. When would you use composition? Provide a simple example in Java.

    ```Java
    public class Flight {

        ArrayList<Pilot> pilots;
        ArrayList<CabinCrewMember> cabinCrewMembers;
        ArrayList<Passenger> passengers;
        Plane plane;
        String flightNumber;
        String destination;
        String departureAirport;
        String departureTime;

        public Flight(ArrayList<Pilot> pilots,
                    ArrayList<CabinCrewMember> cabinCrewMembers,
                    ArrayList<Passenger> passengers,
                    Plane plane,
                    String flightNumber,
                    String destination,
                    String departureAirport,
                    String departureTime){
            this.pilots = pilots;
            this.cabinCrewMembers = cabinCrewMembers;
            this.passengers = passengers;
            this.plane = plane;
            this.flightNumber = flightNumber;
            this.destination = destination;
            this.departureAirport = departureAirport;
            this.departureTime = departureTime;
        }
    ```

    This part of code shows a Flight Class made of passengers, crew members, and other objects - some are actual Classes, some just basic data.
    
    If those objects did not exist, the Class Flight as it is would not exist.

8. Give a difference between composition and aggregation?

    Aggregation is when an object contains another object but it would still exist if that object is missing.
    
    In this case we are talking about what ab object HAS, and consider the Class as an 'aggregation' of other objects.

9. What is/are the advantage(s) of using composition/aggregation?

    We should favour composition over inheritance to not pollute or conflict with existing hierarchies, and ofor a Class to access behaviours from othr Classes and still exist if the owned objects diasppear.

10. When using composition, when an object is destroyed, what happens to all the objects it is composed of?

    Nothing to the objects who compose it. If the contrary were to happen, the object owner would be destroyed.

11. When using aggregation, when an object is destroyed, what happens to all the objects it is composed of?

    They still exist.