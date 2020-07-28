Hay tres formas básicas de usar límites de palabras en una sustitución de regex:

  1. cambiando el final de las palabras
  1. cambiando el comienzo de las palabras
  1. cambiando palabras enteras solamente.

### Cambiando el final de las palabras

- Si quieres cambiar la palabra `'caminar'` a `'caminando'`, entonces una sustitución estándar de regex funcionaría. Podrías simplemente reemplazar `'r'` con `'ndo'`.

    ```python
    import re
    palabra = re.sub('r', 'ndo', 'caminar')
    ```

- Sin embargo, esto no funcionaría con la palabra `'colorear'`. Todos los patrones `'r'` serían reemplazados por `'ndo'` para dar `'colondoeando'`. Sin embargo, el único `'r'` que quieres reemplazar es el que hay al final.

- En tales casos puedes usar el **meta carácter** `\b` que significa **límite de palabra**. Así que, en lugar de buscar el patrón `'r'`, buscas el patrón `'r\b'`. Esto le dirá a Python que sólo sustituya el patrón al final de una palabra.

- Ahora estás usando el `\`, que es un **carácter de escape**, en tu cadena. Por lo tanto, necesitas decirle a Python que lo trate como un **literal de cadena** para evitar comportamientos extraños. Esto simplemente significa poner una ``r` antes de las comillas: `r'r\b'`

- Coloca todo esto junto en una línea de código funcional como este:

    ```python
    import re
    palabra = re.sub(r'r\b', 'ndo', 'colorear')
    ```

### Cambiando el comienzo de las palabras

- Se puede usar el mismo sistema para detectar cuándo un patrón está al comienzo de una palabra. Entonces, para cambiar `'revelar'` a `'develar'` en lugar de `'develad'` podrías hacer lo siguiente:

    ```python
    import re
    palabra = re.sub(r'\br', 'd', 'revelar')
    ```

- Usando la `\b` al principio del patrón hace que Python compruebe que el patrón está al principio de la palabra.

### Cambiando palabras completas

- Para cambiar una palabra completa, simplemente utiliza el meta carácter `\b` al principio y al final del patrón.

- Así que para cambiar `'Él lideró el equipo'` a `'Ella dirigió el equipo'`, harías lo siguiente:

    ```python
    import re
    oracion = 'Él lideró el equipo'
    oracion = re.sub(r'\bÉl\b', 'Ella', oracion)
    ```
