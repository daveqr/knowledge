# Intellij customization

## Custom keyboard shortcuts

| **Functionality**                            | **Shortcut**                  |
| -------------------------------------------- | ----------------------------- |
| Git diff                                          | Shift-G Shift-D                |

## Live templates

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

**foff**

```
// @formatter:off
```

**fon**

```
// @formatter:on
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
