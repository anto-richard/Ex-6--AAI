<H3>Name : Anto Richard. S</H3>
<H3>Reg No : 212221240005</H3>
<H3>EX.NO : 6</H3>
<H3>DATE: 30.04.2024</H3>
<H1 ALIGN =CENTER>Implementation of Semantic Analysis</H1>

## Aim :

To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques.

## Algorithm :

- `Step 1:` Import the nltk library.<br>

- `Step 2:` Download the `'punkt'`, `'wordnet'`, and `'averaged_perceptron_tagger'` resources.<br>

- `Step 3:`Accept user input for the text.<br>

- `Step 4:`Tokenize the input text into words using the `word_tokenize` function.<br>

- `Step 5:`Iterate through each word in the tokenized text.<br>

    -	Perform part-of-speech tagging on the tokenized words using `nltk.pos_tag.`<br>
    
    -	Print each word along with its corresponding part-of-speech tag.<br>
    
    -	For each verb , iterate through its synsets (sets of synonyms) using `wordnet.synsets`(word).<br>
    
    -	Extract synonyms and antonyms using `lemma.name()` and `lemma.antonyms()[i].name()` respectively.<br>
    
    -	Print the unique sets of synonyms and antonyms.
      
## Program :

```python

#importing packages :

! pip install nltk
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
```

```python

#reading content from file:

f = open("/content/samplefile.txt", "r")
sentences = f.readlines()
f.close()
```

```python

verbs = [[] for _ in sentences]
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)

  # Tokenize the sentence into words:

  words = word_tokenize(sentence)

  # Identify the parts of speech for each word:

  pos_tags = nltk.pos_tag(words)

  # Print the parts of speech:

  for word,tag in pos_tags:
    print(word,"->",tag)

    # Save verbs:

    if tag.startswith('VB'):
      verbs[i].append(word)
  i+=1
  print("\n\n")
```

```python

# Identify synonyms and antonyms for each word:

print("Synonyms and Antonymns for verbs in each sentence:\n")
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)
  pos_tags = nltk.pos_tag(verbs[i])
  for word,tag in pos_tags:
    print(word,"->",tag)
    synonyms = []
    antonyms = []
    for syn in wordnet.synsets(word):
      for lemma in syn.lemmas():
        synonyms.append(lemma.name())
        if lemma.antonyms():
          for antonym in lemma.antonyms():
            antonyms.append(antonym.name())

    # Print the synonyms and antonyms:

    print("Synonyms:",set(synonyms))
    print("Antonyms:", set(antonyms) if antonyms else "None")
    print()
  print("\n\n")
  i+=1
```

## Output :

### Sample Sentence from 'samplefile.txt' :
### Words and the respective POS-Tags :

![img1](https://github.com/anto-richard/Ex-6--AAI/assets/93427534/70e27c5c-4a34-4123-bd77-8aeac548d5a7)

### Synonyms and Antonyms for verbs in each sentence :

![img2](https://github.com/anto-richard/Ex-6--AAI/assets/93427534/c11e35d6-9433-4fa2-b28e-e96adf2b90a9)

## Result :

Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.

