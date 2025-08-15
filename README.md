# Enhanced Automatic Washing Machine Controller (v2)

This project implements an **Enhanced Automatic Washing Machine Controller** in Verilog, along with a **comprehensive testbench** for functional verification. It models realistic washing machine operation, complete with wash cycles, temperature control, and safety/error handling.

---

## 🚀 Features

- **Three Wash Cycles**:  
  - Quick  
  - Normal  
  - Heavy (double rinse)

- **Water Temperature Control**:  
  - Cold  
  - Warm  
  - Hot

- **Pause/Resume Functionality** for mid-cycle interruptions.
- **Door-Open Error Detection** for safety.
- **Heavy Cycle Double Rinse** support.
- Simulation-ready with a detailed testbench.

---

## 📂 Repository Structure

- automatic_washing_machine_v2.v # Main washing machine controller
- tb_washing_machine_v2.v # Testbench for simulation


---

## ⚙️ Module Description

### **`automatic_washing_machine_v2`**

Implements a finite state machine (FSM) with the following states:

| State           | Description |
|-----------------|-------------|
| `IDLE`          | Waiting for start signal |
| `FILL_WATER`    | Opens water valves according to selected temperature |
| `ADD_DETERGENT` | Waits for detergent addition |
| `WASH_CYCLE`    | Runs motor until wash/rinse cycle timeout |
| `DRAIN_WATER`   | Drains water until empty |
| `SPIN_DRY`      | Spins clothes dry until timeout |
| `ERROR`         | Error mode triggered when door is opened mid-cycle |

---

## 🧪 Testbench Overview

The testbench (`tb_washing_machine_v2.v`) simulates multiple real-world scenarios:

1. **Normal Cycle, Warm Water**  
   - Standard single rinse wash process.

2. **Heavy Cycle, Hot Water**  
   - Extended wash time with **double rinse**.

3. **Error Scenario**  
   - Door opens mid-cycle, triggering error state and requiring reset.

The testbench uses `$monitor` and `$display` for real-time status and debugging.

---

## 🔧 How to Simulate

### Using **Icarus Verilog**
```bash
iverilog -o washing_machine_tb automatic_washing_machine_v2.v tb_washing_machine_v2.v
vvp washing_machine_tb
vlog automatic_washing_machine_v2.v tb_washing_machine_v2.v
vsim tb_washing_machine_v2
run -all
```

## Example Output

- [T=50] TEST 1: Normal cycle, warm water
- [T=500] Normal wash complete!
- [T=520] TEST 2: Heavy cycle, hot water
- [T=2500] Heavy wash complete!
- [T=2520] TEST 3: Door opens mid-cycle
- [T=2600] Machine in ERROR state, resetting
