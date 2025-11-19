---
article: "[[dtmos_dt.pdf]]"
tags:
  - article_review
---
## Article Review

**DTUMOS (Digital Twin for Urban Mobility Operating System)** is an open-source, versatile framework designed to act as a **test bed and playground** for developing, testing, and quantitatively evaluating large-scale urban mobility systems, algorithms, and policies.

### Core Architecture and Key Performance Advantages

DTUMOS utilizes a **novel architecture** that integrates an **AI-based Estimated Time of Arrival (ETA) model** with a vehicle routing algorithm to ensure both **high-speed performance and accuracy** in implementing large-scale mobility systems.

Compared to existing state-of-the-art mobility simulations, DTUMOS demonstrates significant advantages in three key areas:

1. **Scalability:** DTUMOS expands scalability to the metropolitan level. It has been validated using real data in large cities including **Seoul, New York City, and Chicago**, successfully operating systems with more than 20,000 vehicles and over 100,000 passengers, a scale previously considered unachievable by existing digital twin platforms.
2. **Speed:** DTUMOS is **more than twice as fast** as the state-of-the-art model, Amodeus, with the speed difference becoming more pronounced as the system scale increases. The internal learning-based ETA model (which uses CatBoost) can compute a single sample **more than 100 times faster** than commercial Direction APIs (like Naver or Tmap) while maintaining similar accuracy.
3. **Extensibility and Visualization:** The framework's modular and open-source nature allows it to be easily applied to various mobility types, such as traditional taxi services, depot-based delivery, many-to-many pickup/delivery, and is capable of supporting visualization for urban air mobility (UAM). It utilizes the open-source **deck.gl** visualization framework to smoothly render the movement of large numbers of vehicles.

### Framework Components

The DTUMOS framework operates through four primary components:

1. **Data:** Includes foundational elements like road networks (using **OpenStreetMap**) and historical mobility data (e.g., taxi trip records).
2. **A.I. and Machine Learning Models:** Used to enhance precision. A deep learning-based **ETA model** is trained and applied to correct locations and travel times, significantly improving accuracy and simulation speed.
3. **Operate Mobility System:** This involves generating supply and demand, running the **dispatch algorithm** (an assignment problem, often solved using a greedy FIFO algorithm for maximum scalability), and calculating routes (using **OSRM**).
4. **Outputs:** Includes system performance reports (Level of Service, failed requests, waiting times) and simulation visualizations.

### Case Study and Policy Impact

DTUMOS was implemented to analyze the severe **late-night taxi shortage in the Seoul Metropolitan Area** following the COVID-19 pandemic. By simulating four scenarios based on late-night operations on April 8, 2022:

- The initial system (Scenario 1, 24,910 taxis) showed a **request failure rate of 76.78%** and a mean waiting time of 31 minutes.
- The simulation results provided quantitative evidence that the **supply must increase by approximately 50%** (to 37,365 taxis, Scenario 3) to stabilize the system, preventing the call queue from escalating and reducing the request failure rate to 1.13%.

This demonstrated DTUMOS's potential to provide quantitative guidelines and support for policy decisions. The study also positions DTUMOS as a crucial development linking **Mobility-as-a-Service (MaaS)** and **Digital-twin-as-a-service (DTaaS)**.