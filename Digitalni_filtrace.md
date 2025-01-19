# Digitální filtrace
## Analýza signálů I
### Michal Huptych
#### ZS 2023/2024
#### 5. 12. 2023

## Přehled literatury
- **Knihy a skripta**
  - Robert Vích, Zdeněk Smékal: *Číslicové filtry*, Academia, 2000
  - Vratislav Davídek, Miloš Laipert, Miroslav Vlček: *Analogové a číslicové filtry*, Vydavatelství ČVUT, 2000
  - Mohamed Najim: *Digital Filters Design for Signal and Image Processing*, Wiley-ISTE, 2006

## Zesílení a útlum
- Zesílení
  - Proces zvětšení amplitudy signálu (napěťové, proudové, atd.)
  - Udáváno buď bezrozměrně nebo v dB
  - Příklad vzorce pro zesílení: 
    ```
    A_U = U_výstupní / U_vstupní - ; A_U = 20*log(U_výstupní / U_vstupní) [dB]
    ```
- dB
  - Původně útlumu telefonního vedení, akustika
  - Logaritmická stupnice (podle vnímání sluchu)
  - Není jednotkou v rámci SI
  - Častokrát spojení 3 dB zesílení, resp. 3 dB útlum

## LTI systémy
- Lineární časově invariantní systémy
  - Daný vstupní signál x(t) způsobí na výstupu odezvu y(t)
  - Linearita: platí princip superpozice x1(t) + x2(t) = y1(t) + y2(t) 
  - Časová invariantost: platí x(t-t0) → y(t-t0)
- Předpoklady
  - Kauzalita
  - Stabilita

## Konvoluce
- Základní předpis
  - Kauzalita: h(t) = 0 pro t<0
  - Stabilita: h(t) → 0 pro t → ∞
- Matematické vlastnosti
  - Komutativní: a*b = b*a
  - Asociativní: (a*b)*c = a*(b*c)
  - Distributivní: a*b + a*c = a*(b + c)
- Popis systému
  - Diferenční rovnice
  - Impulsní odezva (LTI systémy)
  - Odezva na Dirakův impuls (jednotkový skok)

## Kauzalita a stabilita
- Kauzalita
  - y(n) + y(n-1)+ … + y(n-N) = x(n+M) - kazální pro M ≤ 0
- Asymptotická definice stability
  - Vlastní čísla systému definovaná algebraickou rovnicí det(λI − A) = 0 leží uvnitř jednotkové kružnice

## Fourierova transformace
- Základním matematickým aparátem pro převod z časové oblasti do frekvenční je Fourierova transformace
- Vztah ke konvoluci
  - S(ω) = ∫ s(t) e−jωt dt = s(t) ⋅ cos( ωt) − j ⋅ sin( ωt)
  - X(ω) = ∫ x(t) e−jωt dt; H(ω) = ∫ h(t) e−jωt dt
  - Y(ω) = X(ω) H(ω)
  - y(t) = (1/2π) ∫ Y(ω) ejωt dω

## Artefakty
- Část záznamu (biosignálu či obrazového signálu), která nemá fyziologický původ ve vyšetřovaném orgánu
- technické artefakty - především při zpracování bioelektrických signálů
- elektrostatické potenciály, rušení elektrorozvodnou sítí, impulsní rušivé signály, rušivá elektromagnetická pole, šum elektronických prvků a obvodů

## Filtrace
- Filtrace = rozdělení signálu na základě jeho frekvenčních složek na propustné a nepropustné pásmo
- Systém implementující funkci filtrace se nazývá filtr
- Filtrace je jednou z nejpoužívanějších operací v signálovém zpracování
- Za jistých podmínek je filtrace procesem, která propouští dané frekvenční pásmo s minimálními deformacemi

## Typy filtrů
- Podle funkce
  - dolní propust (DP)
  - horní propust (HP)
  - pásmová propust (PP)
  - pásmová zádrž (PZ)
- Podle impulzové odezvy
  - FIR filtry (finite impulse response)
  - IIR filtry (infinite impulse response)
- Podle typu zpracování
  - analogové filtry (odpor, kondenzátor, cívka)
  - číslicové filtry (signálové procesory, PC)

## Adaptivní filtrace
- Potřeba reagovat na změny rušení
- Základní uspořádání
- Adaptace
  - Nejčastěji LMS (Least Mean Square) algoritmus
  - Lineární filtr
  - V praxi většinou lineární filtr typu FIR (možno ale i IIR)

## Adaptivní filtrace - LMS
- Gradietní prohledávání
  - Důležitý je vztah mezi chybovým signálem 𝜖k a koeficienty filtru
  - Střední kvadratické odchylky chybového signálu 𝜖k má kvadratickou závislost na koeficientech filtru
  - Tedy můžeme pro střední hodnotu chybového signálu hledat globální minimum, které nám určuje optimální hodnotu koeficientu filtru

## Filtrace - příklady
- Příklady filtrace síťového brumu
- Odstranění tzv. baseline wandering
- Vyhlazení signálu
- Ukázky využití adaptivní filtrace pro EKG
- Síťové rušení 50 Hz
  - Notch filtr
  - Q = 35
  - f0 = 50 ± 0.71 Hz
- Odstranění pohybu izolinie
  - IIR filtr typu DP a 2. řádu
  - f_0 = 0.5Hz
  - filtrace s nulovou fází
- Vyhlazení
  - filtr Savitzky-golay
  - Šířka okna: 23
  - Řád polynomu: 11

## Využití ICA
- Numerická metoda separace signálů
- Zpracovávaný signál tvořen lineární kombinaci různých zdrojů signálu
- Komplikace
  - Pořadí nezávislých komponent nelze určit
  - Energii nezávislých komponent nelze určit
- V práci využito
  - Určení komponenty pomocí upraveného detektoru artefaktů
