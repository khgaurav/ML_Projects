# Assignment 05 Questions and Answers

This document lists the conceptual, hyperparameter, and mathematical questions for Assignment 05. Replace the placeholders below with your final answers.

---

## Part 2: Hyperparameters

### 1. List every hyperparameter in the case-study code, and explain why the weights inside `nn.Linear(7, 12)` are not hyperparameters.

**Answer:**
- Hyperparameters in code:
  - Learning rate ($\eta = 0.001$)
  - Batch size ($10$)
  - Number of training epochs ($100$)
  - Network architecture choices (number of layers, number of units per layer, activation functions like ReLU and Sigmoid)
  - Optimizer choice (Adam)
  - Loss function choice (BCELoss)
- Why weights are not hyperparameters:
  - They are learnable parameters. They start as random values and are changed by the training loop itself (every `optimizer.step()` call updates them using gradients computed from `loss.backward()`).

### 2. The code uses $\eta = 0.001$. Predict what the printed loss would do with (a) $\eta = 5.0$ and (b) $\eta = 10^{-7}$, and justify using $w \leftarrow w - \eta \frac{\partial E}{\partial w}$.

**Answer:**
- **(a) $\eta = 5.0$:**
  - The loss will be very high because the learning rate will be much higher than the delta itself. So the weight will be updated with a very large value in the wrong direction and it will keep flipping, hence never converging. 
- **(b) $\eta = 10^{-7}$:**
  - The loss will be very low because the updates will be very small and it will take a very long time to converge to the minimum loss. 

### 3. With 768 patients and batch size 10: (a) how many weight updates per epoch? (b) over 100 epochs? (c) what is special about the last batch of each epoch?

**Answer:**
- **(a) Updates per epoch:** 77
- **(b) Updates over 100 epochs:** 7700
- **(c) Special feature of the last batch:** It will be only 8 samples

### 4. Keeping everything else fixed, what changes in the procedure if the batch size is set to (a) 768 and (b) 1? Name each variant of gradient descent.

**Answer:**
- **(a) Batch size = 768:**
  - There will be only 1 weight update per epoch. This means the updates will be very accurate but will take a long time to converge. (Batch Gradient Descent).
- **(b) Batch size = 1:**
  - There will be 768 weight updates per epoch. This means the updates will be very noisy but will converge faster. (Stochastic Gradient Descent).

### 5. The code always runs exactly 100 epochs. What risk does that fixed choice carry, and what measurement would the code need in order to stop at the right time?

**Answer:**
- **Risk:** The model will overfit to the training data.
- **Required measurement for stopping:** We need to calculate the accuracy of the model on unseen data. So using a test set accuracy, we can stop training when the accuracy starts to decrease.

### 6. Give two reasons the output activation must be a sigmoid here, referencing the targets built in step 1 and the loss chosen in step 3.

**Answer:**
- **Reason 1:** It maps the output to the range $(0, 1)$ which matches the range of targets chosen in Step 1 (0 and 1).
- **Reason 2:** The BCE loss expects its output to be in the range (0, 1) to avoid `log(0)` which is undefined.

---

## Part 3: Mathematics

### 7. Show, layer by layer, that the network has exactly 209 learnable parameters.

**Answer:**
- **Layer 1 (Linear):** It uses nn.Linear(7,12), so it has 7 inputs and 12 outputs. So total of (7*12) weights and 12 biases. So total of 96 parameters.
- **Layer 2 (Linear):** It uses nn.Linear(12,8), so it has 12 inputs and 8 outputs. So total of (12*8) weights and 8 biases. So total of 104 parameters.
- **Layer 3 (Linear):** It uses nn.Linear(8,1), so it has 8 inputs and 1 output. So total of (8*1) weights and 1 bias. So total of 9 parameters.
- **Total:** 209 learnable parameters.

### 8. A hidden neuron has weights $w = [0.1, -0.2]$ on two inputs, bias $b = 0.3$, and receives $x_1 = 0.5, x_2 = 1.0$. (a) Compute $z$. (b) Compute the ReLU output. (c) Repeat with $b = -0.3$ and state what happens to the gradient through this neuron.

**Answer:**
- **(a) Compute $z$:** z = 0.1\*0.5 - 0.2\*1.0 + 0.3 = 0.05 - 0.2 + 0.3 = 0.15
- **(b) Compute ReLU output:** ReLU(0.15) = 0.15
- **(c) With $b = -0.3$:**
  - z = 0.1\*0.5 - 0.2\*1.0 - 0.3 = 0.05 - 0.2 - 0.3 = -0.45
  - ReLU(-0.45) = 0

### 9. With $\sigma(z) = 1/(1+e^{-z})$: (a) compute $\sigma(0)$; (b) compute $\sigma(0.15)$ to three decimals; (c) what does $\sigma$ approach as $z \rightarrow \pm\infty$, and why does that suit a probability?

**Answer:**
- **(a) $\sigma(0)$:** 1/(1+e^(-0)) = 1/(1+1) = 0.5
- **(b) $\sigma(0.15)$:** 1/(1+e^(-0.15)) = 1/1.161 = 0.861
- **(c) As $z \rightarrow \pm\infty$:**
  - As $z \rightarrow \infty$, $\sigma(z)$ -> 1 and as $z \rightarrow -\infty$, $\sigma(z)$ -> 0. This suits a probability as it maps the output to the range (0,1).

### 10. A patient’s true label is $t = 1$. Compute the BCE loss for (a) $\hat{y} = 0.9$ and (b) $\hat{y} = 0.1$. What principle does the comparison demonstrate?

**Answer:**
- **(a) $\hat{y} = 0.9$ Loss:** $-[(1*\log(0.9))+(0*\log(0.1))]$ = -0.1053
- **(b) $\hat{y} = 0.1$ Loss:** $-[(1*\log(0.1))+(0*\log(0.9))]$ = 2.3026
- **Principle demonstrated:**
  - The loss is much smaller when the prediction is near the target value (0.9 closer to true label 1).

### 11. One weight has $w = 0.37$, the learning rate is $\eta = 1.2$, and backpropagation finds $\partial E/\partial w = -0.0201$. (a) Apply the update rule. (b) Explain in one sentence why the weight increased despite the minus sign.

**Answer:**
- **(a) Update calculation:** w = 0.37 -1.2\*(-0.0201) = 0.37 + 0.02412 = 0.39412
- **(b) Explanation:** The weight increased because the gradient was negative, so subtracting it from the weight increased the value.

### 12. For the output neuron, $E$ depends on $w$ through $\hat{y} = \sigma(z)$ and $z = \sum w x + b$. (a) Write $\partial E/\partial w$ as a product of three factors. (b) Which factor equals just the input $x$, and why? (c) Given $\sigma'(z) = \sigma(z)(1-\sigma(z))$, what is the largest value $\sigma'$ can take, and at which $z$?

**Answer:**
- **(a) Three factors:** $\frac{\partial E}{\partial w} = \frac{\partial E}{\partial \hat{y}}\frac{\partial \hat{y}}{\partial z}\frac{\partial z}{\partial w}$
- **(b) Factor equal to $x$ and why:** $\frac{\partial z}{\partial w} = x$. This is because z = wx + b, so when differentiating with respect to w, we get x.
- **(c) Largest value of $\sigma'$ and at which $z$:** Let $a = \sigma(z)$. Then $\sigma'(z) = a(1-a)$. This is a quadratic function of a, which has a maximum at a = 0.5. So the largest value of $\sigma'(z)$ is 0.25, which happens at z = 0.

### 13. A student deletes `optimizer.zero_grad()`. Write what each weight’s stored gradient contains after batch 3 (in terms of the per-batch gradients $g_1, g_2, g_3$) and state why the resulting updates are wrong.

**Answer:**
- **Gradient contents after batch 3:** $g_1 + g_2 + g_3$
- **Why this update is wrong:**
  This update is wrong because it accumulates the gradients from all the batches instead of updating the weights based on the gradient of the current batch. 

### 14. Explain what breaks mathematically if `optimizer.step()` were called before `loss.backward()` in the first iteration, and why all gradients must be computed before any weight moves.

**Answer:**
- **What breaks in the first iteration:** 
  The weights will be updated with random values since no gradients have been computed yet.
- **Why gradients must be computed first:**
  This is because the gradients are computed using the chain rule, which requires the gradients of all the layers to be computed before the weights can be updated.
