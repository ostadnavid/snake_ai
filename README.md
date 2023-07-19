# snake ai

## running files

just cd to the directory you want. and run `python ./main.py` if you want to train a new agent.

else run `python ./testing.py` for testing pretrained agent

## info

the prefixes `growing` and `no_growing` at each of each directory is just meant to reduce the complexitiy of task. (if `no_growing` then when snake eates food it won't increase it's length)

in each directory:
- `agent.py`: well this is the agent.(a that player learns to play game). and the type of it is mentioned on the suffixes (e.g. `q_learning`)

- `helper.py`: the helper functions(e.g. for plotting the results)

- `main.py`: used to train the agent and save the weights(q values) on directories that start with `Q_values`

- `snake.py`: the game(enviroment). i've implemented it, and i tried to make it like gym enviroments

- `state_setting.py`: the function used to implement the inputs that the agent will receive from enviroment (that makes the game more flexible)

- `testing.py`: used to test the agent. which starts by loading the saved weights/q values and testing it.

## directories

### `no_growing_snake_q_learning`

after about less than 20_000 training steps the score passes from 1000

![no_growing_q_learning_img](./images/no_growing_q_learning.png)

### `growing_snake_q_learning`

well as the chart suggests, the agent is unable to go further than 60-70 because of the lack of information

![ff](./growing_snake_q_learning/Q_values_23_07_19_20_55_15/results.png)