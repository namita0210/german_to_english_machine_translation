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

