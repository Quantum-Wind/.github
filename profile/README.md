# Quantum Wind

We're a team of six engineering students at Worcester Polytechnic Institute (WPI)
building **Gait Drive**, a swerve module for the FIRST Robotics Competition (FRC)
that can change its gear ratio during a match. This is our Major Qualifying Project
(MQP), advised by Professor Kenneth Stafford.

## Why change ratios mid-match?

Swerve is now the standard FRC drivetrain: over 90% of teams ran it by Week 6 of
the 2025 season. Every module on the market ships with a fixed gear ratio, though,
and every team runs the robot off the same 12 V battery. That forces a tradeoff
before the season starts:

- **Lower reduction:** higher top speed for full-field cycles, but more current
  drawn when accelerating.
- **Higher reduction:** more torque and acceleration, better battery life, and
  better for pushing and defense, but slower over long runs.

Gait Drive changes ratio on the fly, without pneumatics. A robot can sprint the
length of the field and still have torque and battery when it needs them. We
named it after an animal's gait: the module changes its stride to suit what the
robot is doing.

## Targets

We measure against the SDS MK5n, the module most top teams run today.

| Requirement | Target |
|---|---|
| Cycle time | 10% faster than an MK5n (R3) over a 40 ft full-field cycle |
| Efficiency | More than the MK5n's 83% mechanical efficiency |
| Reliability | One full FRC season (~40 hours) without a teardown |
| Weight | 4.5 lb dry, 7 lb with drive, steer, and shifting motors |
| Footprint | 5.5" × 8.3" × 6.3", not counting the shifting actuator |
| Cost | $217 FOB per unit at a 2,000-unit production run |

The software side follows the same idea: a low-barrier library that runs the
transmission in the background of team code, with automatic ratio selection, a
semi-automatic mode for manual control, and the ability to set ratio inside
autonomous paths.

## Repositories

| Repo | What it is |
|---|---|
| [GaitLib](https://github.com/Quantum-Wind/GaitLib) | C++ WPILib vendordep for running a Gait module. Built on standard WPILib swerve types, so modules drop into `SwerveDriveKinematics` and the pose estimators. Builds for the roboRIO, Linux, Windows, and macOS. |
