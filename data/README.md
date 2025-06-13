# Data

This project analyzes human activity using permutation entropy and complexity measures.

## Processed Data:
- **processed_permutation_entropy_complexity.csv**: Contains calculated entropy and complexity values for different human activities
  - Activities analyzed: Walking, Running, Climbing Up, Climbing Down
  - Features: Permutation entropy and Jensen-Shannon complexity metrics
  - Used for identifying optimal parameters for activity discrimination

## Sample Data:
- **sample_accelerometer_data.csv**: Example raw accelerometer data for demonstration

## Analysis:
The processed data shows distinct patterns in entropy-complexity space for different activities,
enabling accurate classification with optimal parameters (Dimension=5, Delay=2 for walking/running).

## Source:
Accelerometer data from chest-mounted sensors analyzing human movement patterns.
