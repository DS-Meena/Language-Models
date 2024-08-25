## Building a LSTM model to generate poems

### 1. Finding Data

To create a good model for generating love poems, you'll need a large dataset of poetry, preferably with a focus on love themes. Here are some sources you can consider:

- Project Gutenberg (https://www.gutenberg.org/): A large collection of free e-books, including poetry collections.
- PoetryFoundation (https://www.poetryfoundation.org/): Offers a vast collection of poems, including many about love.
- Kaggle Datasets: Search for "poetry" or "love poems" on Kaggle for pre-compiled datasets.
- Reddit r/OCPoetry: A subreddit where users share original poetry, which you could scrape (following Reddit's API rules).

I used [Poems from poetryfoundation.org](https://www.kaggle.com/datasets/ultrajack/modern-renaissance-poetry) dataset from kaggle.

### 2. Preprocessing the Data

Before training, you'll need to preprocess your data:

1. Clean the text by removing any irrelevant information or formatting.
2. Tokenize the poems into words or subwords.
3. Create sequences of fixed length for training.
4. Encode the sequences into numerical format.

### 3. Building the Model

For this task, I created a LSTM based language model using tensorflow and keras.

### 4. Training the Model

After compiling the model, train it on the poems dataset. Adjust the number of epochs and batch size as needed. You can also use early stopping and model checkpoints to prevent overfitting and save the best model.

### 5. Generating Poems

After training, you can generate new poems by:

1. Starting with a seed text.
2. Predicting the next word using the trained model.
3. Appending the predicted word to the seed text.
4. Repeating the process until you reach the desired length.

## Role of Each file

**preprocesssing.py**
- Cleans the text by removing extra whitespace and converting to lowercase
- Tokenizes the poems using Keras' Tokenizer
- Creates input sequences for training
- Pads the sequences to ensure uniform length
- Prepares the data (X and y) for training a text generation model

**text_generation.py**

This file has the `generate_poem` method, that generates a poem given a seed text and the number of words to generate.
It then iteratively predicts the next word based on the current sequence and appends it to the generated text.

**model.py**

In this, I create a sequential model with embedding and LSTM layers, which is a common architecture for text generation tasks.

