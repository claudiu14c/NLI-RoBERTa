# NLI-RoBERTa
Fine-tuning a RoBERTa based model for Natural Language Inference

## The model
This is a model for Natural Language Inference. It uses a pre-trained RoBERTa model. RoBERTa has the same architecture as BERT, but uses a BPE tokenizer instead. Some hyperparameters and the pre-training objectives are also changed. RoBERTa is not pre-trained using the Next Sentence Prediction task.

A classification head consisting of a dense, a drop-out, and another dense layer is added on top of this. The pre-trained RoBERTa model produces encodings of the input. The classification head takes them and procuses the probabilities of each class (class 0 -> no implication, class 1 -> hypothesis implies premise).

This entire model has been fine-tuned on our data set. Both the parameters of the RoBERTa base model and those of the untrained Classification Head have been changed.

## Credits

The architecture was selected based on a similar model's performance on the [RTE benchmark](https://paperswithcode.com/sota/natural-language-inference-on-rte). The code is inspired by [this article](https://pchanda.github.io/Roberta-FineTuning-for-Classification/), where a model with the same architecture was fine-tuned for classifying molecules.

## Fine-tuned model location

Post fine-tuning, the model has been stored on the Cloud at [this location](https://drive.google.com/file/d/1-IJSt2HGH9Dqbu6NBuHr61ndV1r4g-3H/view?usp=sharing).  It can be downloaded and used directly in the notebook, but uploading it to Colab takes more than 15 minutes. Hence a link to Google Drive was used in the code for loading the model during testing. However, if one wants to test this notebook, this link needs to be replaced by the location of the downloaded model on their machine.

###Pre-requisites for fine-tuning a RoBERTa model with a classification head on top
+++++++++++++++++++++++++++++++++++++++

*   The training and evaluation data should be in csv files with 3 columns  labeled 'premise', 'hypothesis', and 'label'.
*   The traning data csv should be called 'train.csv', and the evaluation data should be called 'dev.csv'. Both should be loaded into Colab. Alternatively, one can modify the *tr_location* and *dev_location* variables, which hold both the location and name of the csv files. Links to Google Drive can be used.
*   The final evaluation can be done either on the same fine-tuned model or on another model loaded from the file sytem or Google Drive. Since this notebook had already been run, the fine-tuned model is currently loaded from Google Drive. If one wants to test the evaluation step, please download the fine-tuned model from [here](https://drive.google.com/file/d/1-IJSt2HGH9Dqbu6NBuHr61ndV1r4g-3H/view?usp=sharing) and change the content of the variable *MODEL_PATH* to the location of the downloaded model.
* A GPU environment must be used for training.

###Pre-requisites for the demo

*   The test data should be a csv file with 2 columns with the labels 'premise' and 'hypothesis'.
*   The test data csv should be called 'test.csv' and should be loaded into Colab. Alternatively, one can modify the *test_location* variable, which holds both the location and name of the csv file. Links to Google Drive can be used.
*   The fine-tuned model is currently loaded from Google Drive. If one wants to test this notebook, please download the model from [here](https://drive.google.com/file/d/1-IJSt2HGH9Dqbu6NBuHr61ndV1r4g-3H/view?usp=sharing) and change the content of the variable *PATH* to the location of the downloaded model.
* The usage of a GPU runtime is encouraged for large test files, but it is not needed for less than 1000 test samples.

