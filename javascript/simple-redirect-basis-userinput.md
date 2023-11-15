Below Javascript function can be used as bookmarklet for getting an input from the user and redirecting to a webpage basis the user input

```javascript
javascript:(function() {
    let userInput = prompt("Please enter a search string: ");
        let url = "https://www.google.com/search?q=" + userInput;
        window.location.href = url;
})();
```

Example: Giving input as cats redirects to https://google.com/search?q=cats