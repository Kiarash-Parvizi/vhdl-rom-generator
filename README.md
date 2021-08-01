# vhdl-rom-generator

## Usage
```
python3 generate_rom.py <inputfile> [optional: rom-addr-size]

example:
python3 generate_rom.py data/program1.hex 4
```

## rom_3_16 output:
```vhdl
library ieee ;
use ieee.std_logic_1164.all;
use ieee.numeric_Std.all; 

entity rom is
    port(
        address: in  std_logic_vector(2 downto 0);
        dataout: out std_logic_vector(15 downto 0)
    );
end entity;


architecture structural of rom is
constant d0: std_logic_vector(15 downto 0) := x"abcd";
constant d1: std_logic_vector(15 downto 0) := x"aaaa";
constant d2: std_logic_vector(15 downto 0) := x"cccc";
constant d3: std_logic_vector(15 downto 0) := x"dddd";
constant d4: std_logic_vector(15 downto 0) := x"eeee";
constant d5: std_logic_vector(15 downto 0) := x"0000";
constant d6: std_logic_vector(15 downto 0) := x"0000";
constant d7: std_logic_vector(15 downto 0) := x"0000";

type rom_array is array (natural range <>) of
    std_logic_vector(15 downto 0);

constant romBuf: rom_array := (d0,d1,d2,d3,d4,d5,d6,d7);
begin
    dataout <= romBuf(to_integer(unsigned(address)));
end architecture structural;
```

### Requirements
```
- python3
```

