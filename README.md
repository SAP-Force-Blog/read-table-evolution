# Read Table Evolution

In this post we'll talk about the changes of ```READ TABLE```

A long time ago, we used to code like this 😱
```ABAP
READ TABLE lt_itab WITH KEY text = 'Your text'.
```
or this
```ABAP
READ TABLE lt_itab INTO ls_line WITH KEY text = 'Your text'
```

In the last update(2016)🙄 the SAP Dev Team include and recomend more inlines declaration

```ABAP
READ TABLE lt_itab INTO DATA(ls_itab) WITH KEY text = 'Your text'.
```
or
```ABAP
READ TABLE lt_itab ASSIGNING FIELD-SYMBOL(<fs_line>) WITH KEY text = 'Your text'.
```
or beyond using a try cath
```ABAP
lv_value = lt_itab[ text = 'Your text' ]-text.
```

But now you can improve your codefication with this
```ABAP
VALUE #( lt_itab[ text = 'Your text' ]-text DEFAULT '' ).
```
This way you don't need, work area, field-symbol, try catch or subrc. it's a more simple, more faster and more security way to read table.






In order to do this we need other codes associated, like:

```ABAP
DATA: lt_itab  TYPE STANDARD TABLE OF ty_string WITH HEADER LINE,
      ls_line  LIKE LINE OF lt_itab,
      lv_value TYPE string.
```

