# Urban Parking Management: Agent-Based Simulation (ABM)

> An Agent-Based Model (ABM) developed in Python using the MESA framework to solve the Parking Allocation Problem by simulating interactions between drivers and parking infrastructure. This project evaluates different management strategies (FCFS, Reservations, Dynamic Pricing) to optimize occupancy rates, queue times, and revenue[cite: 8, 9].

![Simulation Dashboard](docs/videos/ReservationModeVideoShortened.mp4)

## Project Overview
- **The Problem:** Scarcity of parking resources in highly populated cities combined with the stochastic nature of driver behavior leads to severe congestion.
- **The Solution:** A Discrete-Event Simulation (DES) on a rectangular grid that tests three allocation policies to balance revenue generation with minimized wait times. 

## My Role & Contributions
Developed collaboratively with Marcos Costa and Rodrigo Moucho, my contributions to the engineering of the simulation included:
- **Agent State Machines:** Implemented the Finite State Machine (FSM) for driver agents, managing 8 distinct states from `ARRIVING` and `WAITING_AT_GATE` to `PARKED` and `EXITING`.
- **Stochastic Demand Modeling:** Engineered the arrival logic using a Poisson distribution for peak/low hours[cite: 11, 16] and modeled driver "Willingness to Pay" (WTP) using a Log-Normal distribution.
- **Dynamic Pricing Engine:** Built the supply-and-demand pricing model where the parking rate dynamically adjusts based on the current occupancy ratio.
- **Live KPI Dashboard:** Designed the real-time visualization server and custom CSS KPI panel tracking revenue, queue lengths, and idle reserved spaces at each simulation step.

## Allocation Strategies Evaluated
1. **Baseline (FCFS):** Standard First Come First Serve model with a fixed pricing rate where drivers balk if the queue exceeds their patience.
2. **Reservation-Based:** Introduces VIP spots and secondary entry lanes, modeling real-world constraints like "no-show" probabilities and idle hold times.
3. **Dynamic Pricing:** Implements a linear surge function based on real-time occupancy; drivers only enter if their stochastic Willingness to Pay exceeds the current rate.

##  Tech Stack
- **Simulation Framework:** Python 3.10+, Mesa 2.3.2
- **Data & Math:** Pandas, NumPy, Uniform/Log-Normal Statistical Distributions
- **Visualization:** Matplotlib, HTML/CSS (Mesa Custom UI components)
  
##  Quickstart

### Prerequisites
Install the required dependencies from `requirements.txt`:
\`\`\`bash
pip install -r requirements.txt
\`\`\`

### Running the Server
Launch the visualization server locally:
\`\`\`bash
python run.py
\`\`\`
* Navigate to the local host address provided in the terminal.
* Use the UI dropdown in `server.py` to toggle between `"Standard"`, `"Dynamic Pricing"`, and `"Reservations"` strategies.
* Click **Start** to run the 1000-step simulation (representing 16 hours of real-world time).

## 📄 Documentation
- [Project Report (PDF)](docs/ReportDelivery_EIC2_12.pdf)
- [Presentation Slide Deck](docs/)
