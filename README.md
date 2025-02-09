# VHDL Counter: Race Condition or Asynchronous Assignment?

This repository demonstrates a potential issue in a VHDL counter implementation.  The code appears straightforward, but subtle timing issues can lead to unexpected behavior. The core problem lies in how the internal signal 'internal_count' is updated and assigned to the output signal 'count'.  Asynchronous signal assignment could cause a race condition, especially on fast clock rates.

The 'bug.vhdl' file contains the code exhibiting the potential problem.  The 'bugSolution.vhdl' file offers a revised version intended to solve the potential timing issue.

## Potential Issues:

* **Race condition:**  The assignment `count <= internal_count;` might not be synchronized with the clock edge.  If the clock edge arrives while the 'internal_count' signal is changing, the 'count' signal may show an inconsistent or incorrect value.
* **Asynchronous update:** The assignment is outside the clocked process, making it susceptible to asynchronous update issues.  

## Solution Approach:

The solution attempts to synchronize the output assignment with the clock edge, ensuring that 'count' reflects a consistent and accurate value.