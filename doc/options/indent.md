# Change the indentation of lists

The default options map for lists is as follows:
```clojure
 :list {:constant-pair-min 4,
        :constant-pair? true,
        :hang-avoid 0.5,
        :hang-diff 1,
        :hang-expand 2.0,
        :hang-size 100,
        :hang? true,
        :indent 2,
        :indent-arg nil,
        :indent-only-style :input-hang,
        :indent-only? false,
        :pair-hang? true,
        :replacement-string nil,
        :respect-nl? false},
```
Indentation for lists is primarily configured by `:indent`, though 
`:indent-arg` will come into play if it is non-nil.

### What is a hang and how does it differ from a flow?

zprint has a name for these two different approaches to formatting:

  * Hang

```clojure
(this is
      a
      hang)
```

  * Flow

```clojure
(this
  is
  a
  flow)
```
### When does zprint do a hang or a flow?

There are a number of complex heuristics about when zprint will do a hang
or a flow, depending in many cases on how many lines it will take (less is
better), and how it will "look".  To simplify this situation, the basic rules
are:

zprint will hang when:

  * The entire list will not fit in the remaining space on the current line
  * The first element of a list could be a function name
  * The hang approach will not take more lines than the flow approach
  * Some other complex calculations on how it will "look"

Clearly, when zprint is doing a hang, the configured `:indent` is meaningless,
since the indent for the subsequent lines is based on the size of the first
element of the list.

### When does zprint use `:indent`?

zprint will use the `:indent` for a list when it is doing a flow, which is
when:

  * The entire list will not fit in the remaining space on the current line
  * The first element of a list could be a function name
  * A flow is considered "better" than a hang

In this case, zprint will place a number of spaces controlled by `:indent`
in front of the second and subsequent elements of the list.

Note that if zprint doesn't think that the first element can be a function
name (for example, it is a number), then zprint will not use `:indent` for
subsequent elements, it will use a single space.  For example:

```clojure
(555
 aaaa
 bbbb
 cccc)
```
### Different indents for body functions and argument functions?

At some point, the "community standards" for Clojure source formatting
made a distinction between "body functions" and "argument functions",
and wanted "argument functions" to have an indent of 1, and "body functions"
to have an indent of 2.  The theory seemed to be that "body functions"
were functions which had executable forms in them, oftern (though not
always) of indeterminate number.  "Argument functions", on the other
hand, had arguments (typically a fixed number) which were values and
not primarily executable forms.  

To support this (to my mind rather unnecessary and not widely adopted)
distinction, zprint will accept the suffix `-body` to many of the function
types, and will also accept a value for `:indent-arg`, which (if non-nil)
will be used as the indent for argument functions (which is 
everything that is not explicitly classified as a body function).

You can get this sort of indentation by using `{:style :community}`.  It
is defined as:
```clojure
    :community {:binding {:indent 0},
                :fn-map {"apply" :none,
                         "assoc" :none,
                         "filter" :none,
                         "filterv" :none,
                         "map" :none,
                         "mapv" :none,
                         "reduce" :none,
                         "remove" :none,
                         "with-meta" :none-body},
                :list {:indent-arg 1},
                :map {:indent 0},
                :pair {:indent 0}},
```
In this definition you can see where `:indent-arg` is given the value of
1.








