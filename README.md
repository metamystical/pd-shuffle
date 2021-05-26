## pd-shuffle
Improved [shuffle ] object for [Pure Data](https://github.com/pure-data/pure-data) - a free real-time computer music system. 

### Overview

This is a drop-in replacement for the object of the same name in the [Motex library](https://puredata.info/downloads/motex) by Iain Mott, which can crash and uses an inefficient shuffle algorithm. It is rewritten from scratch using proper memory allocation and the Fisher–Yates shuffle algorithm.

### Description

[shuffle ] outputs all of the integers in a specified range in random order without repeating any, then reshuffles. Inputs are described in the following table. All selectors can be sent as messages to the left input with arguments as specified:

| Selector     | Input  | Message argument | Effect                               |
|--------------|--------|------------------|---------------------------------------|
| **bang**     | left   | none  | output next integer in the series |
| **lower**    | left   | float (truncated to integer) | update lower bound of range, trigger reset/reshuffle |
| **upper**    | middle | float (truncated to integer) | update upper bound of range |
| **fraction** | right  | float | update **fraction** (0 <= **fraction** <= 0.5) - if nonzero, ensures that the last fraction of the series is not repeated at the beginning of the next series |

Note: **upper** and **fraction** inputs do not take full effect until **lower** is input and a reset/reshuffle is triggered.

### Installation

The shuffle.c file can be compiled into a Pure Data external using [pure-data/pd-lib-builder](https://github.com/pure-data/pd-lib-builder). Simply place the linked file (e.g. shuffle.pd_linux) along with the help patch shuffle-help.pd into the same directory as your patch, or somewhere on the Pd search path (e.g., externals/shuffle folder).
