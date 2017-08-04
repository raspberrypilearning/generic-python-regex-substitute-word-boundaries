- There are three basic ways of using word boundaries in a regex substitution:

  1. changing the end of words
  1. changing the beginning of words
  1. changing whole words only.
  
### Changing the end of words

- If you wanted to change the word `walked` to `walking` then a standard regex substitution would work. You could just replace `ed` with `ing`.

	```python
	import re
	word = re.sub('ed', 'ing', 'walked')
	```

- This would not work with the word `edited` though. All the `ed` patterns would be replace with `ing` to give `ingiting`. The only `ed` that wants to be replaced is the one at the end.

- Here you can use the **metacharacter** `\b` which means **word boundary**. So instead of searching for the `ed` pattern, you search for the `ed\b` pattern, which means only when it is at then end of a word.

- Because you are now putting the `\` which is an escape character, into your string, you need to tell Python to treat it as a **string literal**, to avoid behaviour. This just means putting an `r` before the quotes - `r'ed\b'

- This will now work:

	```python
	import re
	word = re.sub(r'ed\b', 'ing', 'edited')
	```

### Changing the beginnings of words.

- The same system can be used to detect when the pattern is at the beginning of a word. So to change `unstrung` to `restrung` rather than `restrreg`you could do the following:

	```python
	import re
	word = re.sub(r'\bun', 're', 'unstrung')
	```

- With the `\b` at the beginning of the pattern, it checks that the pattern is at the start of the word.

### Changing whole words.

- To change a whole word, simply use the `\b` metacharacter at the start and end of the pattern.

- So to change 'The man managed the team' to 'The woman managed the team', you would do the following:

	```python
	import re
	sentence = 'The man managed the team'
	sentence = re.sub(r'\bman\b', 'woman', sentence)
	```
