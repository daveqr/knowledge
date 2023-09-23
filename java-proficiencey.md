# Java Proficiency

## Records

Provide a more concise way to declare classes that are primarily used to store data, such as DTOs, POJOs, or entities with just fields and no behavior. Records help reduce boilerplate code.

```
public record Person(String name, int age) {}
```

## Hash-based data structures

### Maps

* **HashMap**: key=value pair; each key is unique 
* **TreeMap**: maintains elements in sorted (ascending) order; useful when you need to iterate through the entries in sorted order
* **LinkedHashMap**: maintains the insertion order of the entries
* **IdentityHashMap**: keys combared using object identity (==) instead of equals()
* **EnumMap**: very efficient use of enums as keys

### Sets

* **HashSet**: unique elements, not ordered
* **LinkedHashSet**: maintains order of insertion
* **TreeSet**: maintains elements in sorted (ascending) order
* **EnumSet**: very efficient use of enums as keys

### equals() and hashCode()

**equals()**: This method is used to compare two objects for logical equality, determining whether they represent the same data.

**hashCode()**: This method generates an int that represents an object, typically used for efficient storage and retrieval in hash-based collections.

Both needed to maintain the integrity and performance of hash-based data structures like HashSet and HashMap. equals() ensures correct logical comparisons of objects, while hashCode() ensures efficient storage and retrieval by placing objects in appropriate buckets based on their hash codes. To maintain consistency, if two objects are equal (equals() returns true), their hash codes should be the same, ensuring objects with the same content end up in the same bucket for retrieval efficiency.

### Same hash code but not equal

This is generally not correct, but if two objects share the same hash code but are not equal, they can still be inserted into a hash data structure. This may lead to reduced efficiency.

1. When an object is placed in a `HashMap` with a key, the key's hash will be used to determine which bucket the object is put into.
2. If two keys have the same hash but are not equal(), they will be put into the same bucket. When the objects are retrieved, under the covers the datastructure will use equals to determine which value to return.

As an example, say we have two objects, bob and joe, whose hashes are the same but are not equal. If these objects are used as the keys, the datastructure will place them in the same bucket, and will use equals() to retrieve the correct value.

	```
	// house.hashCode() == 300
	// car.hashCode() == 300
	map.put(house, theHouse);
	map.put(car, theCar); // theCar is in the same bucket as theHouse
	var car = map.get(car); // goes to the 300 bucket and uses equals to return theCar
	```

## Two approaches for associating values with enums

The first approach involves using the EnumMap data structure, which offers a structured and type-safe way to handle these mappings. The second approach uses an internal array (or other data structure) to associate values with enum constants and is more straightforward and lightweight, suitable for simple mappings.

### EnumMap Approach

Use a dedicated EnumMap data structure to map enum constants to values. It's a structured and type-safe way to handle these mappings.

```
public static void main(String[] args) {
    EnumMap<DayOfWeek, String> daysMap = new EnumMap<>(DayOfWeek.class);
	
    // Initialization with default values
    daysMap.put(DayOfWeek.MONDAY, "Monday");
    daysMap.put(DayOfWeek.TUESDAY, "Tuesday");
	
	// "Tuesday
	System.out.println(daysMap.get(DayOfWeek.TUESDAY))
}
```

### Array-based Approach

Use an internal array (or other data structure) to directly associate values with enum constants. It's a more straightforward and lightweight approach suitable for simple mappings.

```
enum Month {
	
    January(), February(), March(), April(), May(), June(), July();
	
    private static final Month[] months = Month.values();
	
    private static String getMonthNameByNumber(int month) {
        return Month.months[month - 1].toString();
    }
}
    
public static void main(String[] args) {
    String monthName = Month.getMonthNameByNumber(1);
    
    // Print the name of the month (January)
    System.out.println(monthName);
}
```