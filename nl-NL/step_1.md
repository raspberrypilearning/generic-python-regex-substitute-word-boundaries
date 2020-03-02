Er zijn drie basismanieren om woordgrenzen te gebruiken in een regexvervanging:

  1. het einde van woorden veranderen
  1. het begin van woorden veranderen
  1. alleen hele woorden veranderen.

### De uiteinden van woorden wijzigen

- Als je het woord `'gelopen'` tot `'gelopen'`wilde veranderen, zou een standaard regexvervanging werken. Je zou `'ed'` kunnen vervangen door `'ing'`.

    ```python
    import re
    word = re.sub ('ed', 'ing', 'walk')
    ```

- Dit zou echter niet werken met het woord `'bewerkt'`. Alle `'ed'` patronen zouden worden vervangen door `'ing'` om `'ingiting'`. De enige `'ed'` die u wilt vervangen, is echter die aan het einde.

- In dergelijke gevallen kunt u het **metateken** `\ b` wat **woordgrens betekent**. Dus in plaats van te zoeken naar het `'ed'` patroon, zoekt u naar het `'ed \ b'` patroon. Dit zal Python vertellen om het patroon alleen aan het einde van een woord te vervangen.

- Je gebruikt nu de ``\ `, wat een ** escape-teken ** is, in je string. Daarom moet je Python vertellen het te behandelen als een ** letterlijke tekenreeks ** om vreemd gedrag te voorkomen. Dit betekent gewoon dat u een``r`voor de aanhalingstekens plaatst:`r'ed \ b'`

- Zet dit allemaal samen in een werkende coderegel als volgt:

    ```python
    import re
    word = re.sub (r'ed \ b ',' ing ',' edited ')
    ```

### Het begin van woorden veranderen

- Hetzelfde systeem kan worden gebruikt om te detecteren wanneer een patroon aan het begin van een woord staat. Dus om `'onbespannen'` in `'restrung'` plaats van `'restrreg'`zou je het volgende kunnen doen:

    ```python
    import re
    word = re.sub (r '\ bun', 're', 'unstrung')
    ```

- Door de `\ b` aan het begin van het patroon te gebruiken, controleert Python of het patroon aan het begin van het woord staat.

### Hele woorden veranderen

- Als u een heel woord wilt wijzigen, gebruikt u eenvoudig het metateken `\ b` aan het begin en einde van het patroon.

- Dus om `te veranderen 'De man beheerde het team'` tot `'De vrouw beheerde het team'`, zou je het volgende doen:

    ```python
    import re
    zin = 'De man beheerde het team'
    zin = re.sub (r '\ bman \ b', 'woman', zin)
    ```
