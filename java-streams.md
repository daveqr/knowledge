# Streams

## Stream pipeline

The most common pattern for streaming is known as a stream pipeline, consisting of a source followed by zero or more intermediate operations and then a terminal operation.

```
<source>.<intermediate operations>.<terminal operations>
```

Intermediate operations act as a configuration or specification for what should be done when a terminal operation is eventually invoked. Think of it like setting up a series of steps or instructions for processing data, but those steps are not carried out until you explicitly ask for the result by invoking a terminal operation. This deferred execution allows for lazy evaluation, which can be more efficient, especially when working with large data sets or when you want to avoid unnecessary computations.


### Source

A source is the data source providing the raw data to process. Common sources include collections, arrays and i/o operations (ie reading lines from a file).

### Intermediate operations

Intermediate operations are optional, but they allow you to transform, filter, or modify the data in the stream. You can chain multiple intermediate operations together to create a data processing pipeline. These operations return a new stream, which means you can chain them one after another.

These operations include `filter`, `map`, `flatMap`, `distinct`, `sorted`, `peek`, `limit`, `skip`, `takeWhile` and `dropWhile`.

```
Stream<Integer> numbers = Stream.of(1, 2, 3, 4, 5);
Stream<Integer> evenNumbersStream = numbers.filter(n -> n % 2 == 0);
```

Create a pipelin by chaining intermediate operations:

```
List<String> result = people.stream()
    .filter(person -> person.getAge() > 18)
    .map(Person::getName)
    .collect(Collectors.toList());
```

### Terminal operation

A terminal operation is required to produce a result or trigger the execution of the stream pipeline. Terminal operations consume the data in the stream and produce a result or perform some side effect. Once a terminal operation is invoked, the stream is consumed, and you cannot use it again.

Examples of terminal operations include `forEach`, `toArray`, `reduce`, `collect`, `min`, `max`, `sum`, `average`, `count`, `distinct`, `sorted`, `peek`, `limit`, `skip`, `anyMatch`, `allMatch`, `noneMatch`, `findFirst`, and `findAny`.

```
long count = people.stream()
    .filter(person -> person.getAge() > 18)
    .count(); // This is a terminal operation; it triggers the pipeline's execution.
```

### Commonly-used collectors

* **toList()** and **toSet()**

	```
	List<String> namesList = stream.collect(Collectors.toList());
	Set<Integer> numbersSet = intStream.collect(Collectors.toSet());
	```
	
* **joining()**: concatenates the elements of a stream into a single String, optionally allowing you to specify delimiter, prefix, and suffix

	```
	String joinedNames = stream.collect(Collectors.joining(", "));
	```
	
* **toMap()**: converts elements of a stream into a Map. You specify how to extract keys and values from the elements:

	```
	Map<String, Integer> nameToAgeMap = peopleStream.collect(Collectors.toMap(Person::getName, Person::getAge));
	```

* **toConcurrentMap()**: Similar to `toMap()`, but it returns a concurrent map (ConcurrentHashMap) suitable for parallel operations.

	```
	ConcurrentMap<String, Integer> concurrentMap = peopleStream.collect(Collectors.toConcurrentMap(Person::getName, Person::getAge));
	```
	
* **groupingBy()**: group elements of a stream into a Map based on a classification function. It's particularly useful for creating grouped data structures.

	```
	Map<String, List<Person>> peopleByCity = peopleStream.collect(Collectors.groupingBy(Person::getCity));
	```	
	
* **partitioningBy()**: partitions the elements of a stream into two groups based on a predicate, resulting in a Map<Boolean, List<T>>. It's often used for binary classification.

	```
	Map<Boolean, List<Person>> adultsAndMinors = peopleStream.collect(Collectors.partitioningBy(person -> person.getAge() >= 18));
	```	
	
* **averagingInt(), averagingDouble(), and averagingLong()**: calculate the average of elements in a numeric stream.

	```
	double averageAge = peopleStream.collect(Collectors.averagingInt(Person::getAge));
	```			

* **summingInt(), summingDouble(), and summingLong()**: calculate the sum of elements in a numeric stream.
	```
	int totalAge = peopleStream.collect(Collectors.summingInt(Person::getAge));
	```		

* **maxBy() and minBy():**:  find the maximum and minimum elements in a stream based on a specified comparator.
	```
	Optional<Person> oldestPerson = peopleStream.collect(Collectors.maxBy(Comparator.comparingInt(Person::getAge)));
Optional<Person> youngestPerson = peopleStream.collect(Collectors.minBy(Comparator.comparingInt(Person::getAge)));
	```	
	
## Other patterns

### Stream of primitives

```
IntStream intStream = IntStream.of(1, 2, 3, 4, 5);
int sum = intStream.sum();
```

### Optional and null handling

```
List<String> names = Arrays.asList("Alice", "Bob", null, "Charlie");
List<String> nonNullNames = names.stream()
    .filter(Objects::nonNull)
    .collect(Collectors.toList());
```

### Grouping and partitioning

```
List<Person> people = ...
Map<String, List<Person>> peopleByCity = people.stream()
    .collect(Collectors.groupingBy(Person::getCity));
```

### FlatMap

Flatten nested streams or collections into a single stream. This is especially useful when dealing with nested data structures.

```
List<List<Integer>> nestedLists = ...
List<Integer> flatList = nestedLists.stream()
    .flatMap(List::stream)
    .collect(Collectors.toList());
```

### Infinite streams

You can create infinite streams using methods like Stream.generate or Stream.iterate to represent sequences or streams that are theoretically unbounded.

```
Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 1);
```

### Parallel streams

Allows concurrent processing of elements on multi-core processors.

```
List<Integer> numbers = ...
long count = numbers.parallelStream().filter(n -> n % 2 == 0).count();
```