# kanji-list-for-anki
This Javascript will parse a string containing kanji and return a list of them with the keyword, other definitions, onyomi, and kunyomi.

## Usage

Place the `_kanjidict.js` file into your `collection.media` folder.

Put this code in your Anki card where you want the kanji list to appear:
```
<div id="kanjilist"></div>
```

And then put this code at the bottom of your card.
Where I've got `kanji:Sentence`, make sure this references the field where your Japanese sentence is.
```
<script>
	function loadScript(src, callback) {
		var script = document.createElement('script');
		script.src = src;
		script.onload = callback;
		document.head.appendChild(script);
	}

	loadScript('_kanjidict.js', function() {
		//kanji list
		document.getElementById('kanjilist').innerHTML = listKanji("{{kanji:Sentence}}")
	});
</script>
```

(I delay the execution of the script because, on iOS at least, Javascript tends to break on the first card displayed.)

## Result
It should look something like this:

![example of kanji list](./kanji-list-example.png)