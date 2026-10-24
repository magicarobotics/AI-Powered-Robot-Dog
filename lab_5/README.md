# Lab 5: How to Train Your Dog

In this lab, you will train a reinforcement learning (RL) walking policy for Pupper v3, tune reward functions for velocity tracking and stable locomotion, evaluate the learned behavior in simulation, and deploy your policy to the physical robot.

## Files

- `deploy.sh` — Installs, rebuilds, and launches the neural controller. Can also download a trained policy from Weights & Biases (W&B).
- `install.py` — Installs the controller files into Pupper's ROS 2 workspace.
- `download_policy.py` — Downloads and validates a trained policy from W&B.
- `config.yaml` — Controller configuration and gamepad policy assignments.
- `launch.py` — ROS 2 controller launch file.
- `src/` — Neural controller C++ implementation.
- `policies/` — Default walking policies and the location for student-trained policies.
- `test/` — Controller tests.
- `docs/` — Gamepad reference diagram.

## Step 1. Set Up the Controller on Pupper

Connect to Pupper using SSH.

Update the course repository:

```bash
cd ~/AI-Powered-Robot-Dog
git pull
cd lab_5
```

Install, rebuild, and launch the neural controller:

```bash
bash deploy.sh
```

This installs the updated controller into Pupper's ROS 2 workspace and launches it.

Connect the gamepad and verify that Pupper can walk using the default policy before proceeding.

For subsequent sessions, you can launch the installed controller using:

```bash
ros2 launch neural_controller launch.py
```

## Step 2. Train Your Walking Policy

Open the Google Colab notebook linked in your Lab 5 instruction document.

Select **File → Save a copy in Drive** and work in your own copy.

Use the following task:

```python
TASK = "Mjlab-VelocityFS-Flat-Pupper-v3"
```

Train your walking policy, tune the reward weights, and evaluate its performance in simulation.

Your training runs, metrics, and exported policies are saved to Weights & Biases (W&B).

## Step 3. Deploy Your Trained Policy

After training, connect to Pupper and navigate to the Lab 5 directory:

```bash
cd ~/AI-Powered-Robot-Dog/lab_5
```

Authenticate with W&B if you have not already done so:

```bash
python3 -m wandb login --relogin
```

Find the run ID at the end of your W&B run URL.

Deploy your policy:

```bash
bash deploy.sh mjlab/<your-run-id>
```

The script downloads the trained policy, validates it, installs the updated controller files, rebuilds the ROS 2 workspace, and launches the controller.

The trained walking policy is assigned to the **square-button policy slot** on the gamepad.

Test your policy with instructor or TA supervision and keep the emergency stop accessible.

## Lab Deliverables

Refer to the Lab 5 instruction document for all deliverables, evaluation requirements, and questions.

## Acknowledgment

Adapted from Stanford University's CS123 Pupper lab materials.