

# Leak report

clean_whitespace.c is finding 46 bytes of memory loss. The memory is being allocated by 'calloc' on line which is then called in three different locations within the file: in 'strip' on line 41, in 'is_clean' on line 62, and in 'main' on line 87.

I can't free up the memory in strip because that information is used in is_clean. However, it is not returned in is_clean, so I can free the memory once it is done being used in is_clean.
