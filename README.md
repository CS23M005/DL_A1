# DL_A1
CS6910 - Assignment-1

The main branch of this repository consists of train.py and FFNN.py (complete work is done on FFNN.ipnyb).

train.py has the train_nn() function and config default for sweep.
sweep configuration can be changed inside train.py with in sweep_config dictionary

All necessary function definitions such as optimizers(sgd, nag, mgd, rmsprop, adam, nadam), 
activation functions (sigmoid, relu, tanh) and their derivaties, forward propagation framework and
backpropagation frame work are defined with in FFNN.ipynb

Call train_nn() from FFNN.ipynb for executing with default configuration

sweep configuration, train accuracy, validation accuracy, test accuracy is logged with wandb.log in FFNN.ipynb

sweep configuration is as follows:

sweep_config = {"name": "complete-sweep-25dw", "method": "random"}
sweep_config["metric"] = {"name": "validation_acc", "goal": "maximize"}
parameters_dict = {
                "num_epochs": {"values": [2, 3, 4, 5]}, \
                "num_hidden_layers": {"values": [2, 3, 4]}, \
                "size_hidden_layer": {"values": [16, 32, 64, 128]}, \
                "learning_rate": {"values": [ 1e-2, 1e-3, 1e-4]}, \
                "optimizer": {"values": ["sgd", "adam", "mgd", "nadam", "rmsprop", "nag"]}, \
                "batch_size": {"values": [32, 64, 128]}, \
                "weight_init": {"values": ["random", "xavier"]} , \
                "activation": {"values": ["sigmoid", "tanh", "relu"]}, \
                "loss": {"values": ["crossentropy"]}, \
                "reg_lambda": {"values": [0.001, 0.0005, 0]}, \
                  }
sweep_config["parameters"] = parameters_dict

