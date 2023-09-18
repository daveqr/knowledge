# Intellij Live Templates and Code Snippets

Intellij Live Templates and VS Code snippets are predefined code snippets that you can quickly insert into your code by typing an abbreviation and pressing the Tab key.

## Code Snippets

View -> Command Pallet -> Configure user snippets

## Intellij Live Templates

### Custom templates

To create custom templates:

```
Preferences -> Live Templates
```

**should**

```
@Test
public void should$NAME$() {
    $TEST$
}
```


**lambda**

```
($PARAM$) -> {
    $BODY$
}
```

**switch**

```
switch ($VAR$) {
    case $CASE1$:
        $END$
        break;
    case $CASE2$:
        $END$
        break;
    default:
        $END$
}
```

### Built-in tempaltes

| Shortcut | Description                                   |
|----------|-----------------------------------------------|
| fori     | Create iteration loop                        |
| i        | Iterate iterable or array                    |
| itar     | Iterate elements of array                    |
| itco     | Iterate elements of Collection               |
| iter     | Iterate Iterable or array                    |
| itli     | Iterate elements of List                     |
| lst      | Fetch last element of an array               |
| main     | Main method                                  |
| mn       | Set lesser value to a variable               |
| mx       | Set greater value to a variable              |
| prsf     | Private static final                         |
| ritar    | Iterate elements of array in reverse order  |
| soutv    | Print a value to System.out                   |
| toar     | Store elements of Collection into array      |
