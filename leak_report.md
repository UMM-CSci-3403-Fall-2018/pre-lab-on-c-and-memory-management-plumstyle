# Leak report

As the second type of memory leaks described in the repository, the function is_clean() calles helper function strip() which has a inside function calloc() that takes memory. In order to free the space without destroy the current functionality, we have to free space after the actually data that passed by calloc() is entirely used. Therefore we call free(cleaned) right after we assign the value of strip() to $result.
The precise procedure is:
@line 69 in check_whitespace.c we add free(cleaned)

