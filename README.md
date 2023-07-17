# extract-text-from-an-image-using-JavaScript
extract text from an image Many note-taking apps nowadays offer to take a picture of a document and turn it into text. I was curious and decided to dig a little deeper to see what exactly was going on.

Having done a little research I came across Optical Character Recognition — a field of research in pattern recognition and AI revolving around precisely what we are interested in, reading text from an image. There is a very promising JavaScript library implementing OCR called tesseract.js, which not only works in Node but also in a browser — no server needed!

I would like to focus on working out how to add tesseract.js to an application and then check how well it does its job by creating a function to mark all of the matched words in an image.

esseract.js
To add tesseract to a project we can simply type this in the terminal:

npm install tesseract.js
After importing it into our codebase everything should work as expected. At least according to the package’s docs. In reality, though, I kept getting an error about missing worker.js file, and since the docs and very thorough googling wasn’t of much help I used a workaround. I copied a file called worker.min.js from node_modules/tesseract.js, and pasted it to my public folder from which I serve my static files. After that I changed the path to the worker inside tesseract like so:

tesseract.workerOptions.workerPath = ‘http://localhost:8080/worker.min.js';
and everything worked correctly.

Application
Let’s create a simple application to recognize text in an image. We would like it to render the image twice. Once to show the user their original image of choice and once to highlight the words that were matched. Finally, we would also like for our app to display for the user the progress it has made thus far (at all times).
