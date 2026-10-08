# EDSA Busway Dispatch Simulation

This is a group project I worked on for Computer Simulation and Modeling at Ateneo de Manila University. We used Python and Mesa to explore how different bus dispatch rules affect passenger queues and waiting times on the EDSA Busway.

The notebook contains the data preparation, model, experiments, and saved tables and plots. You can [open the notebook](<EDSA Busway Dispatch Simulation Final Code.ipynb>) to view the code and saved outputs without running it.

## What we compared

The model compares four dispatch strategies:
a
- **Fixed interval:** dispatch buses at a set interval
- **Headway control:** maintain a minimum gap between dispatches when passengers are waiting
- **Queue-dependent:** dispatch based on queue size, with additional minimum-gap rules
- **Random interval:** use sampled dispatch gaps to approximate irregular service

Passengers join a queue, wait for a bus, and leave the queue if they exceed the waiting-time threshold. Bus agents board passengers subject to capacity and loading-rate settings.

The comparisons track average waiting time among served passengers, queue length, passengers served, passenger abandonment, dispatch headways, and bunching events. The main experiment runs for 120 simulated minutes.

## Data and tools

The notebook uses bus GPS and passenger records to prepare arrival patterns and identify stops. It uses **Python, Mesa, Pandas, NumPy, and Matplotlib**, and was written for Google Colab.

The CSV inputs are not included in this repository. The data-loading cells expect these columns:

```text
timestamp, Speed, latitude, longitude, Board, Alight, Numpass
```

## Running the notebook

1. Download `EDSA Busway Dispatch Simulation Final Code.ipynb` and open it in Google Colab.
2. Run the first cell to install Mesa. Pandas, NumPy, and Matplotlib must also be available in the environment.
3. Run the file-upload cell and provide the original CSV inputs, or compatible data with the required columns. The notebook uses the first six uploaded filenames to select its training inputs.
4. Run the remaining cells in order to prepare the data, build the model, and generate the comparisons.

Without the CSV inputs, you can still review the saved outputs, but you cannot reproduce the data-dependent cells. The notebook does not pin the package versions used in the original work, so a newer environment may require adjustments.

## Notes on the results

The experiment focuses on the queue at station index 0. It does not establish performance across the full EDSA Busway route.

The random dispatch strategy uses sampled intervals rather than a replay of measured dispatch times. Some parameters, including the service rate, were set as modeling assumptions.

Average waiting time is calculated for passengers who were served. Passengers who left the queue are counted separately, so lower average waiting time should be considered together with abandonment and service counts.

The saved results come from the original runs. Randomness and parameter changes can affect the comparisons, and the notebook's exploratory demand and repeated-run experiments need further validation before drawing general conclusions.

**Project team:** Cabangunay, Cayabyab, Pequieras, and Trestiza  
**Course:** CSCI 115, Computer Simulation and Modeling, Ateneo de Manila University
