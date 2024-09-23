---
---
# NLTK

→ Plein de parser sur nltk

# LLMs

## Benchmarks & Leaderboards

Pour les modèles de chat :

https://chat.lmsys.org/?leaderboard

Pour les modèles ouverts : 

https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard

![tokenization1.webp](https://prod-files-secure.s3.us-west-2.amazonaws.com/51bb4b15-01f5-4b17-8e78-4c910f77218d/abfa9739-b5fd-46a3-9429-8ad637b2f7d0/tokenization1.webp)

## [Embeddings](https://geoffrey-geofe.medium.com/tokenization-vs-embedding-understanding-the-differences-and-their-importance-in-nlp-b62718b5964a)

In order to represent language in a space understandable by machines, we use vectorized representation of the context they are found in

> *You know a word by the company that it keeps*
> 

they are several way of representing this information : 

### static embeddings

Static models (like Word2Vec or GloVe) represent one token given all its neighbours in a given training dataset. The embedding is the same for one token in all context after training.

### dynamic embeddings

With the attention mechanism, the position of token in the context take extra importance. With this additionnal information, the token representation will change in each context it’s seen in. There is then multiple embedding for the same token.

Consider the following two sentences:

1. "My father is a bank teller"
2. "The river bank has been polluted."

In these two sentences, static word embeddings like word2vec will give the word "bank" the same vector.

Dynamic embeddings (from a BERT kr a DNN in general) will give two 
different vectors for the same word because it has two different 
contexts.

This is what's meant by context: the embedding is contextual at prediction time.

The breakthrough of contextualized embedding happened in 2015-2017 with ELMO and ULMFiT

## Tokenizers

They are a first model that split textual (or sound) data into vectors that can be processed by a machine. A good explanation [here](https://docs.mistral.ai/guides/tokenization/). 

![1_o1NcWzyBrE7OZXmOoIbebA.webp](https://prod-files-secure.s3.us-west-2.amazonaws.com/51bb4b15-01f5-4b17-8e78-4c910f77218d/ae10abe7-5f3f-4c24-a859-051a18dea4ca/1_o1NcWzyBrE7OZXmOoIbebA.webp)

- **Byte Pair Encoding (BPE)**
    
    In this algorithm, the first step, assumes all unique characters to be an initial set of 1 character long [n-grams](https://en.wikipedia.org/wiki/N-grams) (i.e.  initial "tokens"). Then, successively the most frequent pair of adjacent characters is merged into a new, 2-character long n-gram and all instances of the pair are replaced by this new token. This is repeated until a vocabulary of prescribed size is obtained.
    
- **SentencePiece**
    
    
- [**Difference between the two**](https://www.activeloop.ai/resources/glossary/sentence-piece/)
    
    BPE is a data compression algorithm that iteratively merges the most frequent pairs of characters in a text corpus to create a new symbol. This process continues until a predefined vocabulary size is reached. WordPiece, on the other hand, is an extension of BPE that focuses on optimizing the likelihood of the training data by iteratively selecting the most frequent subword pairs. The main difference between the two is that WordPiece optimizes for the likelihood of the training data, while BPE optimizes for character pair frequency
    

### Initialization

In order to change the weights of the neural network, you first have to initialize vectors