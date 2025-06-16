# 🏁 Running the InterFuser Agent on CARLA 0.9.14

This document provides step-by-step instructions to set up the environment and run the InterFuser agent, adapted for **Python 3.8** and **CARLA 0.9.14**.

---

## 🧱 1. Environment Setup

> ⚠️ This step is only necessary if you intend to run the agent locally.

Create and activate a Conda environment:
```bash
conda create -n interfuser38 python=3.8
conda activate interfuser38
````

Clone your fork of the InterFuser repository:

```bash
git clone https://github.com/<your-username>/InterFuser-Carla0914.git
cd InterFuser-Carla0914
```

---

## 📦 2. Install Dependencies

Install the modified set of requirements. Note that we removed packages incompatible with Python 3.8:

* ❌ Removed: `matplotlib==3.0.3`, `open3d==0.9.0.0`
* ✅ Added: `carla==0.9.14`

To install the necessary packages:

```bash
pip install -r requirements.txt
```

Install the InterFuser module in editable mode:

```bash
pip install -e /home/jovyan/work/code/InterFuser/interfuser
```

---

## 💾 3. Download Pretrained Weights

Download the example model weights for direct evaluation from the following [link](http://43.159.60.142/s/p2CN).

Then move the weights to the correct directory:

```
InterFuser/leaderboard/team_code/
```

---

## ⚙️ 4. Configure Model Path

Open the following file:

```
leaderboard/team_code/interfuser_config.py
```

Set the path to the downloaded model weights by modifying the appropriate line, e.g.:

```python
'agent_config': '/absolute/path/to/model.ckpt',
```

---

## 🚦 5. Run the Evaluation

We provide a modified version of the original script:

**Modified script path**:

```
leaderboard/scripts/run_evaluation.sh
```

Make sure this script contains the correct paths and environment variables for:

* The model config file
* The team agent
* The route and scenario directories

Then execute it:

```bash
bash leaderboard/scripts/run_evaluation.sh
```

---

## 📸 6. Save Output Images (Optional)

To analyze the agent's visual perception and decision-making:
* We modified `interfuser_agent.py`
* In particular, the `setup()` and `save()` methods were edited to save RGB images (or other sensor outputs) during simulation.

This feature can be used to:
* Debug agent behavior
* Visualize failure cases
* Compare different model versions
