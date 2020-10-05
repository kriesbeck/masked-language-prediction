# Masked language prediction
### Starting from a redacted pdf, can we guess the redactions?

This notebook uses the BertforMaskedLM model to predict the top 10 most likely words for a redacted token.  For each prediction, it outputs a probability of the predicted token in the output vector.

### Next steps
- How to identify redactions in pdf>txt conversion?
  - identify redaction indices
  - apply [MASK]s post-tokenization
- Tokens vs phrases 
  - https://stackoverflow.com/questions/61419089/use-bert-to-predict-multiple-tokens
  - How much (% of text) do we need to redact before it's difficult to predict?
- Can we exploit the size of redaction?  number of characters?
- Multi-token redactions
  - https://stackoverflow.com/questions/59435020/get-probability-of-multi-token-word-in-mask-position

### Resources
- https://arxiv.org/pdf/1706.03762.pdf 
- https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270
- Fine Tuning
  - https://huggingface.co/transformers/model_doc/bert.html#bertformaskedlm
  - https://mccormickml.com/2019/07/22/BERT-fine-tuning/

From the BERT paper (https://arxiv.org/pdf/1810.04805.pdf): 

A.3  Fine-tuning Procedure

For fine-tuning, most model hyperparameters are the same as in pre-training, with the exception of the batch size, learning rate, and number of training epochs.  The dropout probability was always kept at 0.1. The optimal hyperparameter values are task-specific, but we found the following range of possible values to work well across all tasks:

- Batch size: 16, 32
- Learning rate (Adam): 5e-5, 3e-5, 2e-5
- Number of epochs: 2, 3, 4
        
We  also  observed  that  large  data  sets  (e.g.,100k+  labeled  training  examples)  were  far less sensitive to hyperparameter choice than small datasets. Fine-tuning is typically very fast, so it is reasonable  to  simply  run  an  exhaustive  search over the above parameters and choose the model that performs best on the development set.
