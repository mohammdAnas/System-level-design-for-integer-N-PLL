# System-level-design-for-integer-N-PLL
A Python script developed to calculate PLL system dynamic parameters and size the passive filter components (R1, C1, C2), and computes the required Charge Pump current for optimal stability.
### NOTE
**This script is designed to provide a **very good starting point** based on ideal mathematical equations.**  
**you must take these calculated values into Cadence Virtuoso (or any simulator) and perform fine-tuning and optimization based on your deep understanding of PLL architecture**

## Features & Automation Workflow

1. **Dynamic Parameter Calculation**: Computes the natural frequency ($w_n$) and target crossover frequency ($w_c$) based on the specified lock time accuracy. 
   * *Note*: The **Damping Factor ($\zeta$)** is pre-defined and fixed at $1/\sqrt{2}$ ($\approx 0.707$) to ensure optimal loop stability.
     
2. **Filter Component Sizing**:  calculate the passive component values ($R_1$, $C_1$, and $C_2$) for the loop filter given a desired Phase Margin (PM).
   
4. **System Parameters**: Evaluates the Phase Margin peak and calculates the required Charge Pump Current ($I_{CHP}$) considering the VCO gain ($K_{VCO}$).
   
## How to Use (Step-by-Step)
The notebook is interactive and will prompt you to enter specific design parameters in the command line during execution (while keeping $\zeta$ optimized at $0.707$ automatically):  
  
1. Run the initial cells to define the reference frequency ($w_{ref}$) and target lock time constraints.  
2. The script will output a valid range for $w_c$. Enter your chosen value (in Mrad)   
3. Enter the required Phase Margin (PM): Input your target Phase Margin in degrees (e.g., 45, 50, 60)  
4. Enter Resistor Value ($R_1$): Input your chosen standard resistor value in kOhms   
5. Enter VCO Gain ($K_{VCO}$): Input your VCO gain specification in MHz/V The script will instantly output the calculated values for the loop filter components ($C_1$ and $C_2$ in pF) and the Charge Pump Current ($I_{CHP}$ in uA).  
