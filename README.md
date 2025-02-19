# Week_5_technical
Hugging Face: https://huggingface.co/Rasmuzeri/phi-2-dialogsum-finetuned

Changes done:
1. Import AutoTokenizer: Added the explicit import from transformers import AutoTokenizer.
2. GPU Utilization Function: Added a function print_gpu_utilization() to display GPU memory usage. This function requires the pynvml library.
3. Tokenizer Consistency: Changed the gen function to use the same tokenizer instance created earlier in the code, rather than creating a separate eval_tokenizer. The tokenization process is also simplified and the tensors are explicitly moved to "cuda" within the function.
4. gen Function Return: Modified the gen function to consistently return a string. It now checks for the presence of "Output:\n" and extracts the relevant part of the generated text. It also includes a warning if the delimiter is not found and returns the entire generated text in that case. The original code returned a list even when num_return_sequences was set to 1. The new code always returns a string.
5. gen Function Call: The call to the gen function is simplified. The result is directly assigned to output, removing the unnecessary indexing and split.  The original code output = res[0].split('Output:\n')[1] is replaced with the now correctly functioning output = gen(original_model, formatted_prompt, 100).
6. Dash Line: The creation of the dash line is simplified using string multiplication: dash_line = '-' * 100.
7. create_prompt_formats Function: The create_prompt_formats function is modified to use .get() when accessing the dialogue and summary fields of the sample dictionary. This prevents potential KeyError exceptions if these keys are missing.  The joining of the parts is also made more explicit.  The code is also simplified by removing unnecessary f-strings where they are not needed.
8. The training configuration was modified by reducing max_steps, logging_steps, save_steps, and eval_steps to 500 and 50 respectively, and by removing the explicit setting of peft_model.config.use_cache to False, thereby likely enabling caching.
9. Changed the HF username.
10. gen Function Output Handling: The code now directly uses the string returned by the gen function, eliminating the need for indexing ([0]) and improving robustness by checking for the existence of "Output:\n" before splitting. This change is consistent with the earlier modification to the gen function itself, which now guarantees a string return.
11. The code was updated to remove the unused instruct_model_summaries list and to correctly handle the string output of the gen function, including a check for the "Output:\n" delimiter before splitting, for both the original and PEFT model outputs.

![image](https://github.com/user-attachments/assets/029ec8bd-3f1e-494a-8acd-529d16d505eb)
