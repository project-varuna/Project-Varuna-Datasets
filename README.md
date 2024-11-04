# Project-Varuna-Datasets

This repository provides pose, attitude, and control datasets formatted specifically for "Project-Varuna." These datasets can be used directly with the Project-Varuna GUI to create new data-driven models or perform path-tracking tasks with the 1:5 scale Ackermann-steered robot, **Hunter SE**.

### Dataset Branches

> **Note**  
> - To access the off-road dataset, switch to the [`Hunter-SE-Offroad-Dataset`](https://github.com/Tinker-Twins/AutoDRIVE-Hunter-SE-Dataset/tree/off-road-dataset) branch.
> - For the greensward (on-road) dataset, switch to the [`Hunter-SE-Onroad-Dataset`](https://github.com/Tinker-Twins/AutoDRIVE-Hunter-SE-Dataset/tree/greensward-dataset) branch.

### About This Repository

This repository processes and compiles all individual files from the offroad [`AutoDRIVE-Hunter-SE-Dataset`](https://github.com/Tinker-Twins/AutoDRIVE-Hunter-SE-Dataset/tree/on-road-dataset) into the "Project-Varuna" format. The original dataset was collected using the AutoDRIVE Ecosystem, capturing data from the **Hunter SE** vehicle. For more information, visit the [AutoDRIVE-Hunter-SE repository](https://github.com/Tinker-Twins/AutoDRIVE).

## Dataset Structure

The following structure should be used when working with the "Project-Varuna-Custom" format in the GUI application:

| **Data**    | Timestamp               | posX | posY | Yaw | Roll | Pitch | Input Velocity | Steering |
|-------------|-------------------------|------|------|-----|------|-------|----------------|----------|
| **Unit**    | yyyy_MM_dd_HH_mm_ss_fff | m    | m    | rad | rad  | rad   | m/s            | rad      |

Ensure any custom datasets follow this structure.

### Additional Notes

- **Coordinate Frames**: Position (`posX`, `posY`) and yaw should be in the map frame (global pose coordinates). The Multi-Model Parameterized Koopman (MMPK) workflow will internally convert the data to a body frame representation, enabling pose-agnostic model generation.
  
- **Angle Conventions**: Roll, pitch, and yaw should follow the **ISO 8855** convention:
  - Roll angles should be within the range \([-π, π]\), where rightward roll is positive, and leftward roll is negative.
  - Pitch angles should be within \([-π, π]\), where forward pitch is positive, and backward pitch is negative.
  - Yaw follows the same convention: counter-clockwise rotation is positive, and clockwise rotation is negative.

- **IMU Conventions**: If your robot’s IMU uses the **SAE J670** convention, you can select this option in the GUI while mapping the relevant topic. The package will convert it to the **ISO 8855** format for path tracking.

## File Organization

Files in this repository follow a naming convention: `modality_frequency_throttle-value_run_number.csv`

- **modality**: Type of teleoperation modality (Keyboard, Joystick, Steering Wheel) used for data collection.
- **frequency**: Indicates the frequncy at which data is collected.
- **throttle**: Indicates the locked throttle input.

## Citation

If you use Project-Varuna for research or validation purposes, please reference and cite the following:

#### [Expanding Autonomous Ground Vehicle Navigation Capabilities through a Multi-Model Parameterized Koopman Framework](https://www.researchgate.net/publication/380152547_Expanding_Autonomous_Ground_Vehicle_Navigation_Capabilities_through_a_Multi-Model_Parameterized_Koopman_Framework)
```bibtex
@unknown{Joglekar_MMPK,
author = {Joglekar, Ajinkya and Samak, Chinmay and Samak, Tanmay and Krovi, Venkat and Vaidya, Umesh},
year = {2024},
month = {04},
pages = {},
title = {Expanding Autonomous Ground Vehicle Navigation Capabilities through a Multi-Model Parameterized Koopman Framework},
doi = {10.13140/RG.2.2.33007.24485}
}
```

#### [Modeling and Control of Off-road Autonomous Vehicles with Situationally Aware Data-Driven Framework](https://www.researchgate.net/publication/383427789_Modeling_and_Control_of_Off-road_Autonomous_Vehicles_with_Situationally_Aware_Data-Driven_Framework)
```bibtex
@unknown{Joglekar_Adaptive_MMPK,
author = {Joglekar, Ajinkya and Vaidya, Umesh and Krovi, Venkat},
year = {2024},
month = {08},
pages = {},
title = {Modeling and Control of Off-road Autonomous Vehicles with Situationally Aware Data-Driven Framework},
doi = {10.13140/RG.2.2.13288.48642}
}
```



#### [Data-Driven Modeling and Experimental Validation of Autonomous Vehicles Using Koopman Operator](https://www.researchgate.net/publication/380152547_Expanding_Autonomous_Ground_Vehicle_Navigation_Capabilities_through_a_Multi-Model_Parameterized_Koopman_Framework)
```bibtex
@inproceedings{inproceedings,
author = {Joglekar, Ajinkya and Sutavani, Sarang and Samak, Chinmay and Samak, Tanmay and Kosaraju, Krishna and Smereka, Jonathon and Gorsich, David and Vaidya, Umesh and Krovi, Venkat},
year = {2023},
month = {10},
pages = {9442-9447},
title = {Data-Driven Modeling and Experimental Validation of Autonomous Vehicles Using Koopman Operator},
doi = {10.1109/IROS55552.2023.10341797}
}
```

#### [Analytical Construction of Koopman EDMD Candidate Functions for Optimal Control of Ackermann-Steered Vehicles](https://par.nsf.gov/servlets/purl/10491343)
```bibtex
@article{article,
author = {Joglekar, Ajinkya and Samak, Chinmay and Samak, Tanmay and Kosaraju, Krishna and Smereka, Jonathon and Brudnak, Mark and Gorsich, David and Krovi, Venkat and Vaidya, Umesh},
year = {2023},
month = {01},
pages = {619-624},
title = {Analytical Construction of Koopman EDMD Candidate Functions for Optimal Control of Ackermann-Steered Vehicles},
volume = {56},
journal = {IFAC-PapersOnLine},
doi = {10.1016/j.ifacol.2023.12.093}
}
```