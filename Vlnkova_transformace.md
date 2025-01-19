# Vlnková transformace
## Analýza signálů I
### Michal Huptych
#### ZS 2023/2024
#### 19. 12. 2023

## Signál v časové doméně
- Signál měřený v čase
- Amplituda je závislá veličina funkce času
- Přirozená reprezentace měřené veličiny
- Většina měření probíhá primárně v čase
- Ne vždy vhodná doména pro analýzu signálu
- Nemá v časové oblasti jasně patrnou informaci
- Je rušený a rušení je více patrné v jiné doméně
- Vhodná extrakce příznaků v jiné doméně

## Signál ve frekvenční doméně
- Základní metoda je Fourierova transformace
- Převod z čistě časové oblasti do čistě frekvenční oblasti
- Rozložení na frekvenční složky reprezentované bazí (sin, cos)
- Signál ve frekvenční oblasti je komplexní signál
- Rozklad probíhá z 1D do 2D prostoru (frekvence, reálná, imaginární složka) – my však zobrazujeme mod – tedy opět 1D signál

## Časově-frekvenční oblast
- Short-time Fourier Transform (STFT)
- Metoda založená na Fourierově transformaci a rozdělení signálu v časové oblasti
- Okénková Fourierova transformace
- Násobení signálu posuvným oknem
- Výstup ve třech dimenzích – frekvence, čas, amplituda
- Amplituda je funkcí frekvence a času
- Délka okna určuje přesnost transformace v časové a/i frekvenční oblasti

## Vlnková transformace
- Přidává nekonstantní šířku okna, kterým je násoben užitečný signál
- Stále platí princip neurčitosti, ale změnou šířky okna můžeme jeho efekt snížit – zpřesnit výsledek transformace
- Využívá vlastnosti, že rychlé frekvence trvají obvykle kratší čas, kdežto pomalé frekvence delší čas
- U STFT se provádí Fourierova transformace, zde je transformace celková, bez následné FT

## Diskrétní vlnková transformace
- Discrete wavelet transform (DWT)
- Optimalizace diskretizované CWT
- Optimalizované vzorkování frekvenčního prostoru
- Dyadická (dvojková) mřížka daná předpisem s = 2^p, t = k*2^p, p,k ∈ Z
- Lze najít bázi vlnek, které jsou ortogonální / ortonormální

## Využití DWT
- Filtrace signálu
- Využití N-té aproximace (nižší frekvence signálu)
- Odstranění dané aproximace (aproximací) ze signálu

## Vlnková transformace v Matlabu
- Příkazy v Matlabu jsou rozděleny pro spojitou a diskrétní transformaci
- Základním příkazem pro spojitou vlnkovou transformaci je cwt
- Inverzní vlnková transformace je icwt
- Existuje příkaz pro vytvoření banky filtrů i pro cwt – cwtfilterbank
- Diskrétní transformace má příkaz dwt a idwt pro inverzní transformaci
- Pro informace o vlnkách je příkaz waveinfo
- V rámci GUI má Matlab příkaz waveletAnalyzer
