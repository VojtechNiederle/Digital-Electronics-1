# Link na github
[link](https://github.com/VojtechNiederle/Digital-Electronics-1)
# Fabc
## Tabulka
| c | b | a | f(abc) |
| - | - | - | ------ |
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |
## Kod
[link](https://www.edaplayground.com/x/hwYq)
```vhdl
begin
    fabc_o  <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
    fANDabc_o  <= ( a_i nand ( b_i nand b_i ) )   nand ( ( b_i nand b_i ) nand (c_i nand c_i) );
    fORabc_o  <= ((((a_i nor a_i) nor b_i) nor (b_i nor c_i))   nor  (((a_i nor a_i) nor b_i) nor (b_i nor c_i)));
    --fand_o <= a_i and b_i;
    --fxor_o <= a_i xor b_i;
```
## Screen
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/Screenshot%202021-02-16%20220142.png)
