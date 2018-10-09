# Virtual Memory

Basically that's the thing, which makes your computer feel super slow when RAM heavy applications are loaded.

## Explanation

One picture, which describes it is with few words:

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Virtual_memory.svg/250px-Virtual_memory.svg.png)

Basically the CPU sees a very large address space, which is managed by the MMU - memory management unit. That's a physical chip *automatically translating virtual addresses to physical addresses*.

## Advantages

* The applications do not have to manage their (shared) address space.
* Increased security due to memory isolation.
* Using more memory than is physically available by [paging](https://en.wikipedia.org/wiki/Paging).

## Notes

page
  : is a fixed-length contiguous block of (virtual) memory

The size of a page can be determined in C by using `sysconf`:

```C
#include <stdio.h>
#include <unistd.h> /* sysconf(3) */

int main(void) {
	printf("The page size for this system is %ld bytes.\n",
	       sysconf(_SC_PAGESIZE)); /* _SC_PAGE_SIZE is OK too. */

	return 0;
}
```

On `x86-64` it is usually sth between 4 KiB (page frame) and 1GiB, most often 2MiB.

page table
  : each entry in it represents a page

page frame
  : smallest page possible

## Sources

* https://en.wikipedia.org/wiki/Virtual_memory
