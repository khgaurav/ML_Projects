# Assignment 05: Diabetes Classification using PyTorch Neural Networks

## What this project does

This project builds, trains, and analyzes a multi-layer Neural Network using PyTorch to predict whether a patient has diabetes based on the dataset `diabetes.csv`.
- **Data Loading & Preprocessing**: Loading patient metrics, converting binary classes (`positive`/`negative`) to float targets (`1`/`0`), and formatting features into PyTorch float tensors.
- **Neural Network Architecture**: Building a three-layer sequential model with linear layers and non-linear activations (`ReLU` and `Sigmoid` output).
- **Training Loop & Optimization**: Training with Binary Cross Entropy loss (`nn.BCELoss`) and the Adam optimizer using mini-batch gradient descent.
- **Hyperparameter Comparison**: Investigating model convergence and training loss across different learning rates ($\eta = 5.0$, $\eta = 10^{-7}$, and $\eta = 0.001$).
- **Mathematical Analysis**: Answering conceptual and mathematical questions about gradient descent updates, backpropagation chain rule, activation function bounds, and calculating the exact parameter count (209 learnable parameters).

## How to run the notebooks

1. Open `Assignment_05.ipynb` or `NN_02.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
2. Make sure `diabetes.csv` is in the same folder as the notebooks.
3. Run the cells from top to bottom.
4. If needed, install the required packages using the `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```
