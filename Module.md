# Module în Python — Ce Sunt și Cum se Importă

Acest document explică pe scurt ce sunt **modulele** în Python și cum se importă, inclusiv cu **alias**, folosind ca exemple `numpy`, `pandas`, `pygame`, `math` și `random`.

---

# 1. Ce Este un Modul?

Un **modul** este un fișier Python (sau o bibliotecă) care conține cod (funcții, clase, variabile) gata scris, pe care îl poți folosi în propriul program prin `import`, fără să-l rescrii.

---

# 2. Import Simplu

```python
import math

print(math.sqrt(16))
```

Output:

```
4.0
```

Explicație:

După `import math`, tot ce oferă modulul se accesează cu prefixul `math.`.

---

# 3. Import cu Alias (`as`)

```python
import numpy as np

array = np.array([1, 2, 3])
print(array)
```

Output:

```
[1 2 3]
```

Explicație:

`as` dă modulului un **nume mai scurt**, folosit apoi în loc de numele complet — `np` în loc de `numpy`.

---

# 4. Module Folosite Frecvent

## `numpy` — Calcule Numerice și Vectori/Matrici

```python
import numpy as np
```

## `pandas` — Lucrul cu Tabele de Date

```python
import pandas as pd
```

(vezi [Pandas-csv.md](Pandas-csv.md))

## `pygame` — Creare de Jocuri și Grafică

```python
import pygame
```

(vezi [Pygame.md](Pygame.md))

## `math` — Funcții Matematice

```python
import math
```

## `random` — Generare de Valori Aleatoare

```python
import random
```

(vezi [Random.md](Random.md))

---

# 5. Rezumat

* Un **modul** este cod deja scris, reutilizabil prin `import`
* `import modul` → se folosește cu `modul.ceva`
* `import modul as alias` → se folosește cu `alias.ceva`, un nume mai scurt
* Aliasuri des întâlnite: `numpy as np`, `pandas as pd`
* `pygame`, `math`, `random` se importă de obicei fără alias
