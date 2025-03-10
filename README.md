# Net Sentry

## Project Overview

This project implements an intelligent anomaly detection system specifically designed to identify and alert administrators to Distributed Denial of Service (DDOS) attacks in real-time. The pipeline captures network traffic data, processes it through sophisticated machine learning algorithms, and provides actionable insights and alerts to network security teams.

## System Architecture

The system follows a modular architecture with the following components:

1. **Network Traffic Capture Module**
   - Leverages Wireshark/TShark for comprehensive packet capture
   - Configurable to target specific network interfaces or traffic patterns
   - Optimized for high-throughput environments with minimal performance impact

2. **Data Processing Engine**
   - Pre-processes raw packet data for analysis
   - Extracts critical network features and metrics
   - Aggregates traffic patterns at multiple time intervals (5s, 30s, 1m, 5m)
   - Implements stateful tracking of connection patterns

3. **Feature Engineering Pipeline**
   - Calculates statistical metrics on network flows (entropy, variance, etc.)
   - Identifies protocol-specific anomalies and patterns
   - Generates temporal features to capture traffic evolution
   - Creates graph-based features representing connection relationships

4. **Anomaly Detection Core**
   - Employs a multi-model approach combining:
     - Statistical outlier detection for rapid response
     - Machine learning models (Isolation Forest, One-Class SVM) for pattern recognition
     - Optional deep learning models for complex attack pattern identification
   - Maintains baseline models of "normal" network behavior
   - Adapts to evolving network traffic patterns over time

5. **Alert & Visualization System**
   - Real-time dashboard displaying network health and anomaly scores
   - Configurable alerting thresholds with tiered severity levels
   - Attack classification to distinguish between different DDOS types (SYN flood, UDP flood, etc.)
   - Historical data visualization for post-incident analysis

6. **Response Integration Framework**
   - API endpoints for integration with existing security infrastructure
   - Automated response rule configuration
   - Detailed attack forensics data export

## Technical Implementation

The core pipeline is implemented in Python, utilizing a combination of specialized libraries:

- **Traffic Processing**: Built on pyshark/scapy for Python-based packet analysis
- **Data Manipulation**: Pandas and NumPy for efficient data transformation
- **Machine Learning**: Scikit-learn for traditional ML models and PyTorch components for advanced models
- **Orchestration**: Apache Airflow for workflow management
- **Storage**: Time-series databases for efficient storage and retrieval of network metrics
- **Visualization**: Grafana dashboards with real-time monitoring capabilities

## Key Features & Benefits

- **Low False Positive Rate**: Multi-model approach reduces false alarms while maintaining sensitivity
- **Scalability**: Distributed processing architecture handles enterprise-level traffic volumes
- **Adaptability**: Self-adjusting baselines accommodate changing network patterns
- **Explainability**: Detailed attack characterization assists in remediation efforts
- **Historical Analysis**: Comprehensive logging enables post-incident investigation
- **Easy Integration**: Standardized interfaces connect with existing security tools

## Deployment Requirements

- Linux-based environment (Ubuntu 20.04 LTS or later recommended)
- Python 3.8+ runtime environment
- Network interfaces with promiscuous mode access
- Sufficient storage for historical traffic analysis
- Administrative privileges for packet capture

## Future Enhancements

- Integration with threat intelligence feeds
- Behavioral analysis of individual network entities
- Advanced fingerprinting of attack sources
- Reinforcement learning for adaptive defense mechanisms
