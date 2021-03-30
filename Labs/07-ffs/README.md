# Lab 7: Latches and Flip-flops
## Preparation tasks (done before the lab at home)

   | **D** | **Qn** | **Q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-- |
   | 0 | 0 | 0 | No change |
   | 0 | 1 | 0 | Change |
   | 1 | 1 | 1 | No change |
   | 1 | 0 | 1 | Change |

   | **J** | **K** | **Qn** | **Q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | 0 | 0 | 0 | 0 | No change |
   | 0 | 0 | 1 | 1 | No change |
   | 0 | 1 | 0 | 0 | Reset |
   | 0 | 1 | 1 | 0 | Reset |
   | 1 | 0 | 0 | 1 | Set |
   | 1 | 0 | 1 | 1 | Set |
   | 1 | 1 | 0 | 1 | Toggle |
   | 1 | 1 | 1 | 0 | Toggle |

   | **T** | **Qn** | **Q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-- |
   | 0 | 0 | 0 | No change |
   | 0 | 1 | 1 | No change |
   | 1 | 0 | 1 | Toggle |
   | 1 | 1 | 0 | Toggle |
## 2) D latch
### Process
```vhdl
    p_d_latch : process(d, arst, en)
    begin
        if (arst = '1') then
            q     <= '0';
            q_bar <= '1';
        elsif (en = '1') then
            q    <= d;
        end if;
    end process p_d_latch;
```
### Reset
```vhdl
    p_reset_gen :process
    begin
        s_arst <= '0';
        wait for 50ns;
        
        s_arst <= '1';
        wait for 10ns;
        
        s_arst <= '0';
        wait for 108ns;
        
        s_arst <= '1';
        
        wait;
    end process p_reset_gen;
```
### stimulus
```vhdl
    p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_en    <= '0';
        s_d     <= '0';
        assert (s_en = '0' and s_d = '0') report "Failed no. 1" severity note;
        
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        
        s_en <= '1';
        assert (s_en = '1') report "Failed no. 2" severity note;
        
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        
        s_en <= '0';
        assert (s_en = '0') report "Failed no. 3" severity note;
        
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        
        s_en <= '1';
        assert (s_en = '1') report "Failed no. 4" severity note;
        
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        s_d    <= '1';
        wait for 10 ns;
        s_d    <= '0';
        wait for 10 ns;
        
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```
![Waveform D-latch](img/1.PNG)
