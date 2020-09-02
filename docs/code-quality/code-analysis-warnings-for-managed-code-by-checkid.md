---
title: Omówienie reguł jakości kodu
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1310
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1417
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1805
- CA1806
- CA1809
- CA1810
- CA1811
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1835
- CA1836
- CA1837
- CA1838
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA5122
- CA5374
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 05937cef7187726134a7116edae4d74ee004de1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89219754"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Ostrzeżenia analizy kodu dla kodu zarządzanego według CheckId

Poniższa tabela zawiera ostrzeżenia analizy kodu dla kodu zarządzanego przez identyfikator CheckId ostrzeżenia.

| CheckId | Ostrzeżenie | Opis |
|---------| - | - |
| CA1000 | [CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000.md) | Po wywołaniu statycznego elementu członkowskiego typu ogólnego dla typu trzeba określić argument typu. Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. W tych dwóch przypadkach składnia określająca argument typu jest różna i łatwo o pomyłkę. |
| CA1001 | [CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji](../code-quality/ca1001.md) | Klasa deklaruje i implementuje pole wystąpienia typu System.IDisposable, ale nie implementuje interfejsu IDisposable. Klasa, która deklaruje pole IDisposable, pośrednio posiada niezarządzany zasób i powinna implementować interfejs IDisposable. |
| CA1002 | [CA1002: Nie uwidaczniaj list ogólnych](../code-quality/ca1002.md) | System. Collections. Generic. list< (of \<(T> ) >) to ogólna kolekcja, która została zaprojektowana pod kątem wydajności, a nie dziedziczenia. Dlatego też lista nie zawiera wirtualnych elementów członkowskich. Zamiast powyższych powinny zostać zastosowane kolekcje ogólne, zaprojektowane do obsługi dziedziczenia. |
| CA1003 | [CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń](../code-quality/ca1003.md) |Typ zawiera delegata zwracającego wartość void, którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs), i zawierający element docelowy zestawu Microsoft .NET Framework 2,0. |
| CA1004 | [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004.md) | Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. W przypadku użycia wnioskowania dla wszystkich parametrów typu składnia wywoływania ogólnych i nieogólnych metod wystąpień jest identyczna; upraszcza to użycie metod ogólnych. |
| CA1005 | [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005.md) | Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Zwykle jest oczywiste z jednym parametrem typu, jak na liście \<T> , a w niektórych przypadkach, które mają dwa parametry typu, jak w słowniku \<TKey, TValue> . Jeśli jednak istnieją więcej niż dwa parametry typu, poziom trudności staje się zbyt wysoki dla większości użytkowników. |
| CA1006 | [CA1006: Nie zagnieżdżaj typów ogólnych w podpisach składowych](../code-quality/ca1006.md) | Argument typu zagnieżdżonego jest argumentem typu, który jest również typem ogólnym. Aby wywołać element członkowski, którego podpis zawiera argument typu zagnieżdżonego, użytkownik musi zainicjować wystąpienie pierwszego typu ogólnego i przekazać go do konstruktora drugiego typu ogólnego. Wymagana procedura oraz składnia są złożone i należy ich unikać. |
| CA1007 |[CA1007: Używaj typów ogólnych tam, gdzie to odpowiednie](../code-quality/ca1007.md) | Metoda widoczna na zewnątrz zawiera parametr przekazany przez odwołanie do typu System.Object. Użycie metody ogólnej umożliwia przekazanie wszystkich typów podlegających ograniczeniom do metody, bez uprzedniego rzutowania typu do typu parametru przekazanego przez odwołanie. |
| CA1008 | [CA1008: Typy wyliczeniowe powinny mieć wartość zero](../code-quality/ca1008.md) | Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczanie przypisane bez flag powinno definiować element członkowski przy użyciu wartości zero, tak że wartość domyślna jest prawidłową wartością wyliczenia. Jeśli wyliczenie, w którym zastosowano atrybut FlagsAttribute, definiuje element członkowski o wartości zero, powinno być nazwane „Brak”, aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu. |
| CA1009 | [CA1009: Poprawnie deklaruj procedury obsługi zdarzeń](../code-quality/ca1009.md) | Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu System.Object i nosi nazwę „nadawca”. Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu System.EventArgs i nosi nazwę „e”. To dane, które są skojarzone ze zdarzeniem. Metody obsługi zdarzeń nie powinny zwracać wartości; w języku programowania C# jest to wskazywane przez zwrócony typ void. |
| CA1010 | [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010.md) | Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może zostać użyta, aby wypełnić typy generyczne kolekcji. |
| CA1011 |[CA1011: Rozważ przekazywanie typów podstawowych jako parametrów](../code-quality/ca1011.md) | Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Jeśli dodatkowa funkcjonalność dostarczana przez typ parametru pochodnego nie jest wymagana, użycie typu podstawowego umożliwia szersze wykorzystanie metody. |
| CA1012 | [CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów](../code-quality/ca1012.md) | Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany. |
| CA1013 | [CA1013: Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania](../code-quality/ca1013.md) | Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania. |
| CA1014 | [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014.md) | The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt wymusza, że wszystkie zestawy jawnie wskazują zgodność ze specyfikacją CLS przy użyciu <xref:System.CLSCompliantAttribute> . Jeśli ten atrybut nie jest obecny w zestawie, oznacza to, że zestaw jest niezgodny. |
| CA1016 | [CA1016: Oznacz zestawy atrybutem AssemblyVersion](../code-quality/ca1016.md) | Platforma .NET używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane. |
| CA1017 | [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute określa, w jaki sposób klienci COM otrzymują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie zastąpić dla poszczególnych typów i elementów członkowskich typu. Jeśli ten atrybut jest nieobecny, zawartość zestawu jest widoczna dla klientów COM. |
| CA1018 | [CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018.md) | Podczas definiowania atrybutu niestandardowego należy go oznaczyć przy użyciu elementu AttributeUsageAttribute, aby wskazać, w którym miejscu kodu źródłowego ma być on zastosowany. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. |
| CA1019 | [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019.md) | Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis. |
| CA1020 | [CA1020: Unikaj przestrzeni nazw z małą liczbą typów](../code-quality/ca1020.md) | Należy się upewnić, że każda z przestrzeni nazw posiada organizację logiczną i że istnieje uzasadniony powód, aby umieszczać typy w słabo wypełnionych przestrzeniach nazw. |
| CA1021 | [CA1021: Unikaj parametrów out](../code-quality/ca1021.md) | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między parametrami out i ref nie jest powszechnie zrozumiała. |
| CA1023 | [CA1023: Indeksatory nie powinny być wielowymiarowe](../code-quality/ca1023.md) | Indeksatory (właściwości indeksowane) powinny używać pojedynczego indeksu. Indeksatory wielowymiarowe mogą znacznie zmniejszyć użyteczność biblioteki. |
| CA1024 | [CA1024: Używaj właściwości, o ile to możliwe](../code-quality/ca1024.md) | Metody publiczne lub chronione mają nazwę zaczynającą się od „Get”, nie posiadają parametrów i zwracają wartość, która nie jest tablicą. Metoda ta może być dobrym kandydatem na właściwość. |
| CA1025 | [CA1025: Zastąp powtarzalne argumenty tablicą params](../code-quality/ca1025.md) | Użyj tablicy parametrów zamiast powtarzających się argumentów, gdy znana jest dokładna liczba argumentów i argumenty zmiennych są tego samego typu lub mogą być przekazane jako ten sam typ. |
| CA1026 | [CA1026: Nie należy używać parametrów domyślnych](../code-quality/ca1026.md) | Metody z wykorzystaniem parametrów domyślnych są dozwolone w ramach CLS, jednak CLS umożliwia kompilatorom ignorowanie wartości, które są przypisane do tych parametrów. Aby zapewnić odpowiednie zachowanie w językach programowania, metody z wykorzystaniem parametrów domyślnych należy zastąpić przeciążeniami metody, które dostarczają parametry domyślne. |
| CA1027 |[CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027.md) | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj atrybut FlagsAttribute do wyliczenia, gdy jego stałe nazwane mogą zostać sensownie połączone. |
| CA1028 | [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028.md) | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie typ danych System.Int32 jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to wymagane ani zalecane dla większości scenariuszy. |
| CA1030 | [CA1030: Używaj zdarzeń, o ile to możliwe](../code-quality/ca1030.md) |Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, powinna ona zostać wywołana przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę. |
| CA1031 | [CA1031: Nie przechwytuj typów wyjątków ogólnych](../code-quality/ca1031.md) | Ogólne wyjątki nie powinny być przechwytywane. Przechwytuj wyjątek bardziej precyzyjny lub zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w bloku catch. |
| CA1032 |[CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md) | Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. |
| CA1033 | [CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne](../code-quality/ca1033.md) | Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie. |
| CA1034 | [CA1034: Typy zagnieżdżone nie powinny być widoczne](../code-quality/ca1034.md) | Typ zagnieżdżony to typ, który jest zadeklarowany wewnątrz zakresu innego typu. Typy zagnieżdżone są przydatne w przypadku hermetyzacji szczegółów implementacji prywatnej typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz. |
| CA1035 | [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035.md) | Ta reguła wymaga implementacji ICollection w celu dostarczenia mocno typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ Object w przypadku używania funkcjonalności dostarczonej przez interfejs. Ta reguła zakłada, że typ, który implementuje ICollection, robi to tak, aby zarządzać kolekcją wystąpień typów mocniejszych niż Object. |
| CA1036 | [CA1036: Przesłaniaj metody porównywalnych typów](../code-quality/ca1036.md) |Typ publiczny lub chroniony implementuje interfejs System.IComparable. Nie zastępuje on metody Object.Equals ani nie przeciąża specyficznego dla języka operatora równości, nierówności, mniejsze lub większe niż. |
| CA1038 | [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038.md) | Ta reguła wymaga implementacji IEnumerator w celu dostarczenia silnie typizowanej wersji właściwości Current, tak aby użytkownicy nie musieli rzutować wartości zwróconej na typ silny w przypadku używania funkcjonalności dostarczonej przez interfejs. |
| CA1039 | [CA1039: Listy są silnie typizowane](../code-quality/ca1039.md) | Ta reguła wymaga implementacji IList w celu dostarczenia silnie typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ System.Object w przypadku używania funkcjonalności dostarczonej przez interfejs. |
| CA1040 |[CA1040: Unikaj pustych interfejsów](../code-quality/ca1040.md) | Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich; dlatego też nie definiuje kontraktu, który można zaimplementować. |
| CA1041 | [CA1041: Udostępnij komunikat ObsoleteAttribute](../code-quality/ca1041.md) | Typ lub element członkowski jest oznaczony za pomocą atrybutu System.ObsoleteAttribute, który nie ma określonej właściwości ObsoleteAttribute.Message. Podczas kompilowania typu lub elementu członkowskiego, który jest oznaczony za pomocą ObsoleteAttribute, wyświetlana jest właściwość Wiadomość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. |
| CA1043 | [CA1043: Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów](../code-quality/ca1043.md) | Indeksatory (właściwości indeksowane) powinny używać dla indeksu typów całkowitych lub ciągu. Typy te są zwykle używane do indeksowania struktur danych i zwiększają one użyteczność biblioteki. Użycie typu Object powinno zostać ograniczone do przypadków, w których nie może zostać określony typ całkowity lub ciąg w czasie projektowania. |
| CA1044 | [CA1044: Właściwości nie powinny być tylko do zapisu](../code-quality/ca1044.md) | Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Dzieje się tak dlatego, że umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwianie przeglądania tej wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność. |
| CA1045 |[CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045.md) | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać od użytkowników, aby Master pracował z `out` lub `ref` parametrami. |
| CA1046 | [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046.md) | Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt. |
| CA1047 |[CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych](../code-quality/ca1047.md) | Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Z definicji po typach zapieczętowanych nie można dziedziczyć, co oznacza, że nie można wywołać metody chronionej na typach zapieczętowanych. |
| CA1048 | [CA1048: Nie deklaruj wirtualnych składowych w typach zapieczętowanych](../code-quality/ca1048.md) | Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Z definicji po typie zapieczętowanym nie można dziedziczyć. Powoduje to, że metoda wirtualna w typie zapieczętowanym jest całkowicie nieprzydatna. |
| CA1049 | [CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji](../code-quality/ca1049.md) | Typy, które przydzielają zasoby niezarządzane, powinny implementować interfejs IDisposable, umożliwiając metodom wywołującym zwalnianie tych zasobów na żądanie i skrócenie czasu istnienia obiektów, które zawierają te zasoby. |
| CA1050 | [CA1050: Deklaruj typy w przestrzeniach nazw](../code-quality/ca1050.md) | Typy są zadeklarowane w przestrzeniach nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów. |
| CA1051 | [CA1051: Nie deklaruj widocznych pól w wystąpieniach](../code-quality/ca1051.md) | Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być prywatne lub wewnętrzne i dostępne przy użyciu właściwości. |
| CA1052 | [CA1052: Statyczne typy przechowujące powinny być zapieczętowane](../code-quality/ca1052.md) | Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowany za pomocą modyfikatora sealed (C# Reference) (NotInheritable). Typ, po którym nie będzie dziedziczenia, powinien być oznakowany przy użyciu modyfikatora sealed, aby zapobiec użyciu go jako typu podstawowego. |
| CA1053 |[CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053.md) | Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny. Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Przeciążenie typu ciąg powinno wywoływać, dla bezpieczeństwa, przeciążenie jednolitego identyfikatora zasobów (URI) przy użyciu argumentu typu ciąg. |
| CA1054 | [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054.md) | Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, powinno zostać dostarczone odpowiadające przeciążenie, pobierające wystąpienie klasy URI, które dostarcza te usługi w bezpieczny sposób. |
| CA1055 | [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055.md) | Reguła ta zakłada, że metoda zwraca identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1056 | [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056.md) | Reguła ta zakłada, że właściwość reprezentuje identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1057 | [CA1057: Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri](../code-quality/ca1057.md) | Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpieniem parametru typu ciąg parametrem System.Uri. Przeciążenie, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia, które przyjmuje parametr identyfikatora URI. |
| CA1058 | [CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych](../code-quality/ca1058.md) | Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Użyj jednej z alternatyw. |
| CA1059 |[CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059.md) | Konkretny typ jest typem posiadającym pełną implementację i dlatego może zostać utworzone jego wystąpienie. Aby włączyć powszechne użycie elementu członkowskiego, zamień konkretny typ, używając sugerowanego interfejsu. |
| CA1060 | [CA1060: Przenieś P/Invoke do klasy NativeMethods](../code-quality/ca1060.md) | Metody wywoływania platformy, takie jak te, które są oznaczone przy użyciu System.Runtime.InteropServices.Dllatrybutu "ImportAttribute" lub metod, które są zdefiniowane za pomocą słowa kluczowego Declare w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , uzyskują dostęp do niezarządzanego kodu. Metody te powinny być klasami NativeMethods, SafeNativeMethods lub UnsafeNativeMethods. |
| CA1061 |[CA1061: Nie ukrywaj metod klasy bazowej](../code-quality/ca1061.md) | Metoda w typie podstawowym jest ukryta przez metodę o identycznej nazwie typu pochodnego, gdy sygnatura parametru metody pochodnej różni się tylko typami, które są słabiej dziedziczone niż odpowiadające typy w sygnaturze parametru metody podstawowej. |
| CA1062 | [CA1062: Waliduj argumenty metod publicznych](../code-quality/ca1062.md) | Wszystkie argumenty odwołania, które są przekazywane do metody widocznej na zewnątrz, powinny być sprawdzane pod kątem wartości null. |
| CA1063 | [CA1063: Poprawnie zaimplementuj interfejs IDisposable](../code-quality/ca1063.md) | Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose. |
| CA1064 | [CA1064: Wyjątki powinny być publiczne](../code-quality/ca1064.md) | Wyjątek wewnętrzny jest widoczny tylko wewnątrz własnego zakresu wewnętrznego. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wewnętrzny wyjątek jest Dziedziczony z <xref:System.Exception> , <xref:System.SystemException> , lub <xref:System.ApplicationException> , kod zewnętrzny nie będzie zawierał wystarczających informacji, aby dowiedzieć się, co należy zrobić z wyjątkiem. |
| CA1065 | [CA1065: Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065.md) | Metoda, od której nie oczekiwano zgłaszania wyjątków, zgłasza wyjątek. |
| CA1066 | [CA1066: Zaimplementuj interfejs IEquatable przy przesłanianiu metody Equals](../code-quality/ca1066.md) | Typ wartości przesłania <xref:System.Object.Equals%2A> metodę, ale nie implementuje <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: Przesłoń metodę Equals podczas implementowania interfejsu IEquatable](../code-quality/ca1067.md) | Typ implementuje <xref:System.IEquatable%601> , ale nie przesłania <xref:System.Object.Equals%2A> metody. |
| CA1068 | [CA1068: Parametry CancellationToken muszą występować na końcu](../code-quality/ca1068.md) | Metoda ma parametr CancellationToken, który nie jest ostatnim parametrem. |
| CA1069 | [CA1069: Wyliczenia nie powinny mieć zduplikowanych wartości](../code-quality/ca1069.md) | Wyliczenie ma wiele elementów członkowskich, do których jawnie przypisano tę samą stałą wartość. |
| CA1070 | [CA1070: Nie deklaruj pól zdarzeń jako wirtualnych](../code-quality/ca1070.md) | [Zdarzenie podobne do pola](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) zostało zadeklarowane jako wirtualne. |
| CA1200 | [CA1200: Unikaj używania tagów cref z prefiksem](../code-quality/ca1200.md) | Atrybut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Należy unikać używania `cref` tagów z prefiksami, ponieważ uniemożliwia kompilatorowi Weryfikowanie odwołań. Uniemożliwia również znajdowanie i aktualizowanie tych odwołań do tych symboli podczas refaktoryzacji przez program Visual Studio Integrated Development Environment (IDE). |
| CA1300 | [CA1300: Określ argument MessageBoxOptions](../code-quality/ca1300.md) | Aby poprawnie wyświetlić okno komunikatu dla kultur stosujących pismo od prawej do lewej, członkowie RightAlign i RtlReading wyliczenia MessageBoxOptions muszą być przekazani do metody Show. |
| CA1301 | [CA1301: Unikaj duplikowania akceleratorów](../code-quality/ca1301.md) | Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane. |
| CA1302 | [CA1302: Nie umieszczaj trwale w kodzie ciągów specyficznych dla ustawień regionalnych](../code-quality/ca1302.md) | Wyliczenie System.Environment.SpecialFolder zawiera elementy, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w poszczególnych systemach operacyjnych; użytkownik może zmienić niektóre z tych lokalizacji; lokalizacje są zlokalizowane. Metoda Environment.GetFolderPath zwraca lokalizacje, które są skojarzone z wyliczeniem Environment.SpecialFolder, zlokalizowane i odpowiednie dla danego komputera. |
| CA1303 | [CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów](../code-quality/ca1303.md) | Metoda widoczna na zewnątrz przekazuje literał ciągu jako parametr do konstruktora lub metody .NET, a ten ciąg powinien być Lokalizowalny. |
| CA1304 | [CA1304: Określ argument CultureInfo](../code-quality/ca1304.md) | Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1305 | [CA1305: Określ argument IFormatProvider](../code-quality/ca1305.md) | Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1306 | [CA1306: Ustaw ustawienia regionalne dla typów danych](../code-quality/ca1306.md) | Ustawienia regionalne określą specyficzne dla kultur elementy prezentacji danych, takie jak formatowanie, które jest używane dla wartości liczbowych, symbole walut i porządek sortowania. Podczas tworzenia elementu DataTable lub DataSet należy jawnie ustawić ustawienia regionalne. |
| CA1307 | [CA1307: Określ parametr StringComparison w celu zapewnienia jednoznaczności](../code-quality/ca1307.md) | Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison. |
| CA1308 |[CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami](../code-quality/ca1308.md) | Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery. |
| CA1309 | [CA1309: Użyj porządkowego ustawienia właściwości StringComparison](../code-quality/ca1309.md) | Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny. |
| CA1310 | [CA1310: Określ parametr StringComparison w celu zapewnienia poprawności](../code-quality/ca1310.md) | Operacja porównywania ciągów używa przeciążenia metody, które nie ustawia parametru StringComparison i domyślnie używa porównania ciągów specyficznych dla kultury. |
| CA1400 | [CA1400: punkty wejścia P/Invoke powinny istnieć](../code-quality/ca1400.md) |Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. |
| CA1401 | [CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401.md) | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Takie metody nie powinny być udostępniane. |
| CA1402 |[CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](../code-quality/ca1402.md) | Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń. |
| CA1403 | [CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM](../code-quality/ca1403.md) | Typ wartości widoczny dla modelu COM jest oznaczony za pomocą atrybutu System. Runtime. InteropServices. StructLayoutAttribute o wartości LayoutKind. Auto. Układ tych typów może się zmieniać między wersjami programu .NET, co spowoduje przerwanie klientów COM, którzy oczekują określonego układu. |
| CA1404 | [CA1404: Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke](../code-quality/ca1404.md) | Wykonano wywołanie metody Marshal. metodę GetLastWin32Error lub równoważnej [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcji GetLastError, a bezpośrednio poprzednie wywołanie nie jest metodą Invoke systemu operacyjnego. |
| CA1405 | [CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM](../code-quality/ca1405.md) | Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM. |
| CA1406 |[CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6](../code-quality/ca1406.md) | Klienci Visual Basic 6 COM nie mogą uzyskać dostępu do 64-bitowych liczb całkowitych. |
| CA1407 |[CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM](../code-quality/ca1407.md) | Model COM nie obsługuje metod statycznych. |
| CA1408 | [CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408.md) | Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania. |
| CA1409 | [CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia](../code-quality/ca1409.md) |Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego. |
| CA1410 | [CA1410: Metody rejestracji modelu COM powinny mieć swoje odpowiedniki](../code-quality/ca1410.md) | Typ deklaruje metodę, która jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nie deklaruje metody oznaczonej za pomocą atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute lub odwrotnie. |
| CA1411 | [CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411.md) | Metoda oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute lub atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute jest widoczna na zewnątrz. |
| CA1412 | [CA1412: Oznacz interfejsy ComSource atrybutem IDispatch](../code-quality/ca1412.md) | Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM](../code-quality/ca1413.md) | Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń. |
| CA1414 | [CA1414: Oznacz argumenty logiczne P/Invoke za pomocą elementu MarshalAs](../code-quality/ca1414.md) | Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym. |
| CA1415 | [CA1415: Zadeklaruj prawidłowo element P/Invoke](../code-quality/ca1415.md) | Ta reguła szuka systemu operacyjnego wywołania deklaracji metody, które są przeznaczone dla [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcji, które mają wskaźnik do nakładający się parametrów struktury, a odpowiedni parametr zarządzany nie jest wskaźnikiem do struktury system. Threading. NativeOverlapped. |
| CA1417 | [CA1417: nie należy używać `OutAttribute` w parametrach ciągu dla elementu P/Invoke](../code-quality/ca1417.md) | Parametry ciągu przesyłane przez wartość z `OutAttribute` mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami. |
| CA1500 | [CA1500: Nazwy zmiennych nie powinny być zgodne z nazwami pól](../code-quality/ca1500.md) | Metoda wystąpienia deklaruje parametr lub zmienną lokalną, których nazwa pasuje do pola wystąpienia typu deklarującego, prowadząc do błędów. |
| CA1501 | [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| CA1502 | [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| CA1504 | [CA1504: Sprawdź pod kątem mylących nazw pól](../code-quality/ca1504.md) | Nazwa pola wystąpienia rozpoczyna się od "s_" lub nazwa pola statycznego (udostępnionego w Visual Basic) rozpoczyna się od "m_". |
| CA1505 | [CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| CA1506 | [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| CA1507 | [CA1507: Użyj operatora nameof zamiast ciągu](../code-quality/ca1507.md) | Literał ciągu jest używany jako argument, w którym `nameof` można użyć wyrażenia. |
| CA1508 | [CA1508: Unikaj martwego kodu warunku](../code-quality/ca1508.md) | Metoda ma kod warunkowy, który zawsze jest obliczany `true` lub `false` w czasie wykonywania. Prowadzi to do nieaktywnego kodu w `false` gałęzi warunku. |
| CA1509 | [CA1509: Nieprawidłowy wpis w pliku konfiguracji metryk kodu](../code-quality/ca1509.md) | Reguły metryk kodu, takie jak [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) i [CA1506](ca1506.md), dostarczyły plik konfiguracji o nazwie `CodeMetricsConfig.txt` z nieprawidłowym wpisem. |
| CA1600 | [CA1600: Nie używaj priorytetu procesu o wartości Bezczynny](../code-quality/ca1600.md) | Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają System.Diagnostics.ProcessPriorityClass.Idle, zajmują procesor, gdy może on być bezczynny, a zatem będą blokować stan gotowości. |
| CA1601 | [CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania](../code-quality/ca1601.md) | Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde. |
| CA1700 | [CA1700: Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”](../code-quality/ca1700.md) | Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. |
| CA1701 | [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md) | Każdy wyraz w ciągu zasobu jest podzielony na tokeny oparte na obudowie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. |
| CA1702 | [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md) | Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna. |
| CA1703 | [CA1703: Pisownia ciągów zasobów powinna być poprawna](../code-quality/ca1703.md) | Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA1704 | [CA1704: Pisownia identyfikatorów powinna być poprawna](../code-quality/ca1704.md) | Nazwa widocznego na zewnątrz identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA1707 | [CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia](../code-quality/ca1707.md) | Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry. |
| CA1708 | [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708.md) | Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. |
| CA1709 | [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md) | Według konwencji nazwy parametrów używają notacji CamelCase, a przestrzenie nazw, typy i elementy członkowskie notacji PascalCase. |
| CA1710 | [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710.md) |Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają przyrostek skojarzony z typem bazowym lub interfejsem. |
| CA1711 | [CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów](../code-quality/ca1711.md) | Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów. |
| CA1712 | [CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych](../code-quality/ca1712.md) | Nazwy elementów członkowskich wyliczenia nie mają prefiksu od nazwy typu, ponieważ narzędzia programistyczne dostarczają informacje na temat typu. |
| CA1713 | [CA1713: Zdarzenia nie powinny mieć prefiksu „before” ani „after”](../code-quality/ca1713.md) | Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. |
| CA1714 | [CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714.md) | Publiczne wyliczenie ma atrybut System.FlagsAttribute, a jego nazwa nie kończy się na „s”. Typy oznaczone przy użyciu FlagsAttribute mają nazwy w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. |
| CA1715 | [CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715.md) | Nazwa interfejsu, który jest widoczny na zewnątrz, nie zaczyna się od wielkiej litery „I”. Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery „T”. |
| CA1716 | [CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi](../code-quality/ca1716.md) | Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego. |
| CA1717 | [CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1717.md) | Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia. |
| CA1719 | [CA1719: Nazwy parametrów nie powinny być zgodne z nazwami składowych](../code-quality/ca1719.md) | Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki. |
| CA1720 |[CA1720: Identyfikatory nie powinny zawierać nazw typów](../code-quality/ca1720.md) | Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych. |
| CA1721 | [CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get](../code-quality/ca1721.md) |Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje. |
| CA1722 | [CA1722: Identyfikatory nie powinny mieć nieprawidłowych prefiksów](../code-quality/ca1722.md) | Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu. |
| CA1724 | [CA1724: Nazwy typów nie powinny być takie same jak nazwy przestrzeni nazw](../code-quality/ca1724.md) | Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw platformy .NET. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki. |
| CA1725 | [CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową](../code-quality/ca1725.md) | Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody. |
| CA1726 | [CA1726: Używaj preferowanych terminów](../code-quality/ca1726.md) | Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie „Flag” lub „Flags”. |
| CA1800 | [CA1800: Nie rzutuj niepotrzebnie](../code-quality/ca1800.md) | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| CA1801 | [CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801.md) | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| CA1802 |[CA1802: Używaj literałów w odpowiednich miejscach](../code-quality/ca1802.md) |Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) i jest inicjowane przy użyciu wartości obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na pole const (const w), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aby wartość była obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| CA1804 | [CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804.md) | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| CA1805 | [CA1805: Nie inicjuj niepotrzebnie](../code-quality/ca1805.md) | Środowisko uruchomieniowe platformy .NET inicjuje wszystkie pola typów odwołań do ich wartości domyślnych przed uruchomieniem konstruktora. W większości przypadków jawne zainicjowanie pola do jego wartości domyślnej jest nadmiarowe, co zwiększa koszty konserwacji i może obniżyć wydajność (na przykład większy rozmiar zestawu). |
| CA1806 | [CA1806: Nie ignoruj wyników metod](../code-quality/ca1806.md) | Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany. |
| CA1809 |[CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809.md) | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”. Aby zwiększyć szansę, że wszystkie zmienne lokalne są przechowywane, Ogranicz liczbę zmiennych lokalnych do 64. |
| CA1810 | [CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810.md) | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| CA1811 | [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811.md) | Prywatny lub wewnętrzny element członkowski (na poziomie zestawu) nie ma obiektów wywołujących w zestawie; nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego ani przez obiekt delegowany. |
| CA1812 | [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812.md) | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| CA1813 | [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813.md) | .NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| CA1814 | [CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814.md) | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy, mogą mieć różne rozmiary, co zapewnia większą oszczędność miejsca w przypadku niektórych zestawów danych. |
| CA1815 | [CA1815: Przesłaniaj metodę equals i operator równości w typach wartości](../code-quality/ca1815.md) | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| CA1816 | [CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (mi w Visual Basic). |
| CA1819 | [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819.md) | Tablice zwracane przez właściwości nie są zabezpieczone przed zapisem, nawet gdy mają właściwość tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| CA1820 | [CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820.md) | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| CA1821 | [CA1821: Usuwaj puste finalizatory](../code-quality/ca1821.md) | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator powoduje dodatkowe obciążenie i nie zapewnia żadnych korzyści. |
| CA1822 |[CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822.md) | Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone jako statyczne (udostępnione w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| CA1823 | [CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823.md) | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| CA1824 |[CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atrybut NeutralResourcesLanguage informuje Menedżera zasobów języka, który został użyty do wyświetlenia zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
| CA1825 |[CA1825: Unikaj alokacji tablic o zerowej długości](../code-quality/ca1825.md) | Inicjowanie tablicy o zerowej długości prowadzi do niepotrzebnej alokacji pamięci. Zamiast tego należy użyć statycznie przydzielonego wystąpienia pustej tablicy przez wywołanie <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Alokacja pamięci jest współdzielona przez wszystkie wywołania tej metody. |
| CA1826 |[CA1826: Użyj właściwości zamiast metody Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> Metoda LINQ została użyta na typie, który obsługuje równoważną, wydajniejszą właściwość. |
| CA1827 |[CA1827: Nie używaj funkcji Count/LongCount, gdy można użyć funkcji Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> Metoda or <xref:System.Linq.Enumerable.LongCount%2A> została użyta w przypadku, gdy <xref:System.Linq.Enumerable.Any%2A> Metoda byłaby bardziej wydajna. |
| CA1828 |[CA1828: Nie używaj funkcji CountAsync/LongCountAsync, gdy można użyć funkcji AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> Metoda or <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> została użyta w przypadku, gdy <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> Metoda byłaby bardziej wydajna. |
| CA1829 |[CA1829: Użyj właściwości Length/Count zamiast metody Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> Metoda LINQ została użyta w typie, który obsługuje równoważną, wydajniejszą `Length` lub `Count` Właściwość. |
| CA1830 |[CA1830: Preferuj silnie typizowane przeciążenia metod Append i Insert w elemencie StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> i <xref:System.Text.StringBuilder.Insert%2A> Podaj przeciążenia dla wielu typów poza <xref:System.String> .  Jeśli to możliwe, Preferuj silnie wpisane przeciążenia przy użyciu metody ToString () i przeciążenia opartego na ciągach. |
| CA1831 |[CA1831: Użyj metody AsSpan zamiast indeksatorów opartych na zakresie dla ciągów, gdy ma to zastosowanie](../code-quality/ca1831.md) | W przypadku korzystania z indeksatora zakresu w ciągu i niejawnego przypisywania wartości &lt; do &gt; typu char ReadOnlySpan, Metoda <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu ciągu. |
| CA1832 |[CA1832: Użyj metody AsSpan lub AsMemory zamiast indeksatorów opartych na zakresie do pobierania części ReadOnlySpan lub ReadOnlyMemory dla tablicy](../code-quality/ca1832.md) | W przypadku korzystania z indeksatora zakresu w tablicy i niejawnego przypisywania wartości <xref:System.ReadOnlySpan%601> do <xref:System.ReadOnlyMemory%601> typu lub, Metoda <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu tablicy. |
| CA1833 |[CA1833: Użyj metody AsSpan lub AsMemory zamiast indeksatorów opartych na zakresie do pobierania części Memory dla tablicy](../code-quality/ca1833.md) | W przypadku korzystania z indeksatora zakresu w tablicy i niejawnego przypisywania wartości <xref:System.Span%601> do <xref:System.Memory%601> typu lub, Metoda <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu tablicy. |
| CA1835 |[CA1835: Preferuj przeciążenia oparte na Memory' dla elementu "ReadAsync" i "WriteAsync"](../code-quality/ca1835.md) | Element "Stream" ma Przeciążenie "ReadAsync", które przyjmuje &lt; &gt; jako pierwszy argument "bajt pamięci", i Przeciążenie "WriteAsync", które pobiera "ReadOnlyMemory &lt; Byte &gt; " jako pierwszy argument. Preferuj wywoływanie przeciążeń opartych na pamięci, co jest bardziej wydajne. |
| CA1836 |[CA1836: Preferuj `IsEmpty` , `Count` Jeśli są dostępne](../code-quality/ca1836.md) | Preferuj `IsEmpty` Właściwość, która jest bardziej wydajna niż `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub, <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> Aby określić, czy obiekt zawiera elementy, czy nie. |
| CA1837 | [CA1837: Użyj `Environment.ProcessId` zamiast `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` jest prostsze i szybsze niż `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: Unikaj `StringBuilder` parametrów dla P/Invoke](../code-quality/ca1838.md) | Kierowanie elementu "StringBuilder" zawsze tworzy natywną kopię bufora, co powoduje utworzenie wielu alokacji dla jednej operacji organizowania. |
| CA1900 | [CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900.md) | Reguła ta sprawdza, czy struktury, które są zadeklarowane przez użycie jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych. |
| CA1901 | [CA1901: deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901.md) | Ta reguła oblicza rozmiar każdego parametru oraz wartości zwróconej przez metodę P/Invoke i sprawdza, czy rozmiar parametru jest poprawny podczas przekazywania do kodu niezarządzanego w 32-bitowych i 64-bitowych systemach operacyjnych. |
| CA1903 | [CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903.md) | Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu. |
| CA2000 | [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000.md) | Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem. |
| CA2001 | [CA2001: Unikaj wywoływania problematycznych metod](../code-quality/ca2001.md) | Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę. |
| CA2002 |[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002.md) |Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. |
| CA2003 |[CA2003: Nie traktuj włókien jak wątków](../code-quality/ca2003.md) | Zarządzany wątek jest traktowany jako [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] wątek. |
| CA2004 | [CA2004: Usuń wywołania funkcji GC.KeepAlive](../code-quality/ca2004.md) | Podczas konwertowania użycia SafeHandle należy usunąć wszystkie wywołania do GC.KeepAlive (obiekt). W tym przypadku klasy nie powinny wywołać GC.KeepAlive. Założono, że nie mają one finalizatorów, ale polegają na elemencie SafeHandle, który ma sfinalizować dla nich dojście systemu operacyjnego. |
| CA2006 | [CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych](../code-quality/ca2006.md) | Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane. |
| CA2007 | [CA2007: Nie oczekuj bezpośrednio zadania](ca2007.md) | Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> bezpośrednio. Gdy Metoda asynchroniczna czeka <xref:System.Threading.Tasks.Task> bezpośrednio, kontynuacja występuje w tym samym wątku, który utworzył zadanie. Takie zachowanie może być kosztowne pod względem wydajności i może spowodować zakleszczenie w wątku interfejsu użytkownika. Rozważ wywołanie metody <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> sygnalizującej zamiar kontynuacji. |
| CA2008 | [CA2008: Nie twórz zadań bez przekazania klasy TaskScheduler](ca2008.md) | Operacja tworzenia lub kontynuacji zadania używa przeciążenia metody, które nie określa <xref:System.Threading.Tasks.TaskScheduler> parametru. |
| CA2009 | [CA2009: Nie wywołuj elementu ToImmutableCollection dla wartości ImmutableCollection](ca2009.md) | `ToImmutable` Metoda była niekoniecznie wywoływana w niezmiennej kolekcji z <xref:System.Collections.Immutable> przestrzeni nazw. |
| CA2011 | [CA2011: Nie przypisuj właściwości w ramach jej metody ustawiającej](ca2011.md) | Właściwość przypadkowo przypisała wartość w ramach własnej [metody dostępu set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| CA2012 | [CA2012: Poprawnie używaj elementów ValueTask](ca2012.md) | ValueTasks zwracane z wywołań elementów członkowskich są przeznaczone do bezpośredniego oczekiwania.  Próbuje użyć ValueTask wiele razy lub uzyskać bezpośredni dostęp do wyniku, zanim będzie wiadomo, że może to spowodować wyjątek lub uszkodzenie.  Takie ValueTask jest prawdopodobnie oznaką funkcjonalnej usterki i może obniżyć wydajność. |
| CA2013 | [CA2013: Nie używaj metody ReferenceEquals z typami wartości](ca2013.md) | Porównując wartości przy użyciu <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , jeśli obja i objB są typami wartości, są one opakowane przed przekazaniem ich do <xref:System.Object.ReferenceEquals%2A> metody. Oznacza to, że nawet jeśli zarówno objA, jak i objB reprezentują to samo wystąpienie typu wartości, <xref:System.Object.ReferenceEquals%2A> Metoda jednak zwróci wartość false. |
| CA2014 | [CA2014: nie używaj stackalloc w pętlach.](ca2014.md) | Przestrzeń stosu przydzielona przez stackalloc jest wydawana tylko na końcu wywołania bieżącej metody.  Użycie jej w pętli może spowodować powstanie nieograniczonego wzrostu stosu i ostateczne warunki przepełnienia stosu. |
| CA2015 | [CA2015: nie Definiuj finalizatorów dla typów pochodzących z Pamięciobject &lt; T&gt;](ca2015.md) | Dodanie finalizatora do typu pochodzącego od <xref:System.Buffers.MemoryManager%601> może pozwolić na zwolnienie pamięci, gdy jest nadal używany przez <xref:System.Span%601> . |
| CA2016 | [CA2016: Prześlij dalej parametr CancellationToken do metod, które go przyjmują](ca2016.md) | Przekaż `CancellationToken` parametr do metod, które przyjmują w celu zapewnienia, że powiadomienia o anulowaniu operacji są prawidłowo propagowane, lub Przekaż `CancellationToken.None` jawnie, aby wskazać celowo niepropagowanie tokenu. |
| CA2100 | [CA2100: Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach](../code-quality/ca2100.md) | Metoda ustawia właściwość System.Data.IDbCommand.CommandText przez użycie ciągu, który jest zbudowany z argumentem ciągu do metody. Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL. |
| CA2101 |[CA2101: Określ kierowanie dla argumentów ciągu P/Invoke](../code-quality/ca2101.md) | Element członkowski wywołania platformy zezwala na dostęp częściowo zaufanych wywołań, ma parametr ciągu i nie kieruje jawnie tego ciągu. Może to spowodować potencjalne luki w zabezpieczeniach. |
| CA2102 | [CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi](../code-quality/ca2102.md) | Element członkowski w zestawie, który nie jest oznaczony za pomocą atrybutu RuntimeCompatibilityAttribute lub jest oznaczony jako RuntimeCompatibility(WrapNonExceptionThrows = false), zawiera blok catch obsługujący wyjątek System.Exception i nie zawiera bezpośrednio następującego ogólnego bloku catch. |
| CA2103 | [CA2103: Przejrzyj zabezpieczenia imperatywne](../code-quality/ca2103.md) |Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne. Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. |
| CA2104 |[CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu](../code-quality/ca2104.md) | Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej. Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. |
| CA2105 | [CA2105: Pola tablicy nie powinny być tylko do odczytu](../code-quality/ca2105.md) |Po zastosowaniu modyfikatora tylko do odczytu (ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) do pola, które zawiera tablicę, pola nie można zmienić, aby odwoływać się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu. |
| CA2106 | [CA2106: Zabezpiecz asercje](../code-quality/ca2106.md) | Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym. Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. |
| CA2107 | [CA2107: Przejrzyj przypadki użycia metod Deny i PermitOnly](../code-quality/ca2107.md) |Metody PermitOnly oraz akcje zabezpieczeń CodeAccessPermission. Deny powinny być używane tylko przez te osoby, które mają zaawansowaną wiedzę o zabezpieczeniach platformy .NET. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń. |
| CA2108 | [CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości](../code-quality/ca2108.md) | Publiczny lub chroniony typ wartości jest zabezpieczony przez dostęp do danych lub zapotrzebowanie na łącza. |
| CA2109 | [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109.md) | Wykryto publiczną lub chronioną metodę obsługi zdarzeń. Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne. |
| CA2111 |[CA2111: Wskaźniki nie powinny być widoczne](../code-quality/ca2111.md) | Wskaźnik nie jest prywatny, wewnętrzny ani tylko do odczytu. Złośliwy kod może zmienić wartość wskaźnika, co potencjalnie umożliwia dostęp do dowolnego miejsca w pamięci lub powoduje błędy aplikacji lub systemu. |
| CA2112 | [CA2112: Zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112.md) | Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez zapotrzebowania na łącza. Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu. |
| CA2114 | [CA2114: Zabezpieczenie metody powinno być nadzbiorem typu](../code-quality/ca2114.md) | Metoda nie powinna mieć zabezpieczeń deklaratywnych zarówno na poziomie metody, jak i na poziomie typu dla tej samej akcji. |
| CA2115 | [CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115.md) | Ta reguła wykrywa błędy, które mogą wystąpić, ponieważ kończy się działanie niezarządzanego zasobu, a wciąż jest on używany w kodzie niezarządzanym. |
| CA2116 | [CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116.md) |Gdy atrybut APTCA (AllowPartiallyTrustedCallersAttribute) jest obecny w zestawie całkowicie zaufanym i wykonuje kod w innym zestawie, który nie zezwala na dostęp częściowo zaufanych wywołań, mogą zostać wykorzystane luki w zabezpieczeniach. |
| CA2117 | [CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA](../code-quality/ca2117.md) | Gdy atrybut APTCA jest obecny w pełni zaufanym zestawie, a typ w zestawie dziedziczy z typu, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest wykorzystanie luk w zabezpieczeniach. |
| CA2118 | [CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118.md) |Atrybut SuppressUnmanagedCodeSecurityAttribute zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących kod niezarządzany, który używa wywołań międzyoperacyjnych COM lub systemu operacyjnego. Ten atrybut jest używany przede wszystkim do zwiększenia wydajności, wiąże się z nimi jednak znaczące zagrożenie bezpieczeństwa. |
| CA2119 | [CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych](../code-quality/ca2119.md) | Dziedziczony typ publiczny zapewnia implementację metody wewnętrznej (zaprzyjaźnionej w programie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Aby naprawić naruszenie tej zasady, należy zapobiegać zastąpieniu metody poza zestawem. |
| CA2120 | [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120.md) | Typ ten ma konstruktor, który przyjmuje obiekt System.Runtime.Serialization.SerializationInfo i obiekt System.Runtime.Serialization.StreamingContext (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale jeden lub kilka regularnych konstruktorów typu jest zabezpieczonych. |
| CA2121 | [CA2121: Konstruktory statyczne powinny być prywatne](../code-quality/ca2121.md) | System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie. |
| CA2122 | [CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand](../code-quality/ca2122.md) | Element członkowski publiczny lub chroniony ma zapotrzebowanie na łącza i jest wywoływany przez element członkowski, który nie sprawdza zabezpieczeń. Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. |
| CA2123 | [CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi](../code-quality/ca2123.md) | Ta reguła dopasowuje metodę do jej metody podstawowej, która jest interfejsem lub metodą wirtualną innego typu, a następnie porównuje zapotrzebowania na łącza na każdym z nich. Jeśli zasada ta jest naruszona, złośliwy wywołujący może pominąć zapotrzebowanie na łącza przez wywołanie niezabezpieczonej metody. |
| CA2124 | [CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try](../code-quality/ca2124.md) | Metoda publiczna lub chroniona zawiera blok try/finally. Wygląda na to, że blok finally resetuje stan zabezpieczeń i sam nie jest ujęty w bloku finally. |
| CA2126 | [CA2126: Żądania LinkDemand dla typu wymagają żądań dziedziczenia](../code-quality/ca2126.md) | Niezamknięty typ publiczny jest chroniony za pomocą zapotrzebowania na łącza i ma metodę, którą można zastąpić. Ani typ, ani metoda nie są chronione za pomocą żądania dziedziczenia. |
| CA2130 | [CA2130: Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste](../code-quality/ca2130.md) | Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej. |
| CA2131 | [CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów](../code-quality/ca2131.md) | Typ uczestniczy w równoważniku typu i albo sam typ, albo element członkowski, albo pole, albo typ jest oznaczony za pomocą atrybutu SecurityCriticalAttribute. Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach, które zawierają metody krytyczne lub pola uczestniczące w równoważeniu typu. Gdy CLR wykryje taki typ, nie ładuje go z wyjątkiem TypeLoadException w czasie wykonywania. Zazwyczaj ta reguła jest wykorzystywana tylko wtedy, gdy użytkownicy ręcznie implementują równoważnik typu, zamiast opierać się wykonaniu równoważnika typu przez tlbimp i kompilatory. |
| CA2132 | [CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego](../code-quality/ca2132.md) |Typy i elementy członkowskie, które mają atrybut SecurityCriticalAttribute, nie mogą być używane przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical. |
| CA2133 | [CA2133: Delegaci muszą być powiązani z metodami ze spójną przezroczystością](../code-quality/ca2133.md) | To ostrzeżenie jest zgłaszane na metodzie, która wiąże obiekt delegowany, oznaczony za pomocą atrybutu SecurityCriticalAttribute, do metody, która jest przezroczysta lub oznaczona za pomocą SecuritySafeCriticalAttribute. Ostrzeżenie jest także zgłaszane na metodzie, która wiąże obiekt delegowany przezroczysty lub bezpieczny-krytyczny do metody krytycznej. |
| CA2134 | [CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych](../code-quality/ca2134.md) |Ta reguła jest wykorzystywana, gdy metoda oznaczona za pomocą atrybutu SecurityCriticalAttribute zastępuje metodę, która jest przezroczysta lub oznaczona za pomocą atrybutu SecuritySafeCriticalAttribute. Reguła ta jest też wykorzystywana, gdy metoda przezroczysta lub oznaczona przy użyciu atrybutu SecuritySafeCriticalAttribute zastępuje metodę oznaczoną za pomocą atrybutu SecurityCriticalAttribute. Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs. |
| CA2135 | [CA2135: Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand](../code-quality/ca2135.md) | LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używania elementu LinkDemands do wymuszania zabezpieczeń w czasie kompilacji JIT, należy oznaczyć metody, typy i pola za pomocą atrybutu SecurityCriticalAttribute. |
| CA2127 | [CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu](../code-quality/ca2136.md) | Kod krytyczny nie może wystąpić w zestawie 100%-transparent. Ta reguła analizuje 100e zestawy przezroczyste dla dowolnych adnotacji SecurityCritical na poziomie typu, pola i metody. |
| CA2136 | [CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu](../code-quality/ca2136.md) | Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu o większym zakresie mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład klasa, która jest oznaczona za pomocą atrybutu SecurityCriticalAttribute, nie może zawierać metody oznaczonej za pomocą atrybutu SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni](../code-quality/ca2137.md) | Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie. Ta reguła jest wykorzystywana, kiedy przezroczysty pod względem zabezpieczeń kod próbuje wykonać niemożliwy do zweryfikowania Microsoft Intermediate Language (MISL). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL. |
| CA2138 | [CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity](../code-quality/ca2138.md) | Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions](../code-quality/ca2139.md) | Ta reguła jest wykorzystywana przez dowolną metodę, która jest przejrzysta i próbuje obsłużyć wyjątek uszkadzający proces przy użyciu atrybutu HandleProcessCorruptedStateExceptionsAttribute. Wyjątek uszkadzający proces to klasyfikacja wyjątków CLR w wersji 4.0 wątków takich jak AccessViolationException. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej. |
| CA2129 | [CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń](../code-quality/ca2140.md) | Metody, które są oznaczone atrybutem SecurityTransparentAttribute, wywołują niepubliczne elementy członkowskie, które są oznaczone jako SecurityCritical. Ta reguła analizuje wszystkie metody i typy w zestawie mieszanym przezroczysto-krytycznym i oznacza wszelkie wywołania z przezroczystego kodu do niepublicznego krytycznego kodu, który nie jest oznaczony jako SecurityTreatAsSafe. |
| CA2140 | [CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń](../code-quality/ca2140.md) | Element kodu, który jest oznaczony za pomocą atrybutu SecurityCriticalAttribute, jest krytyczny dla bezpieczeństwa. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli przezroczysty typ próbuje użyć typu krytycznego dla zabezpieczeń, zgłaszane są wyjątki TypeAccessException, MethodAccessException lub FieldAccessException. |
| CA2141 |[Metody CA2141:Transparent nie mogą spełniać LinkDemands](../code-quality/ca2141.md) | Przezroczysta pod względem bezpieczeństwa metoda wywołuje metodę w zestawie, który nie jest oznaczony za pomocą APTCA lub spełnia LinkDemand dla typu lub metody. |
| CA2142 | [CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand](../code-quality/ca2142.md) | Reguła ta jest zgłaszana na przezroczystej metodzie, które wymaga elementu LinkDemands, aby uzyskać do niej dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. |
| CA2143 | [CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń](../code-quality/ca2143.md) | Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. |
| CA2144 | [CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych](../code-quality/ca2144.md) | Przegląd zabezpieczeń dla kodu przezroczystego nie jest tak kompletny pod względem bezpieczeństwa, jak kodu krytycznego, ponieważ przezroczysty kod nie może wykonywać czynności wrażliwych pod względem bezpieczeństwa. Zestawy, które są ładowane z tablicy bajtowej, mogą nie być niezauważone w przezroczystym kodzie, a ta tablica bajtów może zawierać krytyczny albo, co ważniejsze, krytyczny dla bezpieczeństwa kod, który musi być poddany inspekcji. |
| CA2145 | [CA2145: Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145.md) | Metody, które są oznaczone przez atrybut SuppressUnmanagedCodeSecurityAttribute, mają niejawny element LinkDemand umieszczony na dowolnej metodzie, który ją wywołuje. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczanie metody, która używa zabezpieczenia SuppressUnmanagedCodeSecurity przez użycie atrybutu SecurityCriticalAttribute, sprawia, że wymóg ten jest bardziej oczywisty dla obiektów wywołujących metodę. |
| CA2146 | [CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe](../code-quality/ca2146.md) | Reguła ta jest wykorzystywana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. |
| CA2128 |[CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń](../code-quality/ca2147.md) | Ta reguła analizuje wszystkie metody i typy w zestawie, który jest 100 procent — przezroczysty lub mieszany przezroczysty/krytyczny, i flaguje wszelkie deklaratywne lub bezwzględne użycie metody Assert. |
| CA2147 |[CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń](../code-quality/ca2147.md) | Kod, który jest oznaczony jako SecurityTransparentAttribute, nie ma przyznanego wystarczającego uprawnienia do potwierdzenia. |
| CA2149 | [CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego](../code-quality/ca2149.md) | Reguła ta jest wykorzystywana dla każdej przezroczystej metody, która wywołuje bezpośrednio kod natywny, na przykład przez metodę P/Invoke. Naruszenie tej zasady prowadzi do wyjątku MethodAccessException na poziomie 2 modelu przezroczystości i pełnego żądania dla UnmanagedCode w modelu przezroczystości poziomu 1. |
| CA2151 |[CA2151: Pola typu krytycznego powinny być krytyczne pod względem zabezpieczeń](../code-quality/ca2151.md) | Aby używać typów krytycznych pod względem zabezpieczeń, kod odwołujący się do typu musi być albo krytyczny pod względem zabezpieczeń, albo bezpieczny-krytyczny pod względem zabezpieczeń. Ta zasada obowiązuje nawet w przypadku odwołania pośredniego. Dlatego pole mające zabezpieczenia przezroczyste lub pole bezpieczne-krytyczne pod względem zabezpieczeń jest mylące, ponieważ przezroczysty kod nadal nie będzie mógł uzyskać dostępu do pola. |
| CA2200 | [CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200.md) | Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona. |
| CA2201 | [CA2201: Nie zgłaszaj wyjątków o zastrzeżonych typach](../code-quality/ca2201.md) | Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2202 | [CA2202: Nie likwiduj obiektów wielokrotnie](../code-quality/ca2202.md) |Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu. |
| CA2204 | [CA2204: Pisownia literałów powinna być poprawna](../code-quality/ca2204.md) | Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA2205 | [CA2205: Użyj zarządzanych odpowiedników funkcji API Win32](../code-quality/ca2205.md) | Jest zdefiniowana metoda Invoke systemu operacyjnego i jest dostępna metoda .NET, która ma równoważne funkcje. |
| CA2207 | [CA2207: Pola statyczne typu wartości inicjuj bezpośrednio](../code-quality/ca2207.md) | Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny. |
| CA2208 |[CA2208: Poprawnie twórz wystąpienia wyjątków argumentów](../code-quality/ca2208.md) | Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException. |
| CA2210 |[CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210.md) | Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. |
| CA2211 |[CA2211: Pola niebędące stałymi nie powinny być widoczne](../code-quality/ca2211.md) | Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania, aby synchronizować dostęp do obiektu klasy. |
| CA2212 | [CA2212: Nie oznaczaj składników usługi atrybutem WebMethod](../code-quality/ca2212.md) |Metoda w typie, który dziedziczy z elementu System.EnterpriseServices.ServicedComponent, jest oznaczona za pomocą atrybutu System.Web.Services.WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne. |
| CA2213 | [CA2213: Pola możliwe do likwidacji należy likwidować](../code-quality/ca2213.md) | Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego. |
| CA2214 | [CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać](../code-quality/ca2214.md) | Gdy konstruktor wywołuje metodę wirtualną, konstruktor wystąpienia, który wywołuje metodę, mógł nie zostać wykonany. |
| CA2215 | [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215.md) | Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose. |
| CA2216 |[CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216.md) | Typ, który implementuje element System.IDisposable i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, tak jak opisano w Object.Finalize. |
| CA2217 | [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217.md) |Widoczne na zewnątrz wyliczenie jest oznaczone przy użyciu FlagsAttribute i ma jedną lub więcej wartości, które nie są potęgami dwójki lub kombinacji innych zdefiniowanych wartości z wyliczenia. |
| CA2218 |[CA2218: Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals](../code-quality/ca2218.md) | GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu. |
| CA2219 | [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków](../code-quality/ca2219.md) | Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2220 | [CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej](../code-quality/ca2220.md) | Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize. |
| CA2221 |[CA2221: Finalizatory powinny być chronione](../code-quality/ca2221.md) | Finalizatory muszą korzystać z modyfikatora dostępu „family”. |
| CA2222 | [CA2222: Nie obniżaj dziedziczonej widoczności składowych](../code-quality/ca2222.md) |Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. |
| CA2223 | [CA2223: Składowe powinny różnić się nie tylko zwracanym typem](../code-quality/ca2223.md) | Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET. |
| CA2224 | [CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości](../code-quality/ca2224.md) | Typ publiczny implementuje operator równości, lecz nie zastępuje metody Object.Equals. |
| CA2225 | [CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne](../code-quality/ca2225.md) |Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski udostępnia taką samą funkcjonalność jak operator i jest dostarczany deweloperom programującym w językach, które nie obsługują przeciążonych operatorów. |
| CA2226 | [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226.md) | Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego. |
| CA2227 |[CA2227: Właściwości kolekcji powinny być tylko do odczytu](../code-quality/ca2227.md) |Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. |
| CA2228 | [CA2228: Nie publikuj zasobów w formatach z wersji wstępnych](../code-quality/ca2228.md) | Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu .NET, mogą nie być używane przez obsługiwane wersje platformy .NET. |
| CA2229 | [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229.md) | Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. |
| CA2230 | [CA2230: Użyj elementu params dla argumentów zmiennych](../code-quality/ca2230.md) | Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params. |
| CA2231 | [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231.md) | Typ wartości zastępuje metodę Object.Equals, ale nie implementuje operatora równości. |
| CA2232 | [CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread](../code-quality/ca2232.md) | STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. |
| CA2233 |[CA2233: Operacje nie powinny powodować przepełnienia](../code-quality/ca2233.md) | Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzania argumentów. To gwarantuje, że wynik operacji nie jest spoza zakresu możliwych wartości dla typów danych, które są zaangażowane. |
| CA2234 | [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234.md) | Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”. Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri. |
| CA2235 | [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235.md) | Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. |
| CA2236 | [CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236.md) | Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora. |
| CA2237 | [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237.md) | Aby typy były rozpoznawalne przez CLR jako możliwe do serializacji, muszą być oznaczone za pomocą atrybutu SerializableAttribute nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez implementację interfejsu ISerializable. |
| CA2238 |[CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238.md) | Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności. |
| CA2239 | [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239.md) | Typ ma pole oznaczone za pomocą atrybutu System.Runtime.Serialization.OptionalFieldAttribute, ale nie zapewnia on metod obsługi zdarzeń deserializacji. |
| CA2240 | [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240.md) | Aby naprawić naruszenie tej zasady, należy się upewnić, że metoda GetObjectData jest widoczna oraz możliwa do zastąpienia i że wszystkie pola wystąpienia są uwzględnione w procesie serializacji lub jawnie oznaczone atrybutem NonSerializedAttribute. |
| CA2241 | [CA2241: Podaj poprawne argumenty metod formatowania](../code-quality/ca2241.md) | Argument formatu, który jest przekazany do elementu System.String.Format, nie zawiera elementu format, który odpowiada każdemu obiektowi argumentu lub odwrotnie. |
| CA2242 |[CA2242: Poprawnie testuj nie-liczby (NaN)](../code-quality/ca2242.md) | To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości. |
| CA2243 |[CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie](../code-quality/ca2243.md) | Parametr o typie literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikatora GUID lub wersji. |
| CA2244 | [CA2244: Nie duplikuj inicjowania indeksowanych elementów](../code-quality/ca2244.md) | Inicjator obiektu ma więcej niż jeden indeks elementu indeksowanego z tym samym indeksem stałym. Wszystkie oprócz ostatniego inicjatora są nadmiarowe. |
| CA2245 | [CA2245: Nie przypisuj właściwości do jej samej](../code-quality/ca2245.md) | Właściwość została przypadkowo przypisana do samej siebie. |
| CA2246 | [CA2246: Nie przypisuj symbolu i jego składowej w tej samej instrukcji](../code-quality/ca2246.md) | Przypisanie symbolu i jego elementu członkowskiego, czyli pola lub właściwości, w tej samej instrukcji nie jest zalecane. Nie jest jasne, jeśli dostęp do elementu członkowskiego był przeznaczony do użycia starej wartości symbolu przed przypisaniem lub nową wartością z przypisania w tej instrukcji. |
| CA2247 | [CA2247: argument przesłany do konstruktora TaskCompletionSource powinien być opcji TaskCreationOptions wyliczeniem zamiast TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource ma konstruktory, które przyjmują opcji TaskCreationOptions, które kontrolują podstawowe zadanie, i konstruktorów, które przyjmują stan obiektu, który jest przechowywany w zadaniu.  Przypadkowe przekazanie TaskContinuationOptions zamiast opcji TaskCreationOptions spowoduje wywołanie opcji jako stanu. |
| CA2249 | [CA2249: CA2249: Rozważ użycie ciągu. Contains zamiast String. IndexOf](../code-quality/ca2249.md) | Wywołania, do `string.IndexOf` których wynik służy do sprawdzania obecności/braku podciągu, mogą zostać zastąpione przez `string.Contains` . |
| CA5122 | [Deklaracje P/Invoke CA5122 deklaracje nie powinny być bezpieczne krytyczne](../code-quality/ca5122.md) | Metody są oznaczone jako SecuritySafeCritical, gdy wykonują operacje zależne od zabezpieczeń, ale mogą być również bezpiecznie używane przez kod przezroczystości. Kod przezroczystości może nigdy bezpośrednio nie wywołać kodu natywnego za pośrednictwem metody P/Invoke. Dlatego oznakowanie metody P/Invoke jako bezpiecznej-krytycznej pod względem zabezpieczeń nie umożliwi jej wywołania kodu przezroczystości i jest mylące dla analizy zabezpieczeń. |
| CA5359 | [CA5359 nie wyłączaj weryfikacji certyfikatu](../code-quality/ca5359.md) | Certyfikat może pomóc uwierzytelnić tożsamość serwera programu. Klienci powinni sprawdzić poprawność certyfikatu serwera, aby upewnić się, że żądania są wysyłane do zamierzonego serwera. Jeśli ServerCertificateValidationCallback zawsze zwróci `true` , każdy certyfikat przejdzie pomyślnie weryfikację. |
| CA5360 | [CA5360 nie wywoływać niebezpiecznych metod w deserializacji](../code-quality/ca5360.md) | Niezabezpieczona deserializacja jest luką w zabezpieczeniach, która występuje, gdy niezaufane dane są używane do nadużycia logiki aplikacji, wynoszą atak typu "odmowa usługi" (DoS), a nawet wykonują dowolny kod podczas deserializacji. Często Złośliwi użytkownicy mogą nadużyć tych funkcji deserializacji, gdy aplikacja deserializacji dane niezaufane, które są pod kontrolą. W celu wywołaj metody niebezpieczne w procesie deserializacji. Pomyślne niezabezpieczone ataki deserializacji mogą pozwolić atakującemu na przeprowadzanie ataków, takich jak ataki systemu DoS, obejścia uwierzytelniania i zdalne wykonywanie kodu. |
| CA5362 | [CA5362 potencjalny cykl odwołań w grafie obiektu deserializowanego](../code-quality/ca5362.md) | W przypadku deserializacji niezaufanych danych, każdy kod przetwarzania deserializowanego grafu obiektów musi obsługiwać cykle odwołań bez przechodzenia do nieskończonych pętli. Obejmuje to zarówno kod, który jest częścią wywołania zwrotnego deserializacji i kod, który przetwarza Graf obiektu po zakończeniu deserializacji. W przeciwnym razie atakujący może przeprowadzić atak typu "odmowa usługi" ze złośliwymi danymi zawierającymi cykl referencyjny. |
| CA5365 | [CA5365 nie wyłączaj sprawdzania nagłówka HTTP](../code-quality/ca5365.md) | Sprawdzanie nagłówka HTTP włącza kodowanie znaku powrotu karetki i znaków nowego wiersza, \r i \n, które znajdują się w nagłówkach odpowiedzi. To kodowanie może ułatwić uniknięcie ataków wykorzystujących niezaufane dane zawarte w nagłówku przez program. |
| CA5366 | [CA5366 Użyj elementu XmlReader do odczytu pliku XML](../code-quality/ca5366.md) | Korzystanie z programu <xref:System.Data.DataSet> do odczytywania danych XML z niezaufanymi danymi może ładować niebezpieczne odwołania zewnętrzne, które powinny być ograniczone przy użyciu programu <xref:System.Xml.XmlReader> z bezpiecznym mechanizmem rozwiązywania konfliktów lub z wyłączonym przetwarzaniem DTD. |
| CA5367 | [CA5367 nie serializować typów z polami wskaźników](../code-quality/ca5367.md) | Ta reguła sprawdza, czy istnieje Klasa możliwa do serializacji z polem wskaźnika lub właściwością. Elementy członkowskie, które nie mogą być serializowane, mogą być wskaźnikami, takimi jak statyczne elementy członkowskie lub pola oznaczone przy użyciu <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Ustaw ViewStateUserKey dla klas pochodnych ze strony](../code-quality/ca5368.md) | Ustawienie <xref:System.Web.UI.Page.ViewStateUserKey> właściwości może pomóc w zapobieganiu atakom w aplikacji przez umożliwienie przypisania identyfikatora do zmiennej stanu widoku dla poszczególnych użytkowników, tak aby atakujący nie mogli użyć zmiennej do wygenerowania ataku. W przeciwnym razie zostaną wystąpiły luki w zabezpieczeniach związane z fałszerstwem żądań między lokacjami. |
| CA5374 | [CA5374 nie należy używać XslTransform](../code-quality/ca5374.md) | Ta reguła sprawdza, czy <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> jest tworzone wystąpienie w kodzie. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> jest już przestarzałe i nie należy go używać. |
| CA5375 | [CA5375 nie używaj sygnatury dostępu współdzielonego konta](../code-quality/ca5375.md) | Sygnatura dostępu współdzielonego konta może delegować dostęp do operacji odczytu, zapisu i usuwania dla kontenerów obiektów blob, tabel, kolejek i udziałów plików, które nie są dozwolone przy użyciu sygnatury dostępu współdzielonego usługi. Nie obsługuje jednak zasad na poziomie kontenera i zapewnia mniejszą elastyczność i kontrolę nad udzielonymi uprawnieniami. Po otrzymaniu złośliwych użytkowników Twoje konto magazynu zostanie łatwo naruszone. |
| CA5376 | [CA5376 Użyj SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | Sygnatury dostępu współdzielonego to dane poufne, których nie można transportować w postaci zwykłego tekstu na HTTP |
| CA5377 | [CA5377 użycie zasad dostępu na poziomie kontenera](../code-quality/ca5377.md) | Zasady dostępu na poziomie kontenera można zmodyfikować lub odwołać w dowolnym momencie. Zapewnia większą elastyczność i kontrolę nad udzielonymi uprawnieniami. |
| CA5379 | [CA5379 nie używaj algorytmu funkcji wyprowadzania klucza słabego](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Klasa domyślnie używa <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algorytmu. Należy określić algorytm wyznaczania wartości skrótu, który ma być używany w niektórych przeciążeniach konstruktora z <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> lub wyższym. Uwaga, <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> Właściwość ma tylko `get` metodę dostępu i nie ma `overriden` modyfikatora. |
| CA5382 | [CA5382 używanie bezpiecznych plików cookie w ASP.NET Core](../code-quality/ca5382.md) | Aplikacje dostępne za pośrednictwem protokołu HTTPS muszą używać bezpiecznych plików cookie, które wskazują przeglądarkę, że plik cookie powinien być przesyłany tylko przy użyciu SSL (SSL). |
| CA5383 | [CA5383 Zadbaj o używanie bezpiecznych plików cookie w ASP.NET Core](../code-quality/ca5383.md) | Aplikacje dostępne za pośrednictwem protokołu HTTPS muszą używać bezpiecznych plików cookie, które wskazują przeglądarkę, że plik cookie powinien być przesyłany tylko przy użyciu SSL (SSL). |
| CA5384 | [CA5384 nie używają algorytmu podpisu cyfrowego (DSA)](../code-quality/ca5384.md) | DSA jest słabym algorytmem szyfrowania. |
| CA5385 | [CA5385 używać algorytmu Rivest – Shamir – Adleman (RSA) o odpowiednim rozmiarze klucza](../code-quality/ca5385.md) | Klucz RSA mniejszy niż 2048 bitów jest bardziej narażony na ataki typu "odmowa". |
| CA5387 | [CA5387 nie używaj słabej funkcji wyprowadzania klucza z niewystarczającą liczbą iteracji](../code-quality/ca5387.md) | Ta reguła sprawdza, czy klucz kryptograficzny został wygenerowany przy <xref:System.Security.Cryptography.Rfc2898DeriveBytes> użyciu liczby iteracji mniejszej niż 100 000. Wyższa liczba iteracji może pomóc wyeliminować ataki słownikowe próbujące złamać wygenerowany klucz kryptograficzny. |
| CA5388 | [CA5388 zapewnia wystarczającą liczbę iteracji podczas korzystania z funkcji wyprowadzania klucza słabego](../code-quality/ca5388.md) | Ta reguła sprawdza, czy klucz kryptograficzny został wygenerowany za <xref:System.Security.Cryptography.Rfc2898DeriveBytes> pomocą liczby iteracji, która może być mniejsza niż 100 000. Wyższa liczba iteracji może pomóc wyeliminować ataki słownikowe próbujące złamać wygenerowany klucz kryptograficzny. |
| CA5390 | [CA5390 klucz szyfrowania nie jest kodem twardym](../code-quality/ca5390.md) | Aby algorytm symetryczny był prawidłowy, klucz tajny musi być znany tylko nadawcy i odbiornik. Gdy klucz jest zakodowany, można go łatwo odnaleźć. Nawet przy użyciu skompilowanych plików binarnych, złośliwi użytkownicy mogą łatwo go wyodrębnić. Po naruszeniu zabezpieczeń klucza prywatnego tekst szyfru można odszyfrować bezpośrednio i nie jest już chroniony. |
| CA5391 | [CA5391 używaj tokenów antysfałszowanych w kontrolerach ASP.NET Core MVC](../code-quality/ca5391.md) | Obsługa `POST` , `PUT` , `PATCH` , lub `DELETE` żądanie bez weryfikowania tokenu antysfałszowanego może być narażona na ataki fałszerstwa żądań między lokacjami. Atakujący sfałszowanie żądań między lokacjami może wysyłać złośliwych żądań od uwierzytelnionego użytkownika do kontrolera ASP.NET Core MVC. |
| CA5392 | [CA5392 użycie atrybutu DefaultDllImportSearchPaths dla elementu P/Invoke](../code-quality/ca5392.md) | Domyślnie funkcja P/Invoke korzysta z <xref:System.Runtime.InteropServices.DllImportAttribute> sondowania wielu katalogów, w tym bieżącego katalogu roboczego biblioteki do załadowania. Może to być problem z zabezpieczeniami dla niektórych aplikacji, co prowadzi do przejęcia biblioteki DLL. |
| CA5393 | [CA5393 nie używają niebezpiecznej wartości DllImportSearchPath](../code-quality/ca5393.md) | Może istnieć złośliwa Biblioteka DLL w domyślnych katalogach wyszukiwania bibliotek DLL i katalogach zestawów. Lub, w zależności od tego, gdzie jest uruchomiona aplikacja, może istnieć złośliwa Biblioteka DLL w katalogu aplikacji. |
| CA5394 | [CA5394 nie używaj niezabezpieczonego losowości](../code-quality/ca5394.md) | Użycie kryptografii z kryptograficznie słabym generatorem liczb losowych może pozwolić osobie atakującej na przewidywalność wygenerowania wartości z uwzględnieniem zabezpieczeń. |
| CA5395 | [CA5395 chybień HttpVerb atrybutu dla metod akcji](../code-quality/ca5395.md) | Wszystkie metody akcji, które tworzą, edytują, usuwają lub w inny sposób modyfikują dane, muszą być chronione przy użyciu atrybutu antysfałszowanego z ataków fałszerstwa żądań między lokacjami. Wykonanie operacji GET powinno być bezpieczną operacją, która nie ma efektów ubocznych i nie modyfikuje utrwalonych danych. |
| CA5396 | [CA5396 Ustaw HttpOnly na wartość true dla HttpCookie](../code-quality/ca5396.md) | W celu zapewnienia kompleksowej oceny należy zapewnić, że poufne pliki cookie HTTP są oznaczane jako HttpOnly. Oznacza to, że przeglądarki sieci Web powinny uniemożliwić uzyskiwanie dostępu do plików cookie przez skrypty. Wprowadzane złośliwe skrypty są typowym sposobem kradzieży plików cookie. |
| CA5399 | [CA5399 ostatecznie Wyłącz sprawdzanie listy odwołania certyfikatów HttpClient](../code-quality/ca5399.md) | Odwołany certyfikat nie jest już zaufany. Mogą one być używane przez osoby atakujące, które przechodzą z pewnych złośliwych danych lub kradzieży poufnych danych w komunikacji przy użyciu protokołu HTTPS. |
| CA5400 | [CA5400 upewnij się, że sprawdzanie listy odwołania certyfikatów HttpClient nie jest wyłączone](../code-quality/ca5400.md) | Odwołany certyfikat nie jest już zaufany. Mogą one być używane przez osoby atakujące, które przechodzą z pewnych złośliwych danych lub kradzieży poufnych danych w komunikacji przy użyciu protokołu HTTPS. |
| CA5401 | [CA5401 nie używaj modułu szyfrującego z wartością niedomyślną IV](../code-quality/ca5401.md) | Szyfrowanie symetryczne powinno zawsze używać niepowtarzalnych wektorów inicjalizacji, aby zapobiec atakom słownikowym. |
| CA5402 | [CA5402 Użyj szyfrowania z wartością domyślną IV](../code-quality/ca5402.md) | Szyfrowanie symetryczne powinno zawsze używać niepowtarzalnych wektorów inicjalizacji, aby zapobiec atakom słownikowym. |
| IL3000 | [IL3000 Unikaj dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczy plik](../code-quality/il3000.md) | Unikaj używania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku |
| IL3001 | [IL3001 unikać uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku](../code-quality/il3001.md) | Należy unikać uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku |
