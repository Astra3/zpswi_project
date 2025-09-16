# Cvičení 1

## Hrubý postup práce

Sběr požadavků proběhne přes

Po zákazníkovi budeme vyžadovat pravidelný feedback během vývoje, ať můžeme udělat případné změny do funkcionality před vydáním systému.

Reakce na změny...xd

## Požadavky
### Funkční požadavky
- **Rezervace místa** -- Zákazník musí mít možnost rezervovat místo.
  - Rezervace se bude rezervovat o 5 minut dřív, než ji uživatel zadá v systému. Jedná se o takovou neviditelnou pojistku pro brzké příjezdy.
  - Pokud je na parkovišti volné místo, je možné provést platbu před bránou do parkoviště.
  - **Akceptační kritérium**: Systém zarezervuje místo pro daného zákazníka a nedovolí jinému uživateli udělat rezervaci na tom místě.
- **Zobrazení rezervací** -- Zákazník musí mít možnost zobrazit jeho současné rezervace.
  - **Akceptační kritérium**: Všechny aktuální rezervace uživatele se zobrazí, včetně stavu jejich platby.
- **Platba** -- Platba musí probíhat automaticky přes platební bránu.
  - Pro zákazníky, kteří na parkovišti přesáhnou dobu jejich rezervace budou automaticky účtovány přirážky.
  - **Akceptační kritérium**: Peníze budou doručeny na účet majitele parkoviště.
- **Navigace na místo** -- Uvnitř parkoviště by byly proměnlivé značky navigující na místo.
  - Kdyby byly dvě auta za sebou, tak *wtf*
  - Navigace ven bude vyřešená přes trvalé značky.
  - **Akceptační kritérium**: Systém bude ukazovat správnou cestu k místu.
- **Blokace míst** -- Musí být možnost, která neumožní uživateli zarezervovat dané místo.
  - **Akceptační kritérium**: Uživatel si nebude moct zarezervovat místo na zablokovaném místě.
- **Rušení rezervace** -- Uživatel musí mít možnost zrušit rezervaci.
  - Uživatel bude moct zrušit rezervaci do 15 minut před začátkem rezervace.
  - **Akceptační kritérium**: Místo nebude zarezervované; jiný uživatel si jej bude moct zarezervovat.
- **Scan SPZ** -- Systém musí umět scanovat SPZ u vstupní brány.
  - Pro vozidla bez SPZ na přední straně bude k dispozici čtečka QR kódu z papíru/mobilu nebo NFC čtečka pro mobily.
  - **Akceptační kritérium**: Systém bude bezchybně scanovat SPZ.

### Nefunkční
- **Bezpečnost** -- Systém uchovává platební, osobní údaje a SPZ. Dohromady tvoří citlivé údaje, čili bezpečnost dat je priotitou.
  - **Akceptační kritérium**: Systém bude nějak ok safe lmao.
- **Dostupnost** -- Nedostupný systém znamená nefunkční parkoviště. Pro lidi bez internetu je možné rezervovat předem nebo vjet přímo na místě.
  - **Akceptační kritérium**: Real people test in production.
- **Výkon** -- Otvírání brány by nemělo trvat moc dlouho, navigace by měla být načtená okamžitě po vjezdu.
  - **Akceptační kritérium**: Čas čekání na navigaci a otevření brány je neznatelný.

# Technologie
- PostgreSQL
- svelte nebo react frontend
- nodejs backend?
