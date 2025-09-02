# 1. Preprocesory CSS (Sass i SCSS)

Preprocesor CSS to narzędzie, które rozszerza zwykły CSS o nowe możliwości (zmienne, nesting, mixiny, funkcje). Kod pisany w Sass/SCSS **musi być skompilowany** do zwykłego CSS, bo przeglądarka nie rozumie Sass/SCSS.

Przykład 1 (Sass):
```
nav
  ul
    li
      a
        color: red
        &:hover
          color: blue



```
Przykład 2 (SCSS):
```
nav {
  ul {
    li {
      a {
        color: red;
        &:hover {
          color: blue;
        }
      }
    }
  }
}

```

1. Zmienne 
Zmienne w SCSS pozwalają **przechowywać wartości** (np. kolory, rozmiary, odstępy).

```
// Definicje zmiennych
$primary: #3498db;
$secondary: #2ecc71;
$spacing: 20px;

header {
  background: $primary;
  padding: $spacing;
}

footer {
  background: $secondary;
  padding: $spacing / 2;
}

```

2. Nesting (zagnieżdżanie)
 Nesting pozwala pisać CSS w strukturze przypominającej HTML. Dzięki temu nie trzeba powtarzać całych selektorów
```
<nav>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">Kontakt</a></li>
  </ul>
</nav>

```
```
nav {
  ul {
    li {
      a {
        color: blue;
        &:hover {
          color: red;
        }
      }
    }
  }
}
```
Przykład 2:

```
<section class="banner">
  <h1>Witaj</h1>
  <p>Opis strony</p>
</section>
```

```
.banner {
  h1 {
    font-size: 32px;
    color: darkblue;
  }
  p {
    color: gray;
    font-style: italic;
  }
}

```

# 3. Mixins
**Wyjaśnienie:** Mixin to coś w rodzaju „funkcji dla CSS” – zapisujesz fragment stylu raz, a potem wstawiasz go w wielu miejscach przy pomocy @include. Możesz też przekazywać parametry.

```
<button class="btn">Kliknij</button>
<button class="btn danger">Usuń</button>
```

````

@mixin btn($bg) {. $bg - to zmienna ktora użyta jest w background:
  background: $bg;
  color: #fff;
  padding: 10px 20px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
}

.btn {
  @include btn(blue);

  &.danger {
    @include btn(red);
  }
}
````


Kolejny przykład mix

```
<h1 class="title">Nagłówek responsywny</h1>
<p class="text">To jest tekst, który zmienia rozmiar w zależności od ekranu.</p>
```

```
// Mixin z parametrami
@mixin responsive-font($small, $large) {
  font-size: $small;

  @media (min-width: 768px) {
    font-size: $large;
  }
}

// Użycie
.title {
  @include responsive-font(24px, 40px);
  font-weight: bold;
  color: #333;
}

.text {
  @include responsive-font(14px, 18px);
  color: #555;
}

```


4. Funkcje
Funkcje w SCSS mogą być **wbudowane** (np. lighten, darken, mix) lub **własne** (@function). Umożliwiają wykonywanie obliczeń, operacji na kolorach, tekstach czy liczbach.
```

<button class="btn">Kup teraz</button>
```

```

$primary: #3498db;

.btn {
  background: $primary;
  padding: 12px 24px;
  color: #fff;
  border-radius: 8px;

  &:hover {
    background: lighten($primary, 15%); // rozjaśnia kolor
  }

  &:active {
    background: darken($primary, 10%); // przyciemnia kolor
  }
}

```
