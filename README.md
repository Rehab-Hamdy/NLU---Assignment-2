# NLU---Assignment-2

NLU Assignment: Few-shot OpenQA with ColBERT Retrieval
This assignment explores the challenging task of few-shot open-domain question answering (OpenQA). Unlike standard QA, where a specific passage containing the answer is provided, OpenQA requires the system to retrieve relevant information from a vast collection of texts. This project pushes the boundaries further by using a general-purpose autoregressive language model as the "reader," relying on in-context learning (prompting) rather than task-specific fine-tuning.

System Architecture and Workflow
The developed system integrates dense retrieval with few-shot prompting to bridge the gap between information retrieval and natural language generation:

Retrieval with ColBERT: A pre-trained ColBERT (Contextualized Late Interaction over BERT) retriever is used to identify the most relevant passages from a large corpus for any given input question.

Contextual Prompt Construction: For each retrieved passage, the system searches the SQuAD training dataset to find similar passage/question/answer triplets. These triplets serve as "shots" or examples for the language model.

Few-shot Prompting: The final prompt is constructed by concatenating the SQuAD examples, the newly retrieved passage, and the target question. This prompt guides the autoregressive language model to generate a candidate answer.

Answer Scoring and Selection: Since multiple passages are retrieved, the system generates multiple candidate answers. These are scored and ranked to select the single most accurate response for the user's question.

Hyperparameter Optimization
A systematic grid search was conducted to optimize the performance of the few-shot OpenQA pipeline. The search focused on key parameters that influence both retrieval quality and generation accuracy:

Number of Retrieved Passages: Determining the optimal balance between providing enough context and avoiding prompt truncation.

Number of Few-shot Examples: Testing how many SQuAD triplets are necessary to "prime" the language model effectively.

Prompt Formatting: Evaluating different structures for the input string to maximize the model's reasoning capabilities.

Decoding Parameters: Tuning temperature and top-p sampling to ensure factual and concise answer generation.

Evaluation and Objectives
The primary goal is to develop an original system that successfully performs OpenQA without explicit reader training. This approach represents a significant step toward deploying QA technologies flexibly across new domains where labeled training data may be scarce. By leveraging ColBERT's efficient late interaction and the few-shot capabilities of modern language models, the system demonstrates a scalable method for knowledge retrieval and synthesis.
