# MNIST Distributed Example

## Install

To run this project you need:

- [Python](https://python.org/) 3.5+
- [Git](https://git-scm.com/)
- TensorFlow 1.8+ (to run locally). Get it with `pip install tensorflow`

### Setting Up

## Usage

#### Local

Start out by cloning this repository onto your local machine.

Then cd into the folder you just cloned with `cd mnist`.

Single instance mode is very simple. You just execute mnist.py:
```shell
python mnist.py
```

For distributed mode, you need to launch this script for each worker and parameter server.
```shell
# Worker-0 (Master)
python mnist.py --job_name worker --task_index 0 --worker_hosts "localhost:2222,localhost:2223" --ps_hosts "localhost:2224"

# Worker-1
python mnist.py --job_name worker --task_index 1 --worker_hosts "localhost:2222,localhost:2223" --ps_hosts "localhost:2224"

# Parameter server
python mnist.py --job_name ps --task_index 0 --worker_hosts "localhost:2222,localhost:2223" --ps_hosts "localhost:2224"
```
This will start a local job in distributed mode with 2 workers and 1 parameter server. This is useful for testing purposes but will not speed up your training.

