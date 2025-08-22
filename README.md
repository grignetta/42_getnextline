# get_next_line (mandatory&bonus)

## 📖 About
**Mandatory part** of 42’s `get_next_line`: read a file descriptor **one line at a time**.
Returns a newly allocated string, or `NULL` on EOF/error.
**Bonus part** of 42’s `get_next_line`: **supports multiple FDs** concurrently by keeping per-FD state.

## Function prototype
```bash
char *get_next_line(int fd);
```
## Build get_next_line library
Run '**make**' to compile both mandatory get_next_line function or '**make bonus**'.
This would create a static library called libgnl.a or libgnl_bonus.a respectively.
BUFFER_SIZE is possible to change during compilation process.
```bash
make
# or override:
make BUFFER_SIZE=4096
```
## Usage example
Add as a header into your program
```bash
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("Makefile", O_RDONLY);
    char *line;

    if (fd < 0) return 1;
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```
Compile and run your program
```bash
cc main.c libgnl.a -o gnl_test
./gnl_test
```
