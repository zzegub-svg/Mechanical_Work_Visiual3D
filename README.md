# Mechanical_Work_Visiual3D

Visual3D Gait Analysis Pipeline
Overview

This Visual3D pipeline processes full-body gait data for multiple subjects, calculating joint angles, moments, and powers for the lower limbs, as well as treadmill belt speeds.

The pipeline includes:

File management and cleanup

Selects all active files

Deletes processed folders for metrics and derived signals to ensure a clean workflow

Signal preprocessing

Lowpass filtering of analog and motion capture signals (Butterworth, 6 Hz cutoff for markers/targets, 4 Hz for center of pressure)

Rectification and event-specific signal manipulation (heel distance, absolute signals)

Gait event processing

Deletes unnecessary events

Computes automatic gait events for left and right sides

Calculates metrics like weight from ground reaction forces

Joint kinematics and kinetics computation

Model-based calculation of joint angles, moments, and powers for:

Ankles (left/right)

Knees (left/right)

Hips (left/right)

Pelvis center of mass (COM)

Normalization to subject mass when appropriate

Power segmentation and integration

Splits joint power into positive and negative phases for each joint

Integrates over gait events (LON/LOFF for left, RON/ROFF for right) to compute:

L_Ankle_Work_Pos, L_Ankle_Work_Neg

R_Ankle_Work_Pos, R_Ankle_Work_Neg

L_Knee_Work_Pos, L_Knee_Work_Neg

R_Knee_Work_Pos, R_Knee_Work_Neg

L_Hip_Work_Pos, L_Hip_Work_Neg

R_Hip_Work_Pos, R_Hip_Work_Neg

Treadmill belt speed processing

Corrects belt speed values to remain within realistic limits (0.9 – 2.2 m/s)

Applies lowpass filtering

Extracts belt speed at specific events for further analysis

Key Features

Fully automated across all active files

Supports multiple signal types: Target, Analog, Metric, Derived, Link Model-Based

Normalization ensures comparability across subjects

Generates processed metrics ready for statistical analysis in R or Python

Example Output Metrics

L_Ankle_Work_Pos / R_Ankle_Work_Neg

L_Knee_Work_Pos / R_Knee_Work_Neg

L_Hip_Work_Pos / R_Hip_Work_Neg

Left_BeltSpeed / Right_BeltSpeed
