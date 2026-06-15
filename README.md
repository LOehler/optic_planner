# ros2 optic planner

This repository is forked from [triboelectric](https://github.com/triboelectric/optic_planner) with minimal changes

It consists of two packages
 - [OPTIC planner](https://nms.kcl.ac.uk/planning/software/optic.html) that builds within [ROS2](https://github.com/ros2)
 - [PlanSys2](https://github.com/IntelligentRoboticsLabs/ros2_planning_system) plugin to run the OPTIC planner in the PlanSys2 framework
 
After building with colcon and sourcing, it can be launched as a stand-alone plan solver with
```
ros2 run optic_planner optic_planner <optional-args> <domain.pddl> <problem.pddl> <optional-plan>
```
or loaded as a plugin for plansys2 as `plansys2/OPTICPlanSolver`

---

### optional arguments

| flag | description |
|--------|-----|
| -N     | Don't optimise solution quality (ignores preferences and costs)  |
| -0     | Abstract out timed initial literals that represent recurrent windows |
| -n<lim>| Optimise solution quality, capping cost at <lim> |
| -citation | 	Display citation to relevant papers |
| -b     | Disable best-first search - if EHC fails, abort|
| -E     | Skip EHC: go straight to best-first search |
|-e      | Use standard EHC instead of steepest descent |
|-h      | Disable helpful-action pruning|
|-k      | Disable compression-safe action detection|
|-c      | Enable the tie-breaking in RPG that favour actions that slot into the partial order earlier|
|-S      | Sort initial layer facts in RPG by availability order (only use if using -c)|
|-m      | Disable the tie-breaking in search that favours plans with shorter makespans|
|-F      | Full FF helpful actions (rather than just those in the RP applicable in the current state)|
|-r      | Read in a plan instead of planning (need to specify plan after problem.pddl)|
|-T      | Rather than building a partial order, build a total-order|
|-v<n>   | Verbose to degree n (n defaults to 1 if not specified)|
|-L<n>   | LP verbose to degree n (n defaults to 1 if not specified)|
|-x<n>   | timeout in seconds|

All arguments can be found in [opticMain](https://github.com/LOehler/optic_planner/blob/rolling/optic_planner/src/optic/opticMain.cpp)
