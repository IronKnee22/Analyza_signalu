# Spektrální analýza signálu I

## Fourierova transformace (FT)

### Definice
Fourierova transformace je základním nástrojem pro lineární zpracování signálů. Umožňuje jednoznačný převod signálu z časové reprezentace do frekvenční reprezentace a naopak. Umožňuje analyzovat frekvenční obsah (spektrum) signálu.

### Klíčové body
- **Spektrum signálu**: Analyzuje frekvenční obsah signálu.
- **Základní idea transformace**: Uvažuje transformace v časové nebo transformované oblasti.

### Komplexní čísla
- **Definice**: Komplexní číslo rozšiřuje reálné číslo o imaginární složku.


## Fourierovy řady
**Harmonická analýza:** Libovolnou periodickou funkci lze rozložit na elementární harmonické složky (sin, coss)  
**Kmitočtová syntéza:** Kombinací harmonických složek lze vytvořit libovolnou periodickou funkci.

### Sudé a liché funkce
**Sudá**: Sudá funkce je symetrická podle osy `y`  
**Lichá**: Lichá funkce je symetrická vůči počátku `bod [0,0]`

Každou funkci lze rozložit na sudou a lichou část. Sudou část lze poté vyjádřit pomocí kombinace kosinů, lichou část pomocí kombinace sinů.

### Trigonometrický tvar
Trigonometrický tvar Fourierových řad rozkládá periodickou funkci na součet sinusových a kosinusových funkcí, každá s určitou amplitudou a frekvencí

### Polární tvar
Polární tvar je jen jiný způsob vyjádření stejných informací jako trigonometrický tvar, ale s využitím polárních souřadnic.

### Komplexní (exponenciální) tvar
Tento tvar používá komplexní exponenciály místo sinus a kosinus, což činí výpočty často jednoduššími, zvláště v kontextu digitálního zpracování signálu

# Fourierova transformace
### Spojitý případ
fourierova transformace rozšiřuje koncept Fourierových řad na neperiodické funkce, umožnující analyzovat jakýkoliv spojitý signál tím, že jej převede z časové doméno do frekvenční domény

### Inverzní Fourierova transformace
Inverzní Fourierova transformace umožňuje převést data zpět z frekvenční domény do časové domény. 

### Amplitudové  spektrum
popisuje velikost (amplitudu) jednotlivých frekvenčních komponent v signálu. 

### Fázové spektrum
Poskytuje informace os fázi frekvenčních komponent signálu. Fáze určuje,jak jdou jednotlivé frekvenční komponenty posunuty v čase vzhledem k nějakému referenčnímu bodu

### Výkonové spektrum
Výkonové spektrum signálu ukazuje distribuci výkonu signálu mezi jednotlivými frekvencemi

### Spektrum reálného signálu
Je-li signál reálný, pak pro jeho spektrum platí:
- Amplitudové spektrum je sudou funkcí.
- Fázové spektrum je lichou funkcí
- Spektrum sudého signálu je sudou reálnou funkcí.
- Spektrum lichého signálu je lichou ryze imaginární funkcí

### Jednostranné a dvoustranné spektrum
**Jednostranné**:
- Jednostranné spektrum se obvykle používá pro reálné signály, kde záporné frekvence nejsou nutné k prezentaci spektra, protože mají stejnou informaci jako odpovídající kladné frekvence.

**Dvoustranné**: 
- Dvoustranné spektrum zahrnuje kompletní frekvenční rozsah od minus nekonečna do plus nekonečna 

## Diskrétní Fourierova transformace (DFT)
- **Definice**: Umožňuje výpočet Fourierova spektra z diskrétních bodů signálu.
- **Inverzní DFT**: Zpětný převod z frekvenčního spektra do časového signálu.

### Rychlá Fourierova transformace (FFT)
- **Výhody**: Efektivnější než DFT, složitost O(N log N).
- **Motýlkové schéma**: Algoritmus pro výpočet FFT.


### Spectrum leakage (prosakování ve spektru)
Prosakování způsobuje že spektrum získané pomocí DFT je pouze aproximací spektra a ne jeho přesným obrazem


### Analýza neperiodických signálů
Fourierova transformace předpokládá periodický signál. V případě, že potřebujeme analyzovat neperiodický signál, můžeme použít jeden z následujících přístupů:  
- **Časová okna**: Signál rozdělujeme do časových oken a předpokládáme periodicitu v rámci těchto oken.
- **Vlnková transformace**: Složitější bázové funkce, jako jsou wavelety, které lépe zpracovávají neperiodické signály.

## Short-time Fourier transform (STFT)
Analyzujeme signál po krátkých úsecích a aplikujeme Fourierovu transformaci na výsledky.

### Spektrogram
je vizuální reprezentace spektra frekvencí v signálu, jak se mění v čase

### Konstrukce spektrogramu
Projekce spekter z jednotlivých časových oken do finální matice, kde každý sloupec odpovídá spektru z jednoho časového okna.

### Rušení na frekvenci 50 Hz v elektrickém signálu
To je většinou z důvodu střídavého napětí v zásuvkách

## Příklady spektrogramů
- **EKG signál**: Dynamické sledování kvality EKG.
- **EEG signál**: Monitorování mozkové aktivity během spánku.
- **Seismická aktivita**: Charakterizace pyroklastických toků.
- **Vibrace motoru**: Analýza vibrací v automobilovém průmyslu.
- **Solární erupce**: Studium solárních erupcí prostřednictvím spektrogramů.


## Obálka signálu
Obálka signálu je hladká křivka, která obepíná vrcholy amplitudy daného signálu. Obálka může být použita k popisu změn amplitudy signálu v čase a je často užitečná pro analýzu modulovaných signálů.

### Klouzavý průměr RMS
Obálka se vypočítává pomocí klouzavé ho průměru kořene střední kvadratické hodnoty.

## Výkonová spektrální hustota
je funkce, která popisuje distribuci výkonu signálu v závislosti na frekvenci. Je to důležitý nástroj pro analýzu signálů v oblastech jako telekomunikace, akustika, a další technické aplikace

## Princip neurčitosti
- Vztahuje se k limitaci, jak přesně můžeme určit polohu a hybnost částice současně. Analogicky v signální analýze, čím přesněji určíme časovou polohu signálu, tím méně přesně určíme jeho frekvenci.


# Úvod do nelineárních systémů

## Nelineární analýza signálu
- **Realita**: Signály ve skutečném světě jsou často nelineární, což znamená složité vztahy mezi vstupy a výstupy.
- **Metody**: Používají se fraktální dimenze a Lyapunovovy exponenty pro zkoumání složitosti a chaotičnosti systémů.

## Lineární vs. Nelineární systémy
- **Lineární systémy**: Vyznačují se vlastnostmi superpozice, předvídatelným a jednoduše analyzovatelným chováním.
- **Nelineární systémy**: Nevykazují vlastnosti superpozice a mohou generovat složité, nebo chaotické výstupy.

## Fraktalita a samopodobnost
- **Definice**: Fraktální objekty jsou ty, které vykazují samopodobnost na různých úrovních detailu.
- **Fraktální dimenze**: Metrika, která kvantifikuje fraktalitu objektu, ukazující, jak se detailnost objektu mění s měřítkem.

## Odhad fraktální dimenze signálu
- **Metody**:
  - **Higuchiho metoda**: Efektivní výpočet fraktální dimenze časových řad.
  - **Box-counting**: Pokryje signál boxy různých velikostí a spočítá potřebný počet boxů.
  - **DFA (Detrended Fluctuation Analysis)**: Zkoumá dlouhodobou korelační strukturu v časových řadách.

## Teorie chaosu a deterministický chaos
- **Chaos**: Systém, který je extrémně citlivý na počáteční podmínky, což vede k dramaticky odlišným výsledkům při malých změnách.
- **Lorenzův atraktor**: Příklad nelineárního dynamického systému s chaotickým chováním.

## Ljapunovovy exponenty
- **Použití**: Matematický koncept pro charakterizaci dynamických systémů, zejména jejich citlivosti na počáteční podmínky.
- **Interpretace**:
  - **Pozitivní exponent**: Systém je chaotický a trajektorie se exponenciálně vzdalují.
  - **Nulový exponent**: Ukazuje na kvaziperiodické chování.
  - **Negativní exponent**: Trajektorie se sbíhají, systém je stabilní.




