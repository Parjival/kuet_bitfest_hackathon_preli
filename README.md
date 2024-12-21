# kuet_bitfest_hackathon_preli
Preliminary contest codes
# Challenge 1 Justification
1. Learning Rate
Suggested Value: 5e-5 or 3e-5

Reasoning:
Transformer models like MT5 are sensitive to the learning rate.
A lower learning rate (e.g., 1e-5) can prevent overfitting and stabilize training for small datasets or when fine-tuning pre-trained models.
A moderately higher learning rate (e.g., 5e-5) works well for larger datasets.
Justification: We choose 5e-5 as it is commonly used in fine-tuning pre-trained models, providing a balance between speed and stability.

2. Batch Size
Suggested Value: 8 or 16 (per device)

Reasoning:
Larger batch sizes allow the model to generalize better but require more GPU memory.
For memory-limited setups, a smaller batch size (e.g., 8) is preferred.
Using gradient accumulation can simulate larger batch sizes if hardware is constrained.
Justification: A batch size of 8 fits most setups without running into memory issues while allowing for reasonable convergence speed.

3. Number of Epochs
Suggested Value: 3 to 5

Reasoning:
Pre-trained models require fewer epochs to converge since the weights are already initialized.
Longer training may lead to overfitting, especially for smaller datasets.
Justification: We choose 3 epochs as a baseline for fine-tuning. If the validation loss does not stabilize, it can be increased to 5.

4. Weight Decay
Suggested Value: 0.01

Reasoning:
Weight decay regularizes the model by penalizing large weights, which can prevent overfitting.
A small value (e.g., 0.01) works well for fine-tuning pre-trained models.
Justification: It balances the trade-off between underfitting and overfitting.

5. Gradient Clipping
Suggested Value: 1.0

Reasoning:
Gradient clipping prevents exploding gradients, ensuring stable training.
A value of 1.0 is standard for transformer models.
Justification: It helps avoid training instabilities in Seq2Seq tasks.

6. Learning Rate Scheduler
Suggested Value: Linear decay with warm-up

Reasoning:
A warm-up phase helps the model adjust to the new task before decaying the learning rate.
Linear decay ensures a steady reduction in the learning rate over time, which improves stability.
Justification: Warm-up combined with linear decay improves fine-tuning efficiency for transformer models.

7. Evaluation Strategy
Suggested Value: Evaluate at the end of every epoch

Reasoning:
Regular evaluation ensures the model isn't overfitting and provides feedback on performance.
Evaluating too frequently (e.g., every batch) can slow down training without significant benefits.
Justification: Evaluation after each epoch strikes a good balance between monitoring and training efficiency.

8. Early Stopping
Suggested Value: Stop training if the validation loss does not improve for 2 consecutive evaluations.

Reasoning:
Prevents unnecessary computation if the model has converged.
Helps avoid overfitting.
Justification: Ensures computational efficiency and prevents overfitting.
