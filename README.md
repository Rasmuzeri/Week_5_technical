# Week_5_technical
Hugging Face: https://huggingface.co/Rasmuzeri/phi-2-dialogsum-finetuned

Changes done:
1. Library Installation:
- In the initial version, the code started with library installations using !pip install.
- In the revised version, the installation commands were moved to the beginning of the notebook to ensure all necessary libraries are installed before any other code is run.

2. Tokenizer Configuration:
- In the initial version, the tokenizer was instantiated with trust_remote_code=True and padding_side="left".
- In the revised version, use_fast=False was added to the tokenizer instantiation parameters.

3. Model Loading:
- In the initial version, the model was loaded using AutoModelForSeq2SeqLM.from_pretrained with trust_remote_code=True and low_cpu_mem_usage=True.
- In the revised version, torch_dtype=torch.float16 was added to the model loading parameters.

4. Training Configuration:
- In the initial version, the TrainingArguments were configured with fp16=True, optim="paged_adamw_8bit", and per_device_train_batch_size=1.
- In the revised version, gradient_accumulation_steps=4 and max_grad_norm=0.3 were added to the TrainingArguments.

5. Training Loop:
- In the initial version, the training loop used the Trainer class with the specified model, dataset, and training arguments.
- In the revised version, the training loop was modified to include gradient accumulation and gradient clipping using the accelerator and optimizer objects.

6. Evaluation:
- In the initial version, the evaluation was performed using the evaluate function with the specified metric.
- In the revised version, the evaluation was moved inside the training loop to evaluate the model's performance on the fly.

7. Logging:
- In the initial version, the code logged the training loss and learning rate using wandb.log.
- In the revised version, additional logging was added to track the evaluation results during training.

8. Data Loading:
- In the initial version, the dataset was loaded using load_dataset with the specified dataset name and split.
- In the revised version, the dataset loading was modified to handle different splits of the dataset.

9. Preprocessing:
- In the initial version, the preprocessing function preprocess_function was defined to tokenize the input and target sequences.
- In the revised version, the preprocessing function was updated to handle different input formats and include additional preprocessing steps.

10. Summary Generation:
- In the initial version, the summary generation was performed using the model.generate method with the specified input sequence.
- In the revised version, the summary generation was modified to include additional parameters such as max_length, num_beams, and temperature.
