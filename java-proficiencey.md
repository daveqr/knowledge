# Java Proficiency

## Records

Provide a more concise way to declare classes that are primarily used to store data, such as DTOs, POJOs, or entities with just fields and no behavior. Records help reduce boilerplate code.

```
public record Person(String name, int age) {}
```

## equals() and hashCode()

**equals()**: This method is used to compare two objects for logical equality, determining whether they represent the same data.

**hashCode()**: This method generates a numeric code that represents an object, typically used for efficient storage and retrieval in hash-based collections.

Both needed to maintain the integrity and performance of hash-based data structures like HashSet and HashMap. equals() ensures correct logical comparisons of objects, while hashCode() ensures efficient storage and retrieval by placing objects in appropriate buckets based on their hash codes. To maintain consistency, if two objects are equal (equals() returns true), their hash codes must be the same, ensuring objects with the same content end up in the same bucket for retrieval efficiency.

## Comparing EnumMap to Array-Based Enum Value Mapping

Two different approaches to directly associate values with enum constants.

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