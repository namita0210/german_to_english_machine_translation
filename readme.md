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
<p>The tokenization needs to be done separately for both the english vocab and german vocab - in which all words are to be mapped with integers.
But I think due to the pkl file there is some problem differentiating between the columns - 0 and 1 . 
0 : English and 1: German respectively. So in this branch I am going to omit the step of saving a pkl file and directly tokenize the cleaned text.</p>

