# Lombok

## Project setup

1. Add to build.gradle:

	```
	plugins {
	    id 'java'
	    id "io.freefair.lombok" version "8.3"
	}
	```

1. Install Intellij `Lombok` plugin to add support to Intelli (eg test recognize getters).

## Features

### Getter

Can be added at the class level:

```
@Getter
public final class SquareAddress {
```

or at the field level:

```
@Getter
private final PieceType type;
```

### ToString

Add at the field level:

```
@ToString.Include
private final String move;
```

### val

Declare `final` local variables with type inference    

```
val message = "Hello, World!";
```