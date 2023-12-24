<h3>Machine Translation Project</h3>
<ul>
<li>1. Get the dataset which is in the form - German text followed by tab then followed by english text and then a new line following the same pattern in the next lines. It is notable that there is punctauation, and the text is ordered by length - with shorter sentences on the top followed by longer sentences towards the end.</li>
  <li>2. First step is to load the file which we do by a load_file function - also ensuring the encoding remains intact and we dont lose any special characters in the german text.</li>
  <li>3. Then the loaded file must be split by lines</li>
  <li> 4. The lines need to split by tab</li>
  <li>5. Ultimately - we get a pattern like this : [ ['hi' 'halo' ] , ['good morning' 'Guten Morgen'] ]</li>
  <li>6. Clean the text - line wise - then phrase wise - removing non printable characters, punctuation etc</li>
  <li>7. Save the cleaned text as a pkl file</li>
  <li>8. Load the pkl file - split into train, test set and save those sets as pkl file</li>
  <li>9. Load the train test pkl files</li>
  <li>10. Tokenize the data with keras</li>
  
</ul>
<i>Removed the existing pkl files - after discovering the error in clean function - pkl files would have been affected and must be having wrong data</i>

<li>Discovered the error in the clean function , brought back the pkl file. The next step after cleaning and splitting is to tokenize</li>

<p><b>Tokenize:</b> Tokenizer is responsible to map words to unique integer values. In this method the tokenizer creates and returns token objects instead of integer encoding. The tokenizer object is then added as a parameter in another method to create and pad the length of the integer encoded sequence.</p>

<p><b>Encode method</b>: After the input is encoded and padding is done, this process is followed by another method which integer encodes the output into one hot encoding and then reshapes the output in the structure of it's input sequence.</p>

<h3> THEORETICAL INFORMATION - WHY ONE HOT ENCODING WAS UNNECESSARY</h3>
<p>The tokenizer from keras created a tokenizer object which takes in textual data and then maps it to a unique integer and the padding ensures that the size remains constant.
Now, the tokenizer maps each token to a unique integer and if we look at the text as a whole - into tokens - converted into unique integers - we get a sequence of integers.So, this sequence of integers is taken as an input by the word embedding layer which in turn converts this sequence of integers into a dense vector representation.
Every unique integer that is representing a token is replaced by a dense vector embedding.

All in all - word embedding layer does not take raw text or integer values as input - It takes a sequence of integers as an input which represent tokens of a text and then converts that sequence of integers into a dense vector representation.</p>

<p><b>NOTE: <i>There was a slight oversight. This tutorial is not using a word embedding layer. It is just tokenizing and padding the text and then instead of passing it to a word embedding layer, it is being passed to a one hot encoding method - to get vector representation - although sparse but still those vector representation would be passed into the neural network as input.</i></b></p>

<h5>Passing input to the model - encoder decoder architecture of LSTM </h5>
<p>
  <li>LSTM is a recurrent neural network which is popularly used for sequential data - mainly for NLP tasks</li>
  <li>In an encoder the input is given in the form of a sequence of integers/ one hot encoded vectors or word embeddings - dense vectors. Encoder processes the input and then gives an output - context vector</li>
  A context vector is similar to a dense vector representation as it is also of a fixed length and describes the information from the entire sequence of data.
  <li>The context vector is passed as an input to the decoder which gives a sequence of elements as an output</li>
  Decoder generates output sequence by predicting one element at a time. During the training the output sequence from the decoder is compared to the target sequence to compute the losss, allowing the model to learn from errors and improve predictions.
  During inference (generating predictions on new data) the decoder generates the output sequence based on the learned parameters.
</p>

<p><b>Output of decoders: </b>  Often in the form of probabilities across the vocabulary. Each position in the output sequence could have a probability distibution over the vocabulary.</p>

<h5>UNDERSTANDING THE MODEL PARAMETERS AND THEIR SIGNIFICANCE</h5>
<p> In many sequence-to-sequence tasks, like language translation or sequence generation, trainX often represents input sequences as sequences of integers (tokenized or encoded input data), while trainY consists of sequences of sparse vectors, typically in a one-hot encoded format representing the target sequences.

trainX: Sequence of integers representing the input data.
trainY: Sequence of sparse vectors, often one-hot encoded representations of the target data.
The usage of these different formats for trainX and trainY aligns with the requirements of sequence-to-sequence models.

Input Sequence (trainX): Sequence of integers representing words or tokens in the input language. These integers often correspond to indices in a vocabulary or have been encoded using tokenization methods.

Target Sequence (trainY): Sequence of sparse vectors representing the target output. In natural language processing tasks, these sparse vectors often use one-hot encoding, where each vector represents a word/token in the target language vocabulary.

During training, the model uses the input-output pairs (trainX and trainY) to learn how to map input sequences to output sequences, adjusting its parameters (weights) to minimize the difference between predicted outputs and actual target outputs.

The code provided (model.fit(trainX, trainY, ...)) aims to train the model using this input-output data pair, allowing the model to learn the mapping from input sequences to sparse vector representations of the output sequences. This process enables the model to generate suitable predictions for unseen input sequences during inference.</p>

