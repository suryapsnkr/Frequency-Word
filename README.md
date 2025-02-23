# FrequencyOfWord
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Word Frequency Counter</title>
    <link rel="stylesheet" type="text/css" media="screen" href="https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css">
    <link rel="stylesheet" href="https://pyscript.net/releases/2024.1.1/core.css">
    <script type="module" src="https://pyscript.net/releases/2024.1.1/core.js"></script>
</head>

<body>
    <center><br>
        <textarea id="input_text" placeholder="Enter Your Text"></textarea><br><br>

        <button id="run" type="button" class="button is-primary">Count</button>
        <button id="clear" type="button" class="button is-danger">Clear</button><br><br>

        <p id='output'></p>
    </center>

    <script type="py">
        from js import document
        from pyodide.ffi import create_proxy  # ✅ Fix Pyodide event issue

        def clear(event):
            document.getElementById("input_text").value = ""
            document.getElementById("output").innerText = ""

        def count(event):
            input_text = document.getElementById("input_text").value
            output = document.getElementById("output")

            words = input_text.split()
            unique_words = set(words)  # ✅ More efficient way to find unique words
            frequencies = [f"{word}={words.count(word)}" for word in unique_words]

            output.innerText = ", ".join(frequencies)  # ✅ Correct way to display results

        # ✅ Fix Pyodide event issues
        count_proxy = create_proxy(count)
        clear_proxy = create_proxy(clear)

        document.getElementById("run").addEventListener("click", count_proxy)
        document.getElementById("clear").addEventListener("click", clear_proxy)
    </script>
</body>
</html>

    lS = ", ".join(map(str, f))
    output.write(lS)

</py-script>
</center></body>
</html>
