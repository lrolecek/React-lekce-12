# React - lekce 12

Tento repozitář obsahuje podklady a cvičení pro 12. lekci kurzu React od Czechitas.


## React router a vnořené cesty

V předchozí lekci jsme si ukázali, jak pomocí React Routeru vytvářet v naší aplikaci samostatné stránky a jak mezi nimi navigovat.

Router toho ale umí mnohem víc, např. **vnořené cesty**.

V kódu vypadají např. takhle:
```jsx
<Routes>
	<Route path="/" element={ <Uvod /> } />
	<Route path="/produkty" element={ <Produkty /> } >
		<Route path="lednicky" element={ <Lednicky />} />
		<Route path="pracky" element={ <Pracky />} />
		<Route path="vysavace" element={ <Vysavace />} />
	</Route>
	<Route path="/kontakt" element={ <Kontakt /> } />
</Routes>
```

Všimni si, že cesta *produkty* je element, který v sobě obsahuje 3 další `Route`. Cesty z nadřazeného a vnořeného elementu se skládají dohromady, takže např. na pračky vede adresa `/produkty/pracky`.

Kam se ale komponenta `<Pracky />` zobrazí?

V komponentě `<Produkty />` použijeme komponentu `<Outlet />` z React Routeru. Nesmíme zapomenout ji naimportovat.

```jsx
import { Outlet } from 'react-router-dom';

const Produkty = () => {
	return (
		<>
			<h1>Produkty</h1>
			<p>Tady je obsah komponenty produkty.</p>

			<Outlet />

			<p>A tady může obsah klidně pokračovat.</p>
		</>
	);
}

export default Produkty;
```

Komponenta `<Outlet />` je vyhrazený prostor (prázdné místo), kam se vloží komponenta, na kterou ukazuje vnořená cesta.

## Cvičení

- [Cvičení 1 - Filmový magazín](https://github.com/Czechitas-React-podklady/Cviceni-Router-Filmovy-magazin) - v samostatném repozitáři, postupuj podle návodu tam

