# snake ai

## running files

just cd to the directory you want. and run `python ./main.py`(uncomment or comment the train and test function)

## info

the prefixes `growing` and `no_growing` at each of each directory is just meant to reduce the complexitiy of task. (if `no_growing` then when snake eates food it won't increase it's length)

in each directory:
- `agent.py`: well this is the agent.(a that player learns to play game). and the type of it is mentioned on the suffixes (e.g. `q_learning`)

- `helper.py`: the helper functions(e.g. for plotting the results)

- `main.py`: has 2 functions train and test

- `snake.py`: the game(enviroment). i've implemented it, and i tried to make it like gym enviroments

- `state_setting.py`: the function used to implement the inputs that the agent will receive from enviroment (that makes the game more flexible)

## directories

### `no_growing_snake_q_learning`

after about less than 20_000 training steps the score passes from 1000 (Note the q values has been replaced so it might now get stuck in some places)

![no_growing_q_learning_img](./images/no_growing_q_learning.png)

### `growing_snake_q_learning`

well as the chart suggests, the agent is unable to go further than 50-60 because of the lack of information. (or maybe tweaking the hyper parameters might help)

![growing_snake_q_learning_chart](./growing_snake_q_learning/Q_values_23_07_26/results.png)

### `growing_snake_deep_q_learning`

well, the algorithm works fine if i've trained it more, (+ wider VISION_SIZE) probably it could master the game.

there is agent_cpu.py and agent_gpu.py. if you have a gpu access for tensorflow you probably wana use agent_gpu. if not you should use agent_cpu (the only thing that makes computations very expensive in agent_gpu is `tf.queue.RandomShuffleQueue`. for some reasons `tf.queue.RandomShuffleQueue` uses a lot resources in cpu).

and note that while useing snake.py the width and height should be equal. otherwise the error will raise from state_setting.py

the file `state_setting.py` know returns a window of the snake head(25)* + direction of food(4) + direction of snake(4).

![growing_snake_deep_q_learning](./images/growing_snake_deep_q_learning.png)

where:
- 0: is empty space
- -1: is the food
- 1: is snake head
- 2: is snake body
- 3: is walls

![growing_snake_deep_q_learning_results](growing_snake_deep_q_learning/saved_models_23_07_27/results.png)

evaluate_agent.py this is used for testing the agent with several hyperparameters in cartpole enviroment. the AdamW and xaiver init method worked well(learned faster)