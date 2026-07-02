# Modulul `pygame` — Definiții de Bază


---

## 1. Ce este `pygame`

`pygame` este o **bibliotecă externă** (nu vine built-in cu Python) folosită pentru a crea jocuri 2D: gestionează fereastra grafică, desenarea pe ecran, input de la tastatură/mouse, sunete și coliziuni.

```python
import pygame
```

---

## 2. `pygame.init()`

Inițializează **toate modulele interne** ale pygame (display, sound mixer, font, joystick etc.), pregătindu-le pentru utilizare.

```python
import pygame
pygame.init()
```

fără `init()`, module precum sunetul sau fonturile nu funcționează corect.

---

## 3. `pygame.display.set_mode()`

Creează și dimensionează **fereastra jocului**. Primește un tuplu `(lățime, înălțime)` în pixeli.

```python
ecran = pygame.display.set_mode((800, 600))
```

aceasta este metoda standard prin care se setează dimensiunea display-ului.

---

## 4. Assets Proprii (imagini, sunete, fonturi)

`pygame` permite încărcarea de fișiere proprii — imagini, sunete, fonturi — pentru personaje, fundaluri, efecte sonore etc.

```python
imagine = pygame.image.load("nava.png")
sunet = pygame.mixer.Sound("laser.wav")
font = pygame.font.Font("font_personalizat.ttf", 32)
```

 pygame nu vine cu grafică sau sunete fixe; totul se încarcă din fișiere proprii.

---

## 5. Gravitația

`pygame` **nu are un sistem de fizică sau gravitație încorporat**. Nu există o funcție/setare de tip `pygame.set_gravity()`. Dacă vrei gravitație într-un joc, trebuie să o **simulezi manual**, de obicei crescând viteza pe verticală la fiecare cadru:

```python
viteza_y = 0
gravitatie = 0.5

viteza_y += gravitatie
pozitie_y += viteza_y
```

 gravitatea nu este o funcție a modulului pygame, ci cod scris de programator.

---

## 6. Bucla de bază a unui joc pygame

```python
import pygame

pygame.init()
ecran = pygame.display.set_mode((640, 480))
ruleaza = True

while ruleaza:
    for eveniment in pygame.event.get():
        if eveniment.type == pygame.QUIT:
            ruleaza = False

    ecran.fill((0, 0, 0))
    pygame.display.flip()

pygame.quit()
```

---

## 7. Rezumat

| Afirmație | Adevărat/Fals | De ce |
|---|---|---|
| `display.set_mode()` setează dimensiunea ferestrei | ✅ Adevărat | funcție standard pygame |
| pygame îți permite să schimbi gravitatea jocului | ❌ Fals | gravitatea nu e built-in, se implementează manual |
| poți folosi propriile assets (imagini/sunete) | ✅ Adevărat | `pygame.image.load()`, `pygame.mixer.Sound()` etc. |
| `init()` inițializează toate modulele pygame | ✅ Adevărat | pregătește display, sunet, font etc. |