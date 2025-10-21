---
tags:
  - knowledge
  - CA
---
So how to use count numbers **MATTERS**, we will talk about base conversions about:
- decimal
- hexadecimal
- binary

# From *Binary* to *Decimal* 
to figure out how to convert other base to decimal, we should first know how to base **works**

| $B^{n}$ | ... | $B^{2}$ | $B^{1}$ | $B^{0}$ |
| ------- | --- | ------- | ------- | ------- |
| $x^{n}$ | ... | $x^{2}$ | $x^{1}$ | $x^{0}$ |
**Example** : convert $0b 1101$ to decimal
$$
1 \times 2^{3} + 1 \times 2^{2} + 0 \times 2^{1} + 1 \times 2^{0}
$$

# From *Hexadecimal* to *Decimal* 
This works similarly
**Example** : convert $0x A5$ to decimal
$$
10 \times 16^{1} + 5 \times 16^{0} = 165
$$

# From *Decimal* to *Binary* / *Hexadecimal*
using the **Amazon Box** algorithm
**Example** : convert 13 to binary
imagine you have four boxes which can respectively hold $8$, $4$, $2$, $1$ items, you have to fill up the box to mark it as **1**.
1. 8: fill up, mark as 1, $13 - 8 = 5$
2. 4: fill up, mark as 1, $5 - 4 = 1$
3. 2: can't fill up, mark as 0
4. 1: fill up, mark as 1, $1-1=0$
5. get $0b 1101$

converting to *hexadecimal* works similarly.