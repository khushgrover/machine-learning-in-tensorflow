# Tokenization on text data using Tensorflow and Keras

### **Tokenizer class**

```python
# importing tokenizer class
from tensorflow.keras.preprocessing.text import Tokenizer

# instantiating tokenizer class
tokenizer = Tokenizer(num_words = 100, oov_token="<OOV>")
```

**param num_words**: will take the 100 most common words and build a dictionary

**param oov_token**: words not included in the dictionary will be assigned this token. If this is not specified, the words not included in the dictionary will be excluded.

<hr>

### **Fitting text on Tokenizer**

```python
# fitting the tokenizer to sentences
tokenizer.fit_on_texts(sentences)

# see the dictionary created
word_index = tokenizer.word_index
```

**fit_on_texts**: automatically does preprocessing on text (lowercase, remove punctuation) and builds a dictionary _word_index_

<hr>

### **For converting the sentences to sequences:**

```python
sequences = tokenizer.texts_to_sequences(sentences)
```

### **Padding Sequences:**

```python
from tensorflow.keras.preprocessing.sequence import pad_sequences

padded = pad_sequences(sequences, padding='post', max_length=10, truncating='post')
```

**param padding**: by default does pre-padding of 0's, can be set to post-padding

**param max_length**: by default padding is done to the maximum length out of the sequences

**param truncating**: by default max_length truncates from the front, setting this to post truncates from the back
