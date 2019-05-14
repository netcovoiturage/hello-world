### highlighting
    
```
#To count the number of matches of a pattern, use the substitute command with the n flag. The following shows the number of times that pattern matches text in the current buffer:
:%s/pattern//gn

#Omit g to display the number of lines where the pattern matches:
:%s/pattern//n

#To restrict the count to a region of the text, specify a range instead of % (% means all lines). For example, the following counts the number of occurrences in lines 10 to 50 inclusive:
:10,50s/pattern//gn

#The following counts the number of occurrences in the lines in the most recent visual selection.
:'<,'>s/pattern//gn
``` 
