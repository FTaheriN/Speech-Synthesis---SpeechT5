<img width="378" alt="image" src="https://github.com/FTaheriN/Speech-Synthesis---SpeechT5/assets/73983064/8664666f-9b56-41a5-9976-d38366f7e8bd">[SpeechT5](https://huggingface.co/docs/transformers/en/model_doc/speecht5) is finetuned for Persian text to speech gengration with the help of the [Common voice dataset](https://commonvoice.mozilla.org/en/datasets).
The Persian dataset is collected and half of the train set is used for finetuning and evaliation. The procedure taken to perform the task is as follows:

1. All text in the dataset are converted to Finglish by mapping persian characters through ASCII codes. This allows us to continue with the model's tokenizer as it is and there would be no need to add Persian characters as tokens to the tokenizer vocabulary.
<img width="378" alt="image" src="https://github.com/FTaheriN/Speech-Synthesis---SpeechT5/assets/73983064/2cd52682-7a85-40d7-85ec-a0c4211e7ca9">

2. Each text in the train set is then tokenized with SpeechT5 tokenizer.
3. Model's feature extractor is used to convert data's waveform to normalized signals and log-mel filter banks.
4. Speaker embeddings are axtracted from the speech by the help of speechBrain.
5. Tokenized text and speech features are then given to the trainer, after being collated in each batch.
The model is then finetuned for 25 epochs and evaluation results are printed in each epoch. Evaluation outputs are also available in the provided notebook. 
