Er zijn drie basismanieren om woordgrenzen te gebruiken in een regexvervanging:

  1. het einde van woorden veranderen
  1. het begin van woorden veranderen
  1. alleen hele woorden veranderen.

### Het einde van woorden veranderen

- Als je het woord `'lopen'` in `'loopt'` wilde veranderen, zou een standaard regexvervanging werken. Je zou `'pen'` kunnen vervangen door `'opt'`.

    ```python
    import re
woord = re.sub('pen', 'opt', 'lopen')
    ```

- Dit zou echter niet werken met het woord `'openwerpen'`. Alle `'pen'` patronen zouden worden vervangen door `'opt'` om `'ooptwerpt'` op te leveren. De enige `'pen'` die je wilt vervangen, is echter die aan het einde.

- In dergelijke gevallen kun je het **metateken** `\b` gebruiken, wat **woordgrens** betekent. Dus in plaats van te zoeken naar het `'pen'` patroon, zoek je naar het `'pen\b'` patroon. Dit zal Python vertellen om het patroon alleen aan het einde van een woord te vervangen.

- Je gebruikt nu de `\`, wat een **escape-teken** is, in je string. Daarom moet je Python vertellen het te behandelen als een **letterlijke tekenreeks** om vreemd gedrag te voorkomen. Dit betekent gewoon dat je een `r` voor de aanhalingstekens plaatst: `r'pen\b'`

- Zet dit allemaal samen in een werkende coderegel als volgt:

    ```python
    import re
woord = re.sub(r'pen\b ', 'opt', 'openwerpen')
    ```

### Het begin van woorden veranderen

- Hetzelfde systeem kan worden gebruikt om te detecteren wanneer een patroon aan het begin van een woord staat. Dus om `'oploop'` in `'afloop'` in plaats van in `'oploaf'` te veranderen zou je het volgende kunnen doen:

    ```python
    import re
woord = re.sub(r'\bo', 'af', 'oploop')
    ```

- Door de `\b` aan het begin van het patroon te gebruiken, controleert Python of het patroon aan het begin van het woord staat.

### Hele woorden veranderen

- Als je een heel woord wilt wijzigen, gebruik je eenvoudig het metateken `\b` aan het begin en einde van het patroon.

- Dus om `'De man leidde het team'` in `'De vrouw leidde het team'` te veranderen, zou je het volgende doen:

    ```python
    import re
zin = 'De man leidde het team'
zin = re.sub(r'\bman\b', 'vrouw', zin)
    ```
