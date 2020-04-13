# Boolean logic

...

# Boolean function synthesis

Boolean function synthesis is going from a truth table to a boolean function.

1. take the table and go row by row
2. take only the rows where the function is 1
3. we have a bunch of expressions where the function is 1
4. we OR them together
5. the function is constructed

Example :

| x | y | z | f |
| - | - | - | - |
| 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |

* for the first row: `not(x) and not(y) and not(z)`
* for the third row: `not(x) and y and not(z)`
* for the fifth row: `x and not(y) and not(z)`

The function is then:
```
f(x,y,z) = (not(x) and not(y) and not(z)) or (not(x) and y and not(z)) or (x and not(y) and not(z))
```

## NAND

Thruth table:

| x | y | nand |
| - | - | ---- |
| 0 | 0 | 1    |
| 0 | 1 | 1    |
| 1 | 0 | 1    |
| 1 | 1 | 0    |

Any boolean function can be represented using just NAND.
For example: `nand(x, x) == not(x)`, or `and(x, y) == not(nand(x,y))`.


# Logic gates

We are going to implement bollean functions using logic gates. A composite logic gate is a gate made up from elementary logic gates.

Functionnal specification of the nand gate:

```vhdl
if (a == 1 and b ==1)
then out=0 else out1
```

A gate interface answers "what" the gate is doing, it's implementation answers the question "how". The interface of a gate is unique, it's implementation is not.

# Hardware description language

Example for the XOR gate:
```vhdl
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Not (in=a, out=nota);
    Not (in=b, out=notb);
    And (a=a, b=notb, out=aAndNotb);
    And (a=nota, b=b, out=notaAndb);
    Or (a=aAndNotb, b=notaAndb, out=out);
}
```

Week 1 gates:

* [x] Not
* [x] And
* [x] Or
* [x] Xor
* [x] Mux
* [ ] DMux
* [ ] Not16
* [ ] And16
* [ ] Or16
* [ ] Mux16
* [ ] Or8Way
* [ ] Mux4Way16
* [ ] Mux8Way16
* [ ] DMux4Way
* [ ] DMux8Way
