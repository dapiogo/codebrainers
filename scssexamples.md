# Zadanie 1 – Zmienne + Nesting (nagłówek z menu)

```
<header class="site-header">
  <h1>Moja Strona</h1>
  <nav>
    <ul>
      <li><a href="#">Start</a></li>
      <li><a href="#">Kontakt</a></li>
    </ul>
  </nav>
</header>
```

**Polecenia**
1 Ustal $primary i $spacing.
2 Tło nagłówka = $primary, padding = $spacing.
3 Linki w <nav> białe, hover jaśniejszy (nesting)


```
rozwiazanie

$primary: #2563eb;
$spacing: 20px;

.site-header {
  background: $primary; padding: $spacing; color: #fff;

  nav {
    ul {
      margin: 0; padding: 0; list-style: none; display: flex; gap: $spacing

      li {
        a {
          color: #fff; text-decoration: none; font-weight: 600;
          &:hover { color: lighten(#fff, 10%); text-decoration: underline; }
        }
      }
    }
  }
}

```


Zadanie 2 – Mixiny (flex + przycisk, z użyciem zmiennych)

```

<div class="wrap">
  <a href="#" class="btn-primary">Zamów</a>
  <button class="btn-alt">Kontakt</button>
</div>

Polecenia
	1	Zdefiniuj $primary, $secondary, $spacing, $radius.
	2	Napisz mixin flex-center($dir, $gap) i użyj w .wrap.
	3	Napisz mixin btn($bg, $size) (padding przez btn-padding($size)), użyj w .btn-primary i .btn-alt.


przykladowe rozwiazanie 

$primary:   #0ea5e9;
$secondary: #f59e0b;
$spacing:   20px;
$radius:    10px;

@function btn-padding($size) {
  @if $size == small { @return 8px 14px; }
  @else if $size == large { @return 14px 24px; }
  @return 12px 20px;
}

@mixin flex-center($dir: row, $gap: $spacing) {
  display: flex; flex-direction: $dir; justify-content: center; align-items: center; gap: $gap;
}

@mixin btn($bg, $size: medium) {
  background: $bg; color: #fff;
  padding: btn-padding($size);
  border: 2px solid darken($bg, 12%);
  border-radius: $radius; font-weight: 700; text-decoration: none; display: inline-block;
  transition: background .2s ease, transform .2s ease;
  &:hover  { background: lighten($bg, 10%); transform: translateY(-1px); }
  &:active { background: darken($bg, 6%);  transform: translateY(0); }
}

.wrap { @include flex-center(row, $spacing/2); }
a.btn-primary { @include btn($primary, medium); }
button.btn-alt { @include btn($secondary, large); }




```


Zadanie 3 – Funkcje (wbudowane + własne)


```

<section class="cards">
  <article class="card">
    <h3>Plan Basic</h3>
    <p class="price">49 zł</p>
  </article>
  <article class="card">
    <h3>Plan Pro</h3>
    <p class="price">99 zł</p>
  </article>
  <article class="card">
    <h3>Plan Max</h3>
    <p class="price">199 zł</p>
  </article>
</section>


Polecenia
	1	Ustal $primary, $spacing.
	2	Użyj funkcji wbudowanych: lighten, darken (cienie/ramki/tła).
	3	Zrób własną funkcję rem($px, $base) i użyj w tytułach/cenach.
	4	Dla .card:nth-child(2) zrób tło jako mix($primary, #22c55e, 30%).



przykladowe rozwiazanie 


$primary: #4f46e5;
$spacing: 20px;

@function rem($px, $base: 16px) { @return ($px / $base) * 1rem; }

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: $spacing;

  .card {
    background: #fff;
    border: 1px solid darken(#fff, 12%);
    border-radius: 12px;
    padding: $spacing;
    box-shadow: 0 8px 22px rgba(2,6,23,.06);

    h3 { font-size: rem(20); margin: 0 0 rem(8); }
    .price { font-size: rem(28); color: $primary; font-weight: 800; }

    &:hover {
      background: lighten(#fff, 2%);
      box-shadow: 0 12px 28px rgba(2,6,23,.12);
    }

    &:nth-child(2) {
      background: lighten(mix($primary, #22c55e, 30%), 35%);
      border-color: darken(mix($primary, #22c55e, 30%), 10%);
    }
  }
}

```
