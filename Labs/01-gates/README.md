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
entity gates is
    port(
        a_i    : in  std_logic;         -- Data input
        b_i    : in  std_logic;         -- Data input
        c_i    : in  std_logic;         -- Data input
        fabc_o  : out std_logic;
        fANDabc_o  : out std_logic;
        fORabc_o  : out std_logic      -- OR output function
        --fand_o : out std_logic;         -- AND output function
        --fxor_o : out std_logic          -- XOR output function
    );
end entity gates;

------------------------------------------------------------------------
-- Architecture body for basic gates
------------------------------------------------------------------------
architecture dataflow of gates is
begin
    fabc_o  <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
    fANDabc_o  <= ( a_i nand ( b_i nand b_i ) )   nand ( ( b_i nand b_i ) nand (c_i nand c_i) );
    fORabc_o  <= ((((a_i nor a_i) nor b_i) nor (b_i nor c_i))   nor  (((a_i nor a_i) nor b_i) nor (b_i nor c_i)));
    --fand_o <= a_i and b_i;
    --fxor_o <= a_i xor b_i;

end architecture dataflow;
```
## Screen
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/Screenshot%202021-02-16%20220142.png)
# Experiment your own
## Boolean postulates
```
Výstupy vyšly dle očekávání
```
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/ad1.png)
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/1.png)
```vhdl
entity gates is
    port(
        x_i    : in  std_logic;         -- Data input
        y_i    : in  std_logic;         -- Data input
        z_i    : in  std_logic;         -- Data input        -- AND output function
        f11_o : out std_logic;
        f12_o : out std_logic;
        f13_o : out std_logic;
        f14_o : out std_logic-- XOR output function
    );
end entity gates;

------------------------------------------------------------------------
-- Architecture body for basic gates
------------------------------------------------------------------------
architecture dataflow of gates is
begin
   
    f11_o <= x_i and (not x_i);
    f12_o <= x_i or (not x_i);
    f13_o <= x_i or x_i or x_i;
    f14_o <= x_i and x_i and x_i;

end architecture dataflow;

```
[link](https://www.edaplayground.com/x/ejxx)
## Distributive Laws
```
Výstupy vyšly dle očekávání, F21 = F22 a F23 = F24
```
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/ad2.png)
![alt text](https://github.com/VojtechNiederle/Digital-Electronics-1/blob/main/Labs/01-gates/images/2.png)
```vhd1
entity gates is
    port(
        x_i    : in  std_logic;         -- Data input
        y_i    : in  std_logic;         -- Data input
        z_i    : in  std_logic;         -- Data input        -- AND output function
        f21_o : out std_logic;
        f22_o : out std_logic;
        f23_o : out std_logic;
        f24_o : out std_logic      -- XOR output function
    );
end entity gates;

------------------------------------------------------------------------
-- Architecture body for basic gates
------------------------------------------------------------------------
architecture dataflow of gates is
begin
   
    f21_o <= (x_i and y_i) or (x_i and z_i);
    f22_o <= x_i and (y_i or z_i);
    f23_o <= (x_i or y_i) and (x_i or z_i);
    f24_o <= x_i or (y_i and z_i);

end architecture dataflow;
```
[link](https://www.edaplayground.com/x/rbve)


