# Google DeepMind: Train a Small Language Model (Challenge Lab) || **GSP531**

**Command:**

```bash
if not ngram_model:
      return tokenizer.join_text(generated_tokens)
    
    context_size=len(tokenizer.character_tokenize(next(iter(ngram_model))))

    for _ in range(n_tokens):
      if len(generated_tokens)<context_size:
        break

      context_tokens=generated_tokens[-context_size:]
      context_key=tokenizer.join_text(context_tokens)

      if context_key not in ngram_model:
        break
      
      next_token_distribution = ngram_model[context_key]

      if not next_token_distribution:
        break
      
      next_token=""

      if sampling_mode=='random':
        tokens=list(next_token_distribution.keys())
        probabilities=list(next_token_distribution.values())

        next_token=random.choices(tokens, weights=probabilities,k=1)[0]
      elif sampling_mode=="greddy":
        next_token=max(next_token_distribution,key=next_token_distribution.get)
      else:
        raise ValueError(f"Unspported sampling_mode: '{sampling_mode}")
      
      generated_tokens.append(next_token)
```

``` bash
start=0
    while start<len(sequence):
      end=start+max_length
      subsequences.append(sequence[start:end])
      if end>=len(sequence):
        break
      start=end-n_overlap
```

```bash
for text in dataset:
      token_ids=tokenizer.encode(text)
      segments=segment_encoded_sequence(token_ids,segmentation_length,n_overlap)
      encoded_tokens.extend(segments)
```
