# Human Activity Monitoring Using Permutation Entropy

<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1400/1*Zy0V3xBNGP5LtkBcnXAuOQ.png" width="80%" alt="Human activity monitoring with accelerometer signals"/>
  <p><em>Example of accelerometer signals during different human activities</em></p>
</div>

## Overview

This repository contains code for analyzing human activity monitoring data using permutation entropy and complexity measures. The project explores how information-theoretic metrics can distinguish between different physical activities (walking, running, climbing up, climbing down) based on accelerometer data.

<div align="center">
  <img src="parameter_space_analysis.png" width="70%" alt="Parameter space analysis showing F-statistics"/>
  <p><em>Activity discrimination across different parameter combinations</em></p>
</div>

## Background

Permutation entropy (PE) is a measure that quantifies the unpredictability and complexity of time series data. Unlike traditional analysis methods like Fourier transforms, PE can effectively capture the nuanced patterns in complex, non-linear signals such as human movement.

<div align="center">
  <img src="https://www.researchgate.net/profile/Javier-Escudero-2/publication/325757493/figure/fig1/AS:639800505237506@1529538849651/Flowchart-of-the-permutation-entropy-calculation-a-An-example-time-series-x-t-is.png" width="60%" alt="Permutation entropy calculation example"/>
  <p><em>Permutation entropy calculation process</em></p>
</div>

When paired with statistical complexity measures, PE provides a powerful framework for characterizing different types of physical activities.

## Dataset

The analysis uses a comprehensive dataset of accelerometer recordings from 15 subjects performing four different activities:
- 🚶 **Walking** (structured, rhythmic movement)
- 🏃 **Running** (faster, more dynamic motion)
- 🧗‍♀️ **Climbing up** (vertical motion against gravity)
- 🧗‍♂️ **Climbing down** (controlled descent with gravity)

Each activity was measured along three axes (X, Y, Z), with data processed using various parameter combinations:
- 4 embedding dimensions (3, 4, 5, and 6)
- 3 time delays (1, 2, and 3)
- 3 signal lengths (1024, 2048, and 4096 samples)

This approach generated 6,480 data points for analysis.

<div align="center">
  <img src="pe_vs_complexity_visualization.png" width="75%" alt="PE vs Complexity visualization"/>
  <p><em>Permutation Entropy vs. Statistical Complexity for different activities</em></p>
</div>

## Key Findings

1. **Parameter Sensitivity**: Standard parameters (dimension=3, delay=1) show minimal differentiation between activities:

<div align="center">
  <img src="activity_comparison_basic.png" width="75%" alt="Activity comparison with basic parameters"/>
  <p><em>Activity comparison with standard parameters (dim=3, delay=1)</em></p>
</div>

2. **Axis Specificity**: Different activities express distinctive signatures along specific axes:

<div align="center">
  <img src="axis_comparison.png" width="85%" alt="Activity analysis by axis"/>
  <p><em>Permutation entropy by axis for each activity</em></p>
</div>

![Activity patterns showing distinct clusters for different physical movements](images/entropy_complexity_plot.png)

*Figure 1: Distinct clustering of human activities in the entropy-complexity feature space, demonstrating clear separation between different movement types with optimal parameter selection.*

3. **Optimized Discrimination**: Higher dimensions with appropriate delays reveal significant differences:

<div align="center">
  <img src="optimal_parameters_comparison.png" width="75%" alt="Activity discrimination with optimal parameters"/>
  <p><em>PE vs. Complexity with optimized parameters showing improved discrimination</em></p>
</div>

4. **Multi-dimensional Analysis**: The 3D parameter space reveals activity-specific patterns:

<div align="center">
  <img src="3d_parameter_space.png" width="70%" alt="3D visualization of parameter space"/>
  <p><em>3D visualization of activities across the parameter space</em></p>
</div>
## Parameter Optimization

To identify the ideal parameters for activity discrimination, I conducted a systematic analysis of different dimension and delay combinations, calculating F-statistics to measure separation power:

<div align="center">
  <img src="images/parameter_heatmap.png" width="70%" alt="Parameter optimization heatmap"/>
  <p><em>F-statistic values for different parameter combinations showing optimal settings for activity discrimination</em></p>
</div>

Higher F-statistic values (darker colors) indicate better discrimination between activities, with the optimal combination found at Dimension=5, Delay=3.

## Repository Contents

- `human_activity_analysis.py`: Main analysis script
- `results/`: Directory containing analysis results and summary reports
- `*.png`: Visualization files showing different aspects of the analysis

## How to Use

1. Clone the repository:
```bash
git clone https://github.com/yourusername/human-activity-monitoring.git
cd human-activity-monitoring
```

2. Ensure you have the required dependencies:
```bash
pip install pandas numpy matplotlib seaborn scipy
```

3. Run the analysis script:
```bash
python human_activity_analysis.py
```

4. Review the results in the `results/` directory and the visualization files.

## Data Analysis Pipeline

<div align="center">
  <img src="https://mermaid.ink/img/pako:eNp1ksFuwjAMhl_F8qnd9gCVOFQMCdAE6jStqJcqdeygkTRREpi2iscZD7QXmZOAGDsxx_z-7c-Ok4JJaYAGVJB7Ew0tRBrOMbYvYDM2FulLQOPM2K4pUqurGVmh1KDVfQbOcLVQQk6_d6CBVD6JJ--3TnNpfnwZIGqtPTXXPBe0FDPWkq90Aw_njHCDc14JbvNcTElk-Yj25Uqy4r0s_GfRZtIkXGLZLPrCgpJ3y6hUbnZ6X-a8zpjY9VQPQdjWX3X48yfWoR8eaeCVtl_2tXXoBrFTAedbWOBGkxzDrAM90FiDZdC9yyZnkhY0IGGTL1AWTi5TGlDpHKiOhq0GKTi9cAaTbkprcILpJKCuD6P7kbvoJQ-oPV86mwrh_xbIQfzX0qf7wPFgZF86UGk_Pmi9UrGPxcOC8oDKPowfR6OvJ5oOu_QIiJxZNg?type=png" width="85%" alt="Data analysis pipeline"/>
  <p><em>Permutation entropy analysis workflow</em></p>
</div>

## Applications

This research has potential applications in:

- Wearable fitness and health monitoring devices
- Clinical assessment of movement disorders
- Sports science and athletic performance monitoring
- Personalized activity recognition systems

<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1400/1*rGJ_JjvPdJpYjOzGi732_g.png" width="70%" alt="Applications of activity monitoring"/>
  <p><em>Applications of human activity monitoring in healthcare and fitness</em></p>
</div>

## Future Directions

Potential extensions of this work include:

- Personalized analytics for individual activity profiles
- Analysis of transitional states between activities
- Applications in detecting abnormal movement patterns
- Real-time implementation for continuous monitoring

## License

[MIT License](LICENSE)

## Citation

If you use this code or find the analysis helpful in your research, please cite:

```
Torres, R. (2025). Human Activity Monitoring Using Permutation Entropy.
GitHub Repository: https://github.com/yourusername/human-activity-monitoring
```

## Contact

For questions or collaborations, please contact:
- Email: torres.ros@northeastern.edu
- GitHub: [@yourusername](https://github.com/rosalinatorres888)
