### Reference
All the instruction links and one of the footnotes come from this [ARM Cortex-M0 User Guide](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABIHJGA.html).

### Interpretation assignment
| Label | Instruction | Intepretation |
| --- | --- | --- |
| negate: | | _Label (corresponds to the address of the first following instruction)_ |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` | Subtact 8 from the stack pointer (and store into the stack pointer) |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r0, [sp, #4]`<sup>[1](#footnotes)</sup> | Write (the contents of) r0 to the memory with address sp + 4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load (the contents of) r3 from the memory with address sp + 4 |
| | [rsbs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)    `r3, r3, #0` | Substracts the value of r3 from 0 and potentially reverses the sign, and then updates the value of the register to the new value |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write value of r3 to r0 |
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` | Add 8 to the stack pointer and store the result in the stock pointer |
| | [bx](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `lr` | Return from function call to link-register |
| | | |
| main: | | _Label (corresponds to the address of the first following instruction)_ |
| | [push](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)    `{lr}` | Push the link-register onto the stack |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | Subtract 12 from the stack pointer and store it in the stack pointer |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #6` | Write the value of 6 onto r3 |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Write (the contents of) r3 to the memory with address sp + 4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load (the contents of) r3 from the memory with address sp + 4 |
| | [cmp](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIHIEI.html)     `r3, #0` | Subtracts 0 from r3 but discards the results |
| | [ble](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)<sup>[2](#footnotes)</sup>     `.L4` | Branch to less than or equal to the label, .L4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Load (the contents of) r3 from the memory with address sp + 4 |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write (the contents of) r3 to r0 |
| | [bl](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `negate` | Branch with Link to the label, Negate |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, r0` | Write (the contents of) r0 to r3 |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | Write (the contents of) r3 to the memory with address sp + 4 |
| | | |
| .L4: | | _Label (corresponds to the address of the first following instruction)_ |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #0` | Write 0 to r3 |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | Write (the contents of) r3 to r0 |
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | Add 12 to the stack pointer and store into the stack pointer |
| | [pop](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)     `{pc}` | Pop pc from the stack |

### Footnotes

**1** _[Addressing modes](http://www.davespace.co.uk/arm/introduction-to-arm/addressing.html)_ 

**2** _[Conditional execution](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABEHFEF.html)_ 
