# HardMaze

This environment is part of the Classic Control environments which contains general information about the environment.

|  |  |
|--|--|
| Action Space      | `Discrete(3)` |
| Observation Space | `Box(0, 1, (9,), float32)` |

## Action Space

The action is a `ndarray` with shape `(1,)` which can take values `{0, 1, 2}`.

- 0: Turn left
- 1: Go forward
- 2: Turn right

## Observation Space

The observation is a `ndarray` with shape `(9,)` with the values corresponding to the following positions and velocities:

| Num | Observation           | Min                 | Max               |
|-----|-----------------------|---------------------|-------------------|
| 0   | Agent Relative Position x         | 0                | 1               |
| 1   | Agent Relative Position y         | 1               | 1               |
| 2   | Cart Velocity         | -Inf                | Inf               |
| 3   | Pole Angle            | ~ -0.418 rad (-24°) | ~ 0.418 rad (24°) |
| 4   | Pole Angular Velocity | -Inf                | Inf               |

**Note:** While the ranges above denote the possible values for observation space of each element,
    it is not reflective of the allowed values of the state space in an unterminated episode. Particularly:
-  The cart x-position (index 0) can be take values between `(-4.8, 4.8)`, but the episode terminates
   if the cart leaves the `(-2.4, 2.4)` range.
-  The pole angle can be observed between  `(-.418, .418)` radians (or **±24°**), but the episode terminates
   if the pole angle is not in the range `(-.2095, .2095)` (or **±12°**)

## Rewards
Since the goal is to keep the pole upright for as long as possible, by default, a reward of `+1` is given for every step taken, including the termination step. The default reward threshold is 500 for v1 and 200 for v0 due to the time limit on the environment.

If `sutton_barto_reward=True`, then a reward of `0` is awarded for every non-terminating step and `-1` for the terminating step. As a result, the reward threshold is 0 for v0 and v1.

