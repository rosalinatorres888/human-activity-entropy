# Human Activity Monitoring Using Permutation Entropy and Complexity


### Author
**Rosalina Torres**  
Northeastern University  
IE6400 – Data Analytics Engineering  
Spring 2025  
Contact: torres.ros@northeastern.edu
🔗 [LinkedIn](#) | [GitHub](#)


### Project Overview
This project analyzes accelerometer data from human activities (walking, running, climbing up, climbing down) using permutation entropy and complexity metrics. By identifying optimal parameters for distinguishing between different physical activities, this work contributes to the rapidly growing field of human activity recognition, which has critical applications across healthcare, fitness, industrial safety, and smart environments.

## Dataset
The dataset contains accelerometer readings from 15 subjects performing four activities:
- Walking
- Running
- Climbing up
- Climbing down

Data was collected from chest-mounted sensors, capturing acceleration in the x, y, and z axes.

### Project Tasks

### Task 1: Load the Required Data
- Loading accelerometer data for all subjects and activities
- Processing and organizing the data for analysis

### Task 2: Compute Permutation Entropy and Complexity
Computing permutation entropy and complexity for various parameter combinations:
- Embedded Dimensions: 3, 4, 5, 6
- Embedded Delays: 1, 2, 3
- Signal Lengths: 1024, 2048, 4096

The calculations were performed for all subjects, activities, and accelerometer axes, resulting in 6480 rows of data.

### Task 3: Filter Data for a Specific Subject, Axis, and Signal Length
Selected Subject 3, x-axis accelerometer data for detailed analysis.

### Task 4: Identify Optimal Parameters for Walking vs. Running
Created scatter plots to identify the optimal dimension and delay for distinguishing walking from running activities.

**Findings:**
- Walking: Lower permutation entropy (~0.75) and higher complexity (~0.22)
- Running: Higher permutation entropy (~0.88) and lower complexity (~0.13)
- **Optimal parameters:** Dimension=5, Delay=2

### Task 5: Identify Optimal Parameters for Climbing Up vs. Climbing Down
Created scatter plots to identify the optimal dimension and delay for distinguishing climbing up from climbing down.

**Findings:**
- Climbing Up: Higher permutation entropy (~0.83) and lower complexity (~0.17)
- Climbing Down: Lower permutation entropy (~0.79) and higher complexity (~0.20)
- **Optimal parameters:** Dimension=4, Delay=3

## Industry Applications

### Healthcare and Remote Patient Monitoring
- **Early Disease Detection**: Changes in gait patterns can indicate neurodegenerative conditions like Parkinson's disease
- **Rehabilitation Monitoring**: Track patient recovery progress through quantitative movement analysis
- **Fall Detection and Prevention**: Identify high-risk movement patterns in elderly patients
- **Medication Effectiveness**: Measure improvements in mobility after treatment interventions

### Fitness and Sports Performance
- **Athlete Training Optimization**: Detailed analysis of movement patterns to improve technique
- **Injury Prevention**: Detect fatigue or improper form before injuries occur
- **Personalized Fitness Programs**: Tailor exercise recommendations based on movement quality
- **Performance Metrics**: Provide quantitative feedback on movement efficiency and consistency

### Industrial Safety and Ergonomics
- **Workplace Safety**: Monitor workers in dangerous environments for signs of fatigue
- **Ergonomic Assessment**: Identify movement patterns that may lead to repetitive strain injuries
- **Training Verification**: Ensure proper technique is being used for safety-critical tasks
- **Productivity Enhancement**: Optimize movement patterns for efficiency while maintaining safety

### Smart Environments and IoT
- **Smart Homes**: Automatically adjust lighting, temperature, or security based on detected activities
- **Energy Efficiency**: Power management based on occupant activities
- **Ambient Assisted Living**: Support independent living for elderly or disabled individuals
- **Context-Aware Computing**: Enhance user experience by anticipating needs based on current activity

### Security and Authentication
- **Biometric Authentication**: Use unique movement patterns as a security feature
- **Behavioral Analysis**: Detect suspicious activities in secure environments
- **Continuous Authentication**: Verify user identity throughout system usage
- **Fraud Detection**: Identify unusual patterns of physical activity indicating unauthorized access

### Entertainment and Gaming
- **Motion-Based Gaming**: Create more responsive and immersive gaming experiences
- **Virtual Reality**: Improve motion tracking for realistic VR experiences
- **Extended Reality Applications**: Enhance user interaction in mixed reality environments
- **Gesture Recognition**: Enable more natural human-computer interaction
