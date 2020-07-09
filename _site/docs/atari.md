## Atari Environments

| Environment | Actions | Agents  | Manual Control | Action Shape | Action Values | Observation Shape | Observation Values |
|--------------|---------|---------|----------------|--------------|---------------|-------------------|--------------------|
| [Boxing](boxing)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Combat: Tank](combat_tank)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Combat: Plane](combat_plane)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Double Dunk](double_dunk)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Entombed: Competitive](entombed_competitive)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Entombed: Cooperative](entombed_cooperative)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Flag Capture](flag_capture)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Joust](joust)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Ice Hockey](ice_hockey)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Maze Craze](maze_craze)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Mario Bros](mario_bros)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Othello](othello)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Pong: Classic](pong_classic)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Pong: Basketball](pong_basketball)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Pong: Foozpong](pong_foozpong)   | Discrete  | 4 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Pong: Quadrapong](pong_quadrapong)   | Discrete  | 4 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Pong: Team Volleyball](pong_volleyball)   | Discrete  | 4 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Space Invaders](space_invaders)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Space War](space_war)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Surround: Original](surround)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Tennis](tennis)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Video Checkers](video_checkers)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Wizard of Wor](wizard_of_wor)   | Discrete  | 2 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |
| [Warlords](warlords)   | Discrete  | 4 | No      | (1,)    | [0,17]         | (210, 160, 3)         | (0,255)            |


The Atari environments are based off the [Arcade Learning Environment](https://github.com/mgbellemare/Arcade-Learning-Environment). This environment was instrumental in the development of modern reinforcement learning, and so we hope that our [multi-agent version](https://github.com/PettingZoo-Team/Multi-Agent-ALE) of it will be useful in the development of multi-agent reinforcement learning.

### Games overview

Most games are two player, with the exception of Warlords and a couple of Pong variations which are four player.

There are three types of games:

### Environment details

The ALE environment has been studied extensively and examined for various flaws and how to fix them.  

* Determinism: The Atari console is deterministic, and so agents can theoretically memorize precise sequences of actions that will maximize the end score. This is not ideal, so we enable *sticky actions*, controlled by the `repeat_action_probability` environment parameter, by default. This is the recommended approach of  *"Machado et al. (2018), "Revisiting the Arcade Learning Environment: Evaluation Protocols and Open Problems for General Agents"*


### Common Parameters

All the Atari environments have the following environment parameters:

```
<atar_game>.env(seed=None, obs_type='rgb_image', frameskip=3, repeat_action_probability=0.25, full_action_space=True)
```

```
seed: Set to specific value for deterministic, reproducible behavior.

obs_type: default value of 'rgb_image' leads to (210, 160, 3) image pixel observations like you see as a a human, 'grayscale_image' leads to a black and white (210, 160, 1) image, 'ram' leads to an observation of the 1024 bits that comprise the RAM of the atari console.

frameskip: number of frames to skip each time you take an action.

repeat_action_probability: probability you repeat an action from the previous frame (not step, frame), even after you have chosen a new action. Simulates the joystick getting stuck and not responding 100% quickly to moves.

full_action_space: The effective action space of the atari games is often smaller than the full space of 18 moves. This shrinks the action space to this smaller space.
```

### Citation

If you use the Atari environments in your research please cite the following paper:

```
@Article{bellemare13arcade,
  author = { {Bellemare}, M.~G. and {Naddaf}, Y. and {Veness}, J. and {Bowling}, M.},
  title = {The Arcade Learning Environment: An Evaluation Platform for General Agents},
  journal = {Journal of Artificial Intelligence Research},
  year = "2013",
  month = "jun",
  volume = "47",
  pages = "253--279",
}
```