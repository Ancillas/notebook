# VIM Cheatsheet

## Delete from current line to target line

### Normal Mode

*Delete from current line to line 45*

```
d45G
```

### Command Mode

*Delete from current line to line 45 (alternate)*

```
:,45d
```

*Delete from line 5 to line 45*

```
:5,45d
```

## Line Numbering

### Enable line numbers

```
:set nu
```

### Enable relative line numbers

```
:set rnu
```

### Disable relative line numbers

``` 
set rnu!
```

or

```
set nornu
```

## Moving text

### Move lines 1-3 to line 5 (credit: Kemin Zhou)

```
:1,3 mo 5
