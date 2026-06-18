# MIT 6.1810 - Resources and References

## Course Materials

### Official Course Page
- [MIT OCW 6.1810](https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/)
- [Course Pages](https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/pages)

### xv6 Resources
- [xv6 Source Code](https://github.com/mit-pdos/xv6-riscv) - GitHub repository
- [xv6 Documentation](https://pdos.csail.mit.edu/6.828/2024/xv6/) - Additional docs
- [xv6 Labs Guide](https://pdos.csail.mit.edu/6.828/2024/labs/) - Lab instructions
- [MIT 6.828 Course](https://pdos.csail.mit.edu/6.828/2024/) - Related course page

## Books and Textbooks

### Primary
- **xv6 Book** - "Operating Systems: Three Easy Pieces" by Arpaci-Dusseau (free online)
  - [OSTEP Website](https://pages.cs.wisc.edu/~remzi/OSTEP/)
  - Covers: virtualization, concurrency, persistence

### Supplementary
- **Operating System Concepts** (Dinosaur Book) by Silberschatz et al.
  - Comprehensive reference for OS concepts
- **Modern Operating Systems** by Tanenbaum
  - Good for microkernel discussion
- **Linux Kernel Development** by Love
  - Practical Linux kernel internals
- **Understanding the Linux Kernel** by Bovet & Cesati
  - Deep dive into Linux internals

## Online Resources

### Tutorials and Guides
- [Writing an OS in Rust](https://os.phil-opp.com/) - Modern OS development tutorial
- [OSDev Wiki](https://wiki.osdev.org/) - Extensive OS development wiki
- [James Molloy's Kernel Tutorial](http://www.jamesmolloy.co.uk/tutorial_html/) - Classic kernel tutorial
- [OS Course at MIT](https://pdos.csail.mit.edu/6.828/) - Related MIT course

### Video Lectures
- [MIT 6.1810 Lectures](https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/)
- [Ben Eater's breadboard computer](https://www.youtube.com/playlist?list=PLowKtXNTBypFtan4Zddo-MI0Q0G7AGURz) - Understanding computer architecture
- [Nand2Tetris](https://www.nand2tetris.org/) - From logic gates to OS

### Interactive Resources
- [PintOS](https://web.stanford.edu/class/cs140/) - Another teaching OS
- [JOS](https://pdos.csail.mit.edu/6.828/) - MIT's other teaching OS
- [Writing a Simple Operating System](https://www.cs.bham.ac.uk/~exr/lectures/opsys/10_11/lectures/os-dev.pdf) - From scratch guide

## Development Tools

### Required Tools
- **QEMU** - x86/RISC-V emulator
  - [QEMU Documentation](https://www.qemu.org/documentation/)
  - Install: `sudo apt install qemu-system-x86` or `qemu-system-riscv64`

- **GDB** - GNU Debugger
  - [GDB Documentation](https://sourceware.org/gdb/documentation/)
  - Install: `sudo apt install gdb-multiarch`

- **GCC** - GNU Compiler Collection
  - Need RISC-V cross-compiler for RISC-V labs
  - Install: `sudo apt install gcc-riscv64-linux-gnu`

- **Make** - Build automation
  - Included in most Linux distributions

### Useful Tools
- **valgrind** - Memory debugging
- **strace** - System call tracing
- **objdump** - Object file inspection
- **nm** - Symbol table display
- **readelf** - ELF file analysis

### IDE/Editor Setup
- **VS Code** with extensions:
  - C/C++ Extension
  - x86 and x86_64 Assembly
  - Hex Editor
- **Emacs** with GUD (built-in GDB frontend)
- **Vim** with termdebug plugin

## Debugging Resources

### GDB Commands Reference
```bash
# Start GDB with QEMU
(gdb) target remote localhost:26000

# Breakpoints
(gdb) break kernelmain
(gdb) break *0x80000000
(gdb) break file.c:42

# Execution
(gdb) continue
(gdb) step
(gdb) next
(gdb) finish

# Inspection
(gdb) info registers
(gdb) info break
(gdb) info threads
(gdb) print variable
(gdb) x/10x $sp

# Memory
(gdb) x/10i $pc
(gdb) x/20x 0x80000000

# Page Tables (if available)
(gdb) monitor info pg
```

### Common Debugging Scenarios
1. **Kernel Panic** - Check backtrace, examine stack
2. **Hang** - Break at scheduler, check process states
3. **Page Fault** - Check trap frame, verify page tables
4. **Data Corruption** - Use watchpoints, check races
5. **Deadlock** - Check lock ordering, examine wait channels

## Related Courses

### MIT Courses
- **6.004** - Computation Structures (prerequisite)
- **6.172** - Performance Engineering of Software Systems
- **6.824** - Distributed Systems
- **6.033** - Computer System Engineering

### Other Universities
- **Berkeley CS162** - Operating Systems
- **Stanford CS140** - Operating Systems
- **Carnegie Mellon 15-213** - Introduction to Computer Systems
- **Georgia Tech CS 3210** - Operating Systems Design

## Community and Discussion

### Forums
- [Piazza](https://piazza.com/) - Course discussion (private)
- [Stack Overflow](https://stackoverflow.com/) - Q&A for specific issues
- [Reddit r/osdev](https://www.reddit.com/r/osdev/) - OS development community
- [OSDev.org Forum](https://forum.osdev.org/) - Dedicated OS dev forum

### GitHub Repositories
- [mit-pdos/xv6-riscv](https://github.com/mit-pdos/xv6-riscv) - Official xv6
- [mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public) - x86 xv6
- Various student forks with lab solutions (academic integrity warning!)

## Papers and Articles

### Classic Papers
- "The Unix Time-Sharing System" by Ritchie and Thompson
- "UNIX Implementation" by Ken Thompson
- "The Design of the Unix Operating System" by Bach
- "On the Duality of Operating System Structures" by Liedtke

### Modern References
- "The Linux Kernel Module Programming Guide"
- "What Every Programmer Should Know About Memory" by Ulrich Drepper
- "Algorithms for Modern Hardware" (optimization techniques)

## Tips for Using Resources

1. **Start with xv6 book** - It's written specifically for this course
2. **Watch lectures after reading** - Reinforce concepts
3. **Use GDB actively** - Don't guess, verify
4. **Read source code** - xv6 is small and readable
5. **Build incrementally** - Test each change
6. **Ask for help early** - Piazza, office hours
7. **Form study groups** - Explain concepts to each other
8. **Review prerequisites** - C, assembly, computer architecture
9. **Take breaks** - Kernel debugging is mentally demanding
10. **Have fun** - Building an OS is rewarding!
