# Masked language prediction
### Starting from a redacted pdf, can we guess the redactions?

This notebook uses the BertforMaskedLM model to predict the top 10 most likely words for a redacted token.

### Next steps
- How to identify redactions in pdf>txt conversion?
  - identify redaction indices
  - apply [MASK]s post-tokenization
- Tokens vs phrases 
  - https://stackoverflow.com/questions/61419089/use-bert-to-predict-multiple-tokens
  - How much (% of text) do we need to redact before it's difficult to predict?
- Can we exploit the size of redaction?  number of characters?
