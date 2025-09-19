# Cvičení 1
Hrubý postup práce a požadavky.

## Hrubý postup práce

Sběr požadavků proběhne přes proběhne přes brainstorming se zákazníkem, kdy zjistíme, co zákazník vlastně plně chce a jak si představuje jeho systém. Dále provedeme i průzkum trhu pro existující řešení a nakonec budeme sbírat informace o parkovišti, pro které systém vyvíjíme. Primárně půjde třeba o počet krytých míst, ale i existující infrastrukturu (např. senzory a brány pro vjezd). Průzkum uživatelů je poměrně zbytečný, protože cílová skupina řidičů aut je moc variabilní. Může se jednat o mechaniky i o vrátné, nemůžeme počítat s nějakou velkou znalostí technologií.

Poté můžeme začít s:
- **Analýzou**: Zde půjde o funkční požadavky a různé usecasy
- **Návrhem**: Tady počítáme s více specifickými návrhy pro to, jak by mohla implementace vypadat. Jde třeba o diagramy nasazení nebo třídní, ale i o zvolené technologie a rozmýšlení se nad ideálními technologiemi
- **Implementací**: Implementace by se měla řídit návrhem. V této fázi jsme ještě schopni poměrně jednoduše akceptovat a provádět změny v požadavcích.
- **Testování**: Testování proběhne jak na uživatelích z hlediska UX, tak i automatizovaně přímo na systému (zda jde rezervovat, zda navigace vede do cíle, atd.)
- **Nasazení**: Zde jde primárně o volbu hardware aby server splnil nefunkční požadavky, ta bude silně záviset na návrhu.

Po zákazníkovi budeme vyžadovat pravidelný feedback během vývoje, ať můžeme udělat případné změny do funkcionality před vydáním systému.

Reakce na změny budeme řešit postupným opakováním kroků výše. Například pokud dojde k nějaké změně během implementace, vrátíme se zpátky k analýze a od té pokračujeme původními kroky.

## Požadavky
### Funkční požadavky
- REQ-01: **Rezervace místa** -- Zákazník musí mít možnost rezervovat místo.
  - Rezervace se bude rezervovat o 5 minut dřív, než ji uživatel zadá v systému. Jedná se o takovou neviditelnou pojistku pro brzké příjezdy.
  - Pokud je na parkovišti volné místo, je možné provést platbu před bránou do parkoviště.
  - **Akceptační kritérium**: Systém zarezervuje místo pro daného zákazníka a nedovolí jinému uživateli udělat rezervaci na tom místě.
- REQ-02: **Zobrazení rezervací** -- Zákazník musí mít možnost zobrazit jeho současné rezervace.
  - **Akceptační kritérium**: Všechny aktuální rezervace uživatele se zobrazí, včetně stavu jejich platby.
- REQ-03: **Platba** -- Platba musí probíhat automaticky přes platební bránu.
  - Pro zákazníky, kteří na parkovišti přesáhnou dobu jejich rezervace budou automaticky účtovány přirážky.
  - **Akceptační kritérium**: Peníze budou doručeny na účet majitele parkoviště.
- REQ-04: **Navigace na místo** -- Uvnitř parkoviště by byly proměnlivé značky navigující na místo.
  - Kdyby byly dvě auta za sebou, tak *wtf*
  - Navigace ven bude vyřešená přes trvalé značky.
  - **Akceptační kritérium**: Systém bude ukazovat správnou cestu k místu.
- REQ-05: **Blokace míst** -- Musí být možnost, která neumožní uživateli zarezervovat dané místo.
  - **Akceptační kritérium**: Uživatel si nebude moct zarezervovat místo na zablokovaném místě.
- REQ-06: **Rušení rezervace** -- Uživatel musí mít možnost zrušit rezervaci.
  - Uživatel bude moct zrušit rezervaci do 15 minut před začátkem rezervace.
  - **Akceptační kritérium**: Místo nebude zarezervované; jiný uživatel si jej bude moct zarezervovat.
- REQ-07: **Scan SPZ** -- Systém musí umět scanovat SPZ u vstupní brány.
  - Pro vozidla bez SPZ na přední straně bude k dispozici čtečka QR kódu z papíru/mobilu nebo NFC čtečka pro mobily.
  - **Akceptační kritérium**: Systém bude bezchybně scanovat SPZ.
- REQ-08: **Hlášení problémů** -- Systém musí obsahovat nějakou možnost pro uživatele, jak hlásit různé problémy s parkovištěm nebo systémem.
  - **Akceptační kritérium**: Uživatel má možnost přes systém nahlásit nějaký problém, který si může správce prohlédnout, vyřešit a vymazat.

### Nefunkční
- REQ-09: **Bezpečnost** -- Systém uchovává platební, osobní údaje a SPZ. Dohromady tvoří citlivé údaje, čili bezpečnost dat je priotitou.
  - **Akceptační kritérium**: Systém bude nějak ok safe lmao.
- REQ-10: **Dostupnost** -- Nedostupný systém znamená nefunkční parkoviště. Pro lidi bez internetu je možné rezervovat předem nebo vjet přímo na místě.
  - **Akceptační kritérium**: Real people test in production.
- REQ-11: **Výkon** -- Otvírání brány by nemělo trvat moc dlouho, navigace by měla být načtená okamžitě po vjezdu.
  - **Akceptační kritérium**: Čas čekání na navigaci a otevření brány je neznatelný.
- REQ-12: **Responsivita** -- Systém by měl mít funkční rozhraní pro uživatele jak na velkých obrazovkách s myší tak i na malých obrazovkách.
  - **Akceptační kritérium**: Mělo by jít interagovat se systémem na mobilu, tabletu a počítači.

# Technologie
- PostgreSQL
- svelte nebo react frontend
- nodejs backend?
