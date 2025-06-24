# AGKA: Annotation Guidelines-Based Knowledge Augmentation

Annotation Guidelines-Based Knowledge Augmentation: Towards Enhancing Large Language Models for Educational Text Classification

AGKA is a project aimed at enhancing Large Language Models (LLMs) for Educational Text Classification using annotation guidelines-based knowledge augmentation. This repository provides a comprehensive framework for performing multi-task classification on various educational text classification datasets using state-of-the-art LLMs and advanced prompting techniques.

## Key Features

- 🌐 Support for multiple LLMs, including GPT 3.5, GPT 4.0 (OpenAI), Llama 3 series (Meta), and Mistral series (Mistral)
- 🎯 Zero-shot, few-shot, and random prediction settings for flexible experimentation
- 📝 Customizable prompts and output formats tailored to each task and dataset
- ⚡️ Parallel processing for enhanced performance and efficiency
- 📊 Comprehensive evaluation metrics, including accuracy, precision, recall, and F1 score
- 🖼️ Intuitive confusion matrix visualization for model performance analysis
- 📚 Detailed logging and error handling for easy debugging and monitoring

## Supported Tasks and Datasets

AGKA supports the following tasks and datasets for Learning Engagement Classification:

### Behavior Classification
- Urgency Level
- Question

### Emotion Classification
- Binary Emotion
- Epistemic Emotion

### Cognition Classification
- Opinion
- Cognitive Presence

## Getting Started

### Prerequisites
- Python 3.6+
- Required dependencies (see `requirements.txt`)

### Installation
1. Clone the repository:
   ```
   git clone https://github.com/your-username/AGKA.git
   cd AGKA
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

### Usage
1. Prepare your dataset files in CSV format and place them in the appropriate directories under the `data` folder.

2. Configure the desired settings, tasks, datasets, and models in the `parse_args()` function of `predict.py`. Set the API keys in the `{'chat': "sk-XXX", 'fireworks': "XX"}` dictionary.

3. Run the `predict.py` script to perform predictions:
   ```shell
   python predict.py
   ```
   or process specified datasets:
   ```shell
   python predict.py --setting ['zero-shot','few-shot'] --model ['fireworks'] --model_name {'fireworks':['llama-v3-8b-instruct','llama-v3-70b-instruct']} --selected_tasks ['forum'] --selected_datasets ['en_forum_2_emotion','en_forum_2_opinion','en_forum_2_question','en_forum_coi_cognition','en_forum_epistemic_emotion','en_forum_urgent'] --prompt_type ['Vanilla','AGKA']
   ```

4. The predictions will be saved in the `outputs` folder, organized by task, dataset, and settings.

5. To evaluate the predictions, run the `evaluate.py` script:
   ```shell
   python evaluate.py
   ```
   or process specified datasets:
   ```shell
   python evaluate.py --model chat --seed 42 --selected_tasks ['forum'] --selected_datasets ['en_forum_2_emotion','en_forum_2_opinion','en_forum_2_question','en_forum_coi_cognition','en_forum_epistemic_emotion','en_forum_urgent']
   ```

6. The evaluation results, including metrics and confusion matrices, will be saved in the corresponding output folders.

## Customization
- To add new tasks or datasets, create appropriate templates in the `generate_template()` function of `predict.py` and update the `get_label_space()` and `get_task_name()` functions accordingly.
- To use different language models or APIs, modify the `query_*_model()` functions in `predict.py` and update the `parallel_query_*_model()` functions as needed.
- Experiment with different prompts and output formats by modifying the `generate_prompt()` function in `predict.py`.

## License
This project is licensed under the [MIT License](LICENSE).

## Acknowledgments
- The code builds upon the OpenAI API and Hugging Face Transformers library.
- Thanks to the authors of the various datasets used in this project.

Feel free to contribute, report issues, or suggest improvements!
