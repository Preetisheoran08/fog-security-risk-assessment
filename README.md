MATLAB-Driven Cyber Risk Assessment Framework for Fog-Enabled Critical Infrastructure

A MATLAB-based simulation framework for evaluating cyberattacks on fog-enabled critical infrastructure through network clustering, communication modeling, QoS degradation analysis, and node-level risk assessment.

Overview

Fog computing extends computational and networking capabilities closer to end devices, making it suitable for latency-sensitive and distributed critical infrastructure applications.

However, the distributed nature of fog environments introduces additional cybersecurity risks. This project develops a MATLAB-based simulation framework to model a fog network, evaluate different clustering strategies, simulate cyberattack scenarios, measure their impact on network Quality of Service (QoS), and calculate node-level cybersecurity risk.

The framework simulates a 1,000-node fog network and evaluates how attacks affect network performance and individual node risk.

Objectives

The project focuses on:

Simulating a large-scale fog-enabled network

Establishing communication relationships between fog nodes

Comparing different clustering and cluster-head selection strategies

Simulating multiple cyberattack scenarios

Measuring network degradation using QoS metrics

Quantifying node-level cybersecurity risk

Identifying high-risk nodes through risk visualization

System Workflow

                 Fog Node Deployment
                         |
                         v
              Communication Graph
                         |
                         v
              Clustering & Cluster
              Head Selection
                         |
                         v
              Cyberattack Simulation
                         |
                         v
                  QoS Analysis
                         |
                         v
                Risk Assessment
                         |
                         v
                 Risk Map / High
                  Risk Nodes

Network Configuration

Parameter

Configuration

Fog Nodes

1,000

Simulation Area

100 × 100

Communication Range

8 units

K-Means Clusters

10

DoS-Affected Nodes

10%

Node Failure

5%

Targeted Cluster Heads

3

The nodes are randomly deployed within the simulation area. Communication links are established between nodes whose distance is within the configured communication range.

Clustering Strategies

The framework evaluates four approaches for cluster formation or cluster-head selection.

1. K-Means Clustering

K-Means is used to divide the fog nodes into 10 clusters.

For each cluster, the node closest to the cluster centroid is selected as the cluster head.

2. LEACH

LEACH-style probabilistic cluster-head selection is implemented using a configurable cluster-head probability.

3. Degree-Based Selection

Nodes are ranked according to their number of neighboring nodes. The nodes with the highest connectivity are selected as cluster heads.

4. Energy-Based Selection

Nodes are assigned simulated energy levels, and nodes with higher remaining energy are selected as cluster heads.

Communication Model

An adjacency matrix is constructed by calculating the Euclidean distance between fog nodes.

Two nodes are connected when their distance is within the configured communication range.

Node Coordinates
       |
       v
Distance Calculation
       |
       v
Communication Range Check
       |
       v
Adjacency Matrix
       |
       v
Network Graph

This allows the simulation to represent connectivity and node degree within the fog network.

Cyberattack Simulation

The framework evaluates three attack scenarios.

1. Denial-of-Service (DoS) Attack

Approximately 10% of the fog nodes are selected as DoS targets.

For affected nodes:

Throughput is reduced

Packet Delivery Ratio (PDR) is reduced

This models the degradation caused by resource-exhaustion or traffic-disruption attacks.

2. Node Failure

Approximately 5% of nodes are selected for complete failure.

For failed nodes:

Throughput becomes zero

Packet Delivery Ratio becomes zero

This represents complete loss of node availability.

3. Cluster Head Attack

Three selected cluster heads are targeted.

For attacked cluster heads:

Throughput is significantly reduced

Packet Delivery Ratio is significantly reduced

This models the impact of compromising critical coordination nodes within a clustered fog network.

Quality of Service Analysis

The framework evaluates the impact of attacks using network QoS metrics.

Metrics

Latency

Throughput

Packet Delivery Ratio (PDR)

The framework compares network conditions before and after attack injection.

              Before Attack
                    |
                    v
             Baseline QoS
                    |
                    |
              Attack Injection
                    |
                    v
              After Attack
                    |
                    v
             QoS Comparison

The resulting comparison is visualized to demonstrate network degradation caused by cyberattacks.

Risk Assessment Model

The framework calculates a risk score for every fog node using three components:

             Impact
                |
                |
        Vulnerability
                |
                |
            Likelihood
                |
                v
           Risk Score

The implemented risk model is:

Risk = Impact × Vulnerability × Likelihood

Impact

Impact represents the degradation in network performance caused by attacks.

It is derived from the change in throughput before and after attack conditions.

Vulnerability

Node vulnerability is calculated using:

Node degree

Remaining energy

The implementation combines normalized node connectivity with inverse normalized energy.

Likelihood

Likelihood is assigned according to the simulated attack scenario:

Attack

Likelihood

DoS

0.7

Node Failure

0.9

Cluster Head Attack

1.0

The resulting risk values are normalized to enable comparison across the network.

High-Risk Node Identification

After calculating risk scores for all nodes, nodes exceeding the configured risk threshold are identified as high-risk nodes.

The current implementation uses:

Risk > 0.6

These nodes are highlighted on the network risk map.

Low Risk  ────────────────>  High Risk

       Network Risk Map
              |
              v
       High-Risk Nodes
              |
              v
      Security Prioritization

Visualizations

The simulation generates visualizations for:

Fog Node Deployment

Displays the spatial distribution of the 1,000 fog nodes.

Communication Graph

Shows communication relationships between nodes based on the configured communication range.

Clustering

Visualizes the four clustering/cluster-head selection strategies.

QoS Degradation

Compares latency, throughput, and PDR before and after cyberattack scenarios.

Risk Map

Visualizes node-level risk across the simulated fog network and highlights high-risk nodes.

Project Structure

fog-security-risk-assessment/
│
├── README.md
│
├── src/
│   └── fog_simulation.m
│
├── docs/
│   ├── BLUEPRINT.md
│   ├── PLAYBOOK.md
│   └── PROJECT_REPORT.pdf
│
├── results/
│   ├── deployment.png
│   ├── communication.png
│   ├── clustering.png
│   ├── qos-degradation.png
│   └── risk-map.png
│
├── .gitignore
└── LICENSE

Implementation

The core simulation is implemented in MATLAB.

The main workflow includes:

Fog node deployment

Communication graph construction

K-Means clustering

LEACH cluster-head selection

Degree-based cluster-head selection

Energy-based cluster-head selection

Cyberattack injection

QoS evaluation

Risk calculation

High-risk node identification

Risk-map visualization

Getting Started

Prerequisites

MATLAB

MATLAB functions/toolboxes required by the implementation

Run the Simulation

Clone the repository.

Open MATLAB.

Navigate to the src directory.

Open:

fog_simulation.m

Run the script.

The simulation will generate the network, clustering, attack, QoS, and risk visualizations.

Output

Running the simulation produces visualizations including:

Fog Nodes Deployment
        ↓
Communication Graph
        ↓
Clustering Comparison
        ↓
Cyberattack QoS Degradation
        ↓
Network Risk Map

Key Findings

The framework enables comparison of clustering strategies based on network performance and resource-related characteristics.

The project evaluates trade-offs involving:

Throughput

Latency

Packet Delivery Ratio

Energy consumption

Network lifetime

The attack simulations demonstrate how targeted disruptions can degrade network performance and increase the risk associated with affected infrastructure nodes.

Documentation

Additional project documentation is available in the docs/ directory.

Blueprint

docs/BLUEPRINT.md

Describes the architecture, components, data flow, and simulation pipeline.

Playbook

docs/PLAYBOOK.md

Provides instructions for configuring and running the simulation.

Project Report

docs/PROJECT_REPORT.pdf

Contains the detailed academic methodology, analysis, experiments, and results.

Technologies

MATLAB
Fog Computing
Cybersecurity
Network Simulation
Clustering
Risk Assessment
QoS Analysis
Graph Modeling

Future Improvements

Potential extensions include:

Adding additional cyberattack models

Introducing dynamic attack probabilities

Using more realistic network traffic models

Incorporating real-world fog/IoT datasets

Implementing adaptive cluster-head selection

Adding automated attack detection

Integrating machine-learning-based risk prediction

Extending the framework toward real-time monitoring

Evaluating additional security mitigation strategies

Author

Preeti Sheoran

Computer Science Engineering — Cyber Security

Project Context

This project explores the intersection of:

Fog Computing + Critical Infrastructure + Cybersecurity + Network Simulation + Quantitative Risk Assessment

The framework is designed to help analyze how cyberattacks affect distributed fog infrastructure and identify nodes requiring higher security attention.
