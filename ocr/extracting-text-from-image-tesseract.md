## Extracting text from image

### Command to install Tesseract in terminal
```shell
brew install tesseract
```

### Command usage
```shell
tesseract image.png output.txt
```

### How I use
I generally use this along with my find command to get the text extracted from my latest screenshot (stored in Desktop folder by default)
```shell
find . -type f -mmin -5 -iname "*.png" -exec tesseract {} output.txt \;
```


The above command finds all files modified in the last 5min matching the pattern `*.png` and executes the command tesseract on the output of the command file
