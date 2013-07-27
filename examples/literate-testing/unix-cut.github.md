The numeric ranges of the Unix command "cut"
============================================

Use single numbers to extract one specific field:

```
$ echo "one:two:three:four:five:six" | cut -d : -f 1
one
$ echo "one:two:three:four:five:six" | cut -d : -f 4
four
$
```

Use commas to inform more than one field:

```
$ echo "one:two:three:four:five:six" | cut -d : -f 1,4
one:four
$
```

Note that inverting the order will *not* invert the output:

```
$ echo "one:two:three:four:five:six" | cut -d : -f 4,1
one:four
$
```

Use an hyphen to inform a range of fields, from one to four:

```
$ echo "one:two:three:four:five:six" | cut -d : -f 1-4
one:two:three:four
$
```

If you omit the second range number, it matches until the last:

```
$ echo "one:two:three:four:five:six" | cut -d : -f 4-
four:five:six
$
```

The same rules apply for the -c option, which instead of fields,
extract individual characters from the text. Watch the next
series of commands and check their output at the right side:

```
$ txt="abcdefghij"
$ echo "$txt"                      #→ abcdefghij
$ echo "$txt" | cut -c 1           #→ a
$ echo "$txt" | cut -c 4           #→ d
$ echo "$txt" | cut -c 1,4         #→ ad
$ echo "$txt" | cut -c 4,1         #→ ad
$ echo "$txt" | cut -c 1-4         #→ abcd
$ echo "$txt" | cut -c 4-          #→ defghij
```

cut is cool, isn't it?

> Note: To automatically test all the 14 shell commands in this
> article, just run: `../../doctest.sh unix-cut.github.md`