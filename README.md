# get_next_line

A C function that reads a file one line at a time: every call returns the next line, until the end of the file. It works with any buffer size, from 1 byte up.

I used it later to read the maps in so_long.

## Use

```c
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include "get_next_line.h"

int main(void)
{
	int		fd = open("notes.txt", O_RDONLY);
	char	*line;

	while ((line = get_next_line(fd)))
	{
		printf("%s", line);
		free(line);
	}
	return (0);
}
```

```bash
cc -D BUFFER_SIZE=42 main.c get_next_line.c get_next_line_utils.c
```
