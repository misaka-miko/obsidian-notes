---
tags:
  - knowledge
category: computer architecture
topic: computer architecture
author: misaka
date: 2026-01-20
---
# Using bits to store things
**IDEA** : when we say *n bits* we are talking about to store $2^{n}$ stuff.

# How many bits to store *n* Items
In short, the answer is
$$
\text{\# bits used for stored items} = \lceil \log_{2} n\rceil 
$$

**Example** : how many bits do we need to store 26 letters(*not including the upper case letters*)
$$
\lceil \log_{2}26 \rceil  = 5
$$