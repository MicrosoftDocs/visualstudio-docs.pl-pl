---
title: Ostrzeżenia analizy kodu dla zarządzanego kodu dzięki CheckId
ms.date: 04/18/2019
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
- CA1068
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
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
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
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6ac6fccb69770c003f21875e5ab3809c2d6415b4
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305881"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Ostrzeżenia analizy kodu dla zarządzanego kodu dzięki CheckId

Poniższa tabela zawiera ostrzeżenia analizy kodu dla kodu zarządzanego przez identyfikator CheckId ostrzeżenia.

| CheckId | Ostrzeżenie | Opis |
|---------| - | - |
| CA1000 | [CA1000: Nie deklaruj statycznych składowych na typach ogólnych @ no__t-0 | Po wywołaniu statycznego elementu członkowskiego typu ogólnego dla typu trzeba określić argument typu. Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. W tych dwóch przypadkach składnia określająca argument typu jest różna i łatwo o pomyłkę. |
| CA1001 | [CA1001: Typy, które są własnością pól, powinny być jednorazowe @ no__t-0 | Klasa deklaruje i implementuje pole wystąpienia typu System.IDisposable, ale nie implementuje interfejsu IDisposable. Klasa, która deklaruje pole IDisposable, pośrednio posiada niezarządzany zasób i powinna implementować interfejs IDisposable. |
| CA1002 | [CA1002: Nie ujawniaj list ogólnych @ no__t-0 | System.Collections.Generic.List < (z \<(T >) >) jest kolekcją ogólną, która jest przeznaczona dla wydajności, nie o dziedziczeniu. Dlatego też lista nie zawiera wirtualnych elementów członkowskich. Zamiast powyższych powinny zostać zastosowane kolekcje ogólne, zaprojektowane do obsługi dziedziczenia. |
| CA1003 | [CA1003: Użyj ogólnych wystąpień programu obsługi zdarzeń @ no__t-0 |Typ zawiera delegata zwracającego wartość typu void, którego podpis zawiera dwa parametry (pierwszy typu obiekt i drugi typu, który można przypisać do EventArgs), a zawierające zestaw jest przeznaczony dla programu Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004: Metody ogólne powinny podawać parametr typu @ no__t-0 | Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. W przypadku użycia wnioskowania dla wszystkich parametrów typu składnia wywoływania ogólnych i nieogólnych metod wystąpień jest identyczna; upraszcza to użycie metod ogólnych. |
| CA1005 | [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych @ no__t-0 | Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Zwykle jest to za pomocą jednego parametru typu, jak w List\<T >, a w niektórych przypadkach zawierających dwa parametry typu, jak Dictionary\<TKey, TValue >. Jeśli jednak istnieją więcej niż dwa parametry typu, poziom trudności staje się zbyt wysoki dla większości użytkowników. |
| CA1006 | [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych @ no__t-0 | Argument typu zagnieżdżonego jest argumentem typu, który jest również typem ogólnym. Aby wywołać element członkowski, którego podpis zawiera argument typu zagnieżdżonego, użytkownik musi zainicjować wystąpienie pierwszego typu ogólnego i przekazać go do konstruktora drugiego typu ogólnego. Wymagana procedura oraz składnia są złożone i należy ich unikać. |
| CA1007 |[CA1007: Użyj typów ogólnych, gdzie odpowiednie wartości @ no__t-0 | Metoda widoczna na zewnątrz zawiera parametr przekazany przez odwołanie do typu System.Object. Użycie metody ogólnej umożliwia przekazanie wszystkich typów podlegających ograniczeniom do metody, bez uprzedniego rzutowania typu do typu parametru przekazanego przez odwołanie. |
| CA1008 | [CA1008: Wyliczenia powinny mieć zero wartości @ no__t-0 | Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczanie przypisane bez flag powinno definiować element członkowski przy użyciu wartości zero, tak że wartość domyślna jest prawidłową wartością wyliczenia. Jeśli wyliczenie, w którym zastosowano atrybut FlagsAttribute, definiuje element członkowski o wartości zero, powinno być nazwane „Brak”, aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu. |
| CA1009 | [CA1009: Zadeklaruj prawidłowo programy obsługi zdarzeń @ no__t-0 | Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu System.Object i nosi nazwę „nadawca”. Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu System.EventArgs i nosi nazwę „e”. To dane, które są skojarzone ze zdarzeniem. Metody obsługi zdarzeń nie powinny zwracać wartości; w języku programowania C# jest to wskazywane przez zwrócony typ void. |
| CA1010 | [CA1010: Kolekcje powinny implementować interfejs generyczny @ no__t-0 | Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może zostać użyta, aby wypełnić typy generyczne kolekcji. |
| CA1011 |[CA1011: Rozważ przekazanie typów podstawowych jako parametrów @ no__t-0 | Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Jeśli dodatkowa funkcjonalność dostarczana przez typ parametru pochodnego nie jest wymagana, użycie typu podstawowego umożliwia szersze wykorzystanie metody. |
| CA1012 | [CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów @ no__t-0 | Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany. |
| CA1013 | [CA1013: Operator przeciążenia jest równy na przeciążeniu Dodaj i Odejmij @ no__t-0 | Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania. |
| CA1014 | [CA1014: Oznacz zestawy atrybutem CLSCompliantAttribute @ no__t-0 | The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Zasada dobrego projektowania nakazuje, aby wszystkie zestawy jawnie wskazywały zgodność ze specyfikacją CLS przy użyciu <xref:System.CLSCompliantAttribute> . Jeśli ten atrybut nie jest obecny w zestawie, oznacza to, że zestaw jest niezgodny. |
| CA1016 | [CA1016: Oznacz zestawy atrybutem AssemblyVersionAttribute @ no__t-0 | Platforma .NET używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane. |
| CA1017 | [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute @ no__t-0 |ComVisibleAttribute określa, w jaki sposób klienci COM otrzymują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie zastąpić dla poszczególnych typów i elementów członkowskich typu. Jeśli ten atrybut jest nieobecny, zawartość zestawu jest widoczna dla klientów COM. |
| CA1018 | [CA1018: Oznacz atrybuty atrybutem AttributeUsageAttribute @ no__t-0 | Podczas definiowania atrybutu niestandardowego należy go oznaczyć przy użyciu elementu AttributeUsageAttribute, aby wskazać, w którym miejscu kodu źródłowego ma być on zastosowany. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. |
| CA1019 | [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów @ no__t-0 | Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis. |
| CA1020 | [CA1020: Unikaj przestrzeni nazw z kilkoma typami @ no__t-0 | Należy się upewnić, że każda z przestrzeni nazw posiada organizację logiczną i że istnieje uzasadniony powód, aby umieszczać typy w słabo wypełnionych przestrzeniach nazw. |
| CA1021 | [CA1021: Unikaj parametrów out @ no__t-0 | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między parametrami out i ref nie jest powszechnie zrozumiała. |
| CA1023 | [CA1023: Indeksatory nie powinny być wielowymiarowe @ no__t-0 | Indeksatory (właściwości indeksowane) powinny używać pojedynczego indeksu. Indeksatory wielowymiarowe mogą znacznie zmniejszyć użyteczność biblioteki. |
| CA1024 | [CA1024: Użyj właściwości, gdzie odpowiednie wartości @ no__t-0 | Metody publiczne lub chronione mają nazwę zaczynającą się od „Get”, nie posiadają parametrów i zwracają wartość, która nie jest tablicą. Metoda ta może być dobrym kandydatem na właściwość. |
| CA1025 | [CA1025: Zastąp powtarzalne argumenty z tablicą parametrów @ no__t-0 | Użyj tablicy parametrów zamiast powtarzających się argumentów, gdy znana jest dokładna liczba argumentów i argumenty zmiennych są tego samego typu lub mogą być przekazane jako ten sam typ. |
| CA1026 | [CA1026: Parametrów domyślnych nie należy używać @ no__t-0 | Metody z wykorzystaniem parametrów domyślnych są dozwolone w ramach CLS, jednak CLS umożliwia kompilatorom ignorowanie wartości, które są przypisane do tych parametrów. Aby zapewnić odpowiednie zachowanie w językach programowania, metody z wykorzystaniem parametrów domyślnych należy zastąpić przeciążeniami metody, które dostarczają parametry domyślne. |
| CA1027 |[CA1027: Oznacz typy wyliczeniowe atrybutem FlagsAttribute @ no__t-0 | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj atrybut FlagsAttribute do wyliczenia, gdy jego stałe nazwane mogą zostać sensownie połączone. |
| CA1028 | [CA1028: Magazyn wyliczeniowy powinien mieć wartość Int32 @ no__t-0 | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie typ danych System.Int32 jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to wymagane ani zalecane dla większości scenariuszy. |
| CA1030 | [CA1030: Użyj zdarzeń, gdzie odpowiednie wartości @ no__t-0 |Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, powinna ona zostać wywołana przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę. |
| CA1031 | [CA1031: Nie Przechwytuj typów wyjątków ogólnych @ no__t-0 | Ogólne wyjątki nie powinny być przechwytywane. Przechwytuj wyjątek bardziej precyzyjny lub zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w bloku catch. |
| CA1032 |[CA1032: Implementowanie standardowych konstruktorów wyjątków @ no__t-0 | Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. |
| CA1033 | [CA1033: Metody interfejsu powinny być wywoływane przez typy podrzędne @ no__t-0 | Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie. |
| CA1034 | [CA1034: Typy zagnieżdżone nie powinny być widoczne @ no__t-0 | Typ zagnieżdżony to typ, który jest zadeklarowany wewnątrz zakresu innego typu. Typy zagnieżdżone są przydatne w przypadku hermetyzacji szczegółów implementacji prywatnej typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz. |
| CA1035 | [CA1035: Implementacje ICollection mają jednoznacznie wpisane elementy członkowskie @ no__t-0 | Ta reguła wymaga implementacji ICollection w celu dostarczenia mocno typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ Object w przypadku używania funkcjonalności dostarczonej przez interfejs. Ta reguła zakłada, że typ, który implementuje ICollection, robi to tak, aby zarządzać kolekcją wystąpień typów mocniejszych niż Object. |
| CA1036 | [CA1036: Przesłoń metody na porównywalnych typach @ no__t-0 |Typ publiczny lub chroniony implementuje interfejs System.IComparable. Nie zastępuje on metody Object.Equals ani nie przeciąża specyficznego dla języka operatora równości, nierówności, mniejsze lub większe niż. |
| CA1038 | [CA1038: Moduły wyliczające powinny mieć silnie wpisaną wartość @ no__t-0 | Ta reguła wymaga implementacji IEnumerator w celu dostarczenia silnie typizowanej wersji właściwości Current, tak aby użytkownicy nie musieli rzutować wartości zwróconej na typ silny w przypadku używania funkcjonalności dostarczonej przez interfejs. |
| CA1039 | [CA1039: Listy są silnie wpisane @ no__t-0 | Ta reguła wymaga implementacji IList w celu dostarczenia silnie typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ System.Object w przypadku używania funkcjonalności dostarczonej przez interfejs. |
| CA1040 |[CA1040: Unikaj pustych interfejsów @ no__t-0 | Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich; dlatego też nie definiuje kontraktu, który można zaimplementować. |
| CA1041 | [CA1041: Podaj komunikat ObsoleteAttribute @ no__t-0 | Typ lub element członkowski jest oznaczony za pomocą atrybutu System.ObsoleteAttribute, który nie ma określonej właściwości ObsoleteAttribute.Message. Podczas kompilowania typu lub elementu członkowskiego, który jest oznaczony za pomocą ObsoleteAttribute, wyświetlana jest właściwość Wiadomość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. |
| CA1043 | [CA1043: Użyj argumentu całkowitego lub ciągu dla indeksatorów @ no__t-0 | Indeksatory (właściwości indeksowane) powinny używać dla indeksu typów całkowitych lub ciągu. Typy te są zwykle używane do indeksowania struktur danych i zwiększają one użyteczność biblioteki. Użycie typu Object powinno zostać ograniczone do przypadków, w których nie może zostać określony typ całkowity lub ciąg w czasie projektowania. |
| CA1044 | [CA1044: Właściwości nie powinny być tylko do zapisu @ no__t-0 | Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Dzieje się tak dlatego, że umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwianie przeglądania tej wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność. |
| CA1045 |[CA1045: Nie przekazuj typów przez odwołanie @ no__t-0 | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać, aby użytkownicy korzystali z parametrów `out` lub `ref`. |
| CA1046 | [CA1046: Nie przeciążania operatora Equals w typach referencyjnych @ no__t-0 | Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt. |
| CA1047 |[CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych @ no__t-0 | Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Z definicji po typach zapieczętowanych nie można dziedziczyć, co oznacza, że nie można wywołać metody chronionej na typach zapieczętowanych. |
| CA1048 | [CA1048: Nie deklaruj wirtualnych elementów członkowskich w typach zapieczętowanych @ no__t-0 | Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Z definicji po typie zapieczętowanym nie można dziedziczyć. Powoduje to, że metoda wirtualna w typie zapieczętowanym jest całkowicie nieprzydatna. |
| CA1049 | [CA1049: Typy, które są właścicielami zasobów natywnych, powinny być jednorazowe @ no__t-0 | Typy, które przydzielają zasoby niezarządzane, powinny implementować interfejs IDisposable, umożliwiając metodom wywołującym zwalnianie tych zasobów na żądanie i skrócenie czasu istnienia obiektów, które zawierają te zasoby. |
| CA1050 | [CA1050: Zadeklaruj typy w przestrzeniach nazw @ no__t-0 | Typy są zadeklarowane w przestrzeniach nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów. |
| CA1051 | [CA1051: Nie deklaruj widocznych pól wystąpień @ no__t-0 | Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być prywatne lub wewnętrzne i dostępne przy użyciu właściwości. |
| CA1052 | [CA1052: Statyczne typy zbiorników powinny być zapieczętowane @ no__t-0 | Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowany za pomocą modyfikatora sealed (C# Reference) (NotInheritable). Typ, po którym nie będzie dziedziczenia, powinien być oznakowany przy użyciu modyfikatora sealed, aby zapobiec użyciu go jako typu podstawowego. |
| CA1053 |[CA1053: Statyczne typy posiadaczy nie powinny mieć konstruktorów @ no__t-0 | Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny. Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Przeciążenie typu ciąg powinno wywoływać, dla bezpieczeństwa, przeciążenie jednolitego identyfikatora zasobów (URI) przy użyciu argumentu typu ciąg. |
| CA1054 | [CA1054: Parametry identyfikatora URI nie powinny być ciągami @ no__t-0 | Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, powinno zostać dostarczone odpowiadające przeciążenie, pobierające wystąpienie klasy URI, które dostarcza te usługi w bezpieczny sposób. |
| CA1055 | [CA1055: Zwracane wartości identyfikatora URI nie powinny być ciągami @ no__t-0 | Reguła ta zakłada, że metoda zwraca identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1056 | [CA1056: Właściwości identyfikatora URI nie powinny być ciągami @ no__t-0 | Reguła ta zakłada, że właściwość reprezentuje identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1057 | [CA1057: Przeciążenia identyfikatora URI ciągu wywołania metody System. URI overloads @ no__t-0 | Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpieniem parametru typu ciąg parametrem System.Uri. Przeciążenie, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia, które przyjmuje parametr identyfikatora URI. |
| CA1058 | [CA1058: Typy nie powinny poszerzać niektórych typów podstawowych @ no__t-0 | Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Użyj jednej z alternatyw. |
| CA1059 |[CA1059: Elementy członkowskie nie powinny ujawniać niektórych typów konkretnych, @ no__t-0 | Konkretny typ jest typem posiadającym pełną implementację i dlatego może zostać utworzone jego wystąpienie. Aby włączyć powszechne użycie elementu członkowskiego, zamień konkretny typ, używając sugerowanego interfejsu. |
| CA1060 | [CA1060: Przenieś P/Invoke do NativeMethods Class @ no__t-0 | Metody platform Invocation, takich jak te, które są oznaczone za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute, lub metody, które są zdefiniowane przy użyciu słowa kluczowego Declare w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dostęp do kodu niezarządzanego. Metody te powinny być klasami NativeMethods, SafeNativeMethods lub UnsafeNativeMethods. |
| CA1061 |[CA1061: Nie ukrywaj metod klasy bazowej @ no__t-0 | Metoda w typie podstawowym jest ukryta przez metodę o identycznej nazwie typu pochodnego, gdy sygnatura parametru metody pochodnej różni się tylko typami, które są słabiej dziedziczone niż odpowiadające typy w sygnaturze parametru metody podstawowej. |
| CA1062 | [CA1062: Weryfikuj argumenty metod publicznych @ no__t-0 | Wszystkie argumenty odwołania, które są przekazywane do metody widocznej na zewnątrz, powinny być sprawdzane pod kątem wartości null. |
| CA1063 | [CA1063: Zaimplementuj interfejs IDisposable poprawnie @ no__t-0 | Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose. |
| CA1064 | [CA1064: Wyjątki powinny być publiczne @ no__t-0 | Wyjątek wewnętrzny jest widoczny tylko wewnątrz własnego zakresu wewnętrznego. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wyjątek wewnętrzny jest dziedziczony z <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>, kod zewnętrzny nie ma wystarczające informacje, aby wiedzieli, co należy zrobić z wyjątkiem. |
| CA1065 | [CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach @ no__t-0 | Metoda, od której nie oczekiwano zgłaszania wyjątków, zgłasza wyjątek. |
| CA1068 | [CA1068: Parametry CancellationToken muszą pochodzić z ostatnich @ no__t-0 | Metoda ma parametr CancellationToken, który nie jest ostatnim parametrem. |
| CA1200 | [CA1200: Unikaj używania tagów cref z prefiksem @ no__t-0 | Atrybut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Unikaj używania tagów `cref` z prefiksami, ponieważ uniemożliwia kompilatorowi Weryfikowanie odwołań. Uniemożliwia również znajdowanie i aktualizowanie tych odwołań do tych symboli podczas refaktoryzacji przez program Visual Studio Integrated Development Environment (IDE). |
| CA1300 | [CA1300: Określ MessageBoxOptions @ no__t-0 | Aby poprawnie wyświetlić okno komunikatu dla kultur stosujących pismo od prawej do lewej, członkowie RightAlign i RtlReading wyliczenia MessageBoxOptions muszą być przekazani do metody Show. |
| CA1301 | [CA1301: Unikaj duplikowania akceleratorów @ no__t-0 | Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Gdy wiele kontrolek ma zduplikowane klucze dostępu, zachowanie klucza dostępu nie jest dobrze zdefiniowane. |
| CA1302 | [CA1302: Nie umieszczaj parametrów specyficznych dla ustawień regionalnych @ no__t-0 | Wyliczenie System.Environment.SpecialFolder zawiera elementy, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w poszczególnych systemach operacyjnych; użytkownik może zmienić niektóre z tych lokalizacji; lokalizacje są zlokalizowane. Metoda Environment.GetFolderPath zwraca lokalizacje, które są skojarzone z wyliczeniem Environment.SpecialFolder, zlokalizowane i odpowiednie dla danego komputera. |
| CA1303 | [CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych @ no__t-0 | Metoda widoczna na zewnątrz przekazuje literał ciągu jako parametr do konstruktora lub metody .NET, a ten ciąg powinien być Lokalizowalny. |
| CA1304 | [CA1304: Określ CultureInfo @ no__t-0 | Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1305 | [CA1305: Określ IFormatProvider @ no__t-0 | Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1306 | [CA1306: Ustaw ustawienia regionalne dla typów danych @ no__t-0 | Ustawienia regionalne określą specyficzne dla kultur elementy prezentacji danych, takie jak formatowanie, które jest używane dla wartości liczbowych, symbole walut i porządek sortowania. Podczas tworzenia elementu DataTable lub DataSet należy jawnie ustawić ustawienia regionalne. |
| CA1307 | [CA1307: Określ StringComparison @ no__t-0 | Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison. |
| CA1308 |[CA1308: Normalizowanie ciągów do Wielkiej litery @ no__t-0 | Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery. |
| CA1309 | [CA1309: Użyj porządkowej StringComparison @ no__t-0 | Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny. |
| CA1400 | [CA1400: Punkty wejścia P/Invoke powinny istnieć @ no__t-0 |Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. |
| CA1401 | [CA1401: Wartości P/Invoke nie powinny być widoczne dla parametru @ no__t-0 | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również implementowany przez słowo kluczowe Declare w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Takie metody nie powinny być udostępniane. |
| CA1402 |[CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM @ no__t-0 | Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń. |
| CA1403 | [CA1403: Typy Autoukładu nie powinny być widoczne dla modelu COM @ no__t-0 | Typ wartości widocznej dla modelu COM jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.StructLayoutAttribute ustawionego na LayoutKind.Auto. Układ tych typów może się zmieniać między wersjami programu .NET, co spowoduje przerwanie klientów COM, którzy oczekują określonego układu. |
| CA1404 | [CA1404: Wywołanie metody GetLastError natychmiast po P/Invoke @ no__t-0 | Wykonywane jest wywołanie metody Marshal.GetLastWin32Error lub równoważny [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcję GetLastError, a bezpośrednio poprzedzające wywołanie nie jest systemowi operacyjnemu wywołania metody. |
| CA1405 | [CA1405: Typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM @ no__t-0 | Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM. |
| CA1406 |[CA1406: Unikaj argumentów Int64 dla Visual Basic 6 klientów @ no__t-0 | Klienci Visual Basic 6 COM nie może uzyskać dostęp do 64-bitowych liczb całkowitych. |
| CA1407 |[CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM @ no__t-0 | Model COM nie obsługuje metod statycznych. |
| CA1408 | [CA1408: Nie używaj AutoDual ClassInterfaceType @ no__t-0 | Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania. |
| CA1409 | [CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia @ no__t-0 |Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego. |
| CA1410 | [CA1410: Metody rejestracji modelu COM powinny być dopasowane do wartości @ no__t-0 | Typ deklaruje metodę, która jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nie deklaruje metody oznaczonej za pomocą atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute lub odwrotnie. |
| CA1411 | [CA1411: Metody rejestracji modelu COM nie powinny być widoczne dla parametru @ no__t-0 | Metoda oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute lub atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute jest widoczna na zewnątrz. |
| CA1412 | [CA1412: Oznacz interfejsy ComSource jako IDispatch @ no__t-0 | Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM @ no__t-0 | Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń. |
| CA1414 | [CA1414: Oznacz argumenty typu Boolean P/Invoke za pomocą elementu MarshalAs @ no__t-0 | Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym. |
| CA1415 | [CA1415: Zadeklaruj prawidłowy element P/Invoke @ no__t-0 | Ta reguła szuka systemu operacyjnego, których platformą docelową deklaracji metod wywołania [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] parametru struktury funkcji, które mają wskaźnik do OVERLAPPED, a odpowiadający parametr zarządzalny nie jest wskaźnikiem do elementu System.Threading.NativeOverlapped Struktura. |
| CA1500 | [CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól @ no__t-0 | Metoda wystąpienia deklaruje parametr lub zmienną lokalną, których nazwa pasuje do pola wystąpienia typu deklarującego, prowadząc do błędów. |
| CA1501 | [CA1501: Unikaj nadmiernego dziedziczenia @ no__t-0 | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| CA1502 | [CA1502: Unikaj nadmiernej złożoności @ no__t-0 | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| CA1504 | [CA1504: Przejrzyj mylące nazwy pól @ no__t-0 | Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa pola statycznego (Shared w języku Visual Basic) zaczyna się od "m_". |
| CA1505 | [CA1505: Unikaj niemożliwego do utrzymania kodu @ no__t-0 | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| CA1506 |[CA1506: Unikaj nadmiernego sprzęgania klas @ no__t-0 | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| CA1600 | [CA1600: Nie używaj priorytetu procesu bezczynności @ no__t-0 | Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają System.Diagnostics.ProcessPriorityClass.Idle, zajmują procesor, gdy może on być bezczynny, a zatem będą blokować stan gotowości. |
| CA1601 | [CA1601: Nie używaj czasomierzy, które uniemożliwiają zmianę stanu baterii @ no__t-0 | Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde. |
| CA1700 | [CA1700: Nie określaj wartości wyliczenia "zarezerwowane" ](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. |
| CA1701 | [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter @ no__t-0 | Każdy wyraz w ciągu zasobu jest podzielony na tokeny oparte na obudowie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. |
| CA1702 | [CA1702: W wyrazach złożonych należy poprawnie uwzględniać wielkość liter @ no__t-0 | Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna. |
| CA1703 | [CA1703: Ciągi zasobów powinny mieć poprawną pisownię @ no__t-0 | Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA1704 | [CA1704: Identyfikatory powinny mieć poprawną pisownię @ no__t-0 | Nazwa widocznego na zewnątrz identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA1707 | [CA1707: Identyfikatory nie powinny zawierać podkreśleń @ no__t-0 | Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry. |
| CA1708 | [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter @ no__t-0 | Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. |
| CA1709 | [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter @ no__t-0 | Według konwencji nazwy parametrów używają notacji CamelCase, a przestrzenie nazw, typy i elementy członkowskie notacji PascalCase. |
| CA1710 | [CA1710: Identyfikatory powinny mieć poprawny sufiks @ no__t-0 |Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają przyrostek skojarzony z typem bazowym lub interfejsem. |
| CA1711 | [CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu @ no__t-0 | Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów. |
| CA1712 | [CA1712: Nie określaj prefiksu wartości wyliczenia z nazwą typu @ no__t-0 | Nazwy elementów członkowskich wyliczenia nie mają prefiksu od nazwy typu, ponieważ narzędzia programistyczne dostarczają informacje na temat typu. |
| CA1713 | [CA1713: Zdarzenia nie powinny mieć prefiksu poprzedzającego lub po znaku @ no__t-0 | Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. |
| CA1714 | [CA1714: Wyliczenia flag powinny mieć nazwy w liczbie mnogiej @ no__t-0 | Publiczne wyliczenie ma atrybut System.FlagsAttribute, a jego nazwa nie kończy się na „s”. Typy oznaczone przy użyciu FlagsAttribute mają nazwy w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. |
| CA1715 | [CA1715: Identyfikatory powinny mieć poprawny prefiks @ no__t-0 | Nazwa interfejsu, który jest widoczny na zewnątrz, nie zaczyna się od wielkiej litery „I”. Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery „T”. |
| CA1716 | [CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi @ no__t-0 | Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego. |
| CA1717 | [CA1717: Tylko wyliczenia FlagsAttribute powinny mieć nazwy w liczbie mnogiej @ no__t-0 | Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia. |
| CA1719 | [CA1719: Nazwy parametrów nie powinny być zgodne z nazwami elementów członkowskich @ no__t-0 | Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki. |
| CA1720 |[CA1720: Identyfikatory nie powinny zawierać nazw typu @ no__t-0 | Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych. |
| CA1721 | [CA1721: Nazwy właściwości nie powinny odpowiadać metodom Get @ no__t-0 |Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje. |
| CA1722 | [CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu @ no__t-0 | Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu. |
| CA1724 | [CA1724: Nazwy typów nie powinny być zgodne z przestrzenią nazw @ no__t-0 | Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw platformy .NET. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki. |
| CA1725 | [CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową @ no__t-0 | Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody. |
| CA1726 | [CA1726: Użyj preferowanych terminów @ no__t-0 | Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie „Flag” lub „Flags”. |
| CA1800 | [CA1800: Nie należy rzutować niepotrzebnie @ no__t-0 | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| CA1801 | [CA1801: Przejrzyj nieużywane parametry @ no__t-0 | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| CA1802 |[CA1802: Użyj literałów, gdzie odpowiednie wartości @ no__t-0 |Pole jest zadeklarowane jako statyczne i tylko do odczytu (Shared i ReadOnly w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i jest inicjowana za pomocą wartości obliczanej w czasie kompilacji. Ponieważ wartość, która jest przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację na stałą (Const w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| CA1804 | [CA1804: Usuń nieużywane elementy lokalne @ no__t-0 | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| CA1806 | [CA1806: Nie Ignoruj wyników metody @ no__t-0 | Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany. |
| CA1809 |[CA1809: Unikaj nadmiernych wartości lokalnych @ no__t-0 | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”. Aby zwiększyć prawdopodobieństwo, że wszystkie zmienne lokalne są przechowywane w rejestrze procesora, należy ograniczyć liczbę zmiennych lokalnych do 64. |
| CA1810 | [CA1810: Inicjuj wbudowane pola typu odwołania @ no__t-0 | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| CA1811 | [CA1811: Unikaj niewywołanego kodu prywatnego @ no__t-0 | Prywatny lub wewnętrzny element członkowski (na poziomie zestawu) nie ma obiektów wywołujących w zestawie; nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego ani przez obiekt delegowany. |
| CA1812 | [CA1812: Unikaj klas wewnętrznych bez wystąpień @ no__t-0 | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| CA1813 | [CA1813: Unikaj niezapieczętowanych atrybutów @ no__t-0 | .NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| CA1814 | [CA1814: Preferuj tablice nieregularne dla wielowymiarowego @ no__t-0 | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy, mogą mieć różne rozmiary, co zapewnia większą oszczędność miejsca w przypadku niektórych zestawów danych. |
| CA1815 | [CA1815: Przesłoń metodę Equals i operator Equals w typach wartości @ no__t-0 | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| CA1816 | [CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo @ no__t-0 | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize; lub metody, która nie jest implementacją Dispose, wywołuje GC. SuppressFinalize; lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje na coś innego niż to (Me w języku Visual Basic). |
| CA1819 | [CA1819: Właściwości nie powinny zwracać tablic @ no__t-0 | Tablice zwracane przez właściwości nie są zabezpieczone przed zapisem, nawet gdy mają właściwość tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| CA1820 | [CA1820: Testuj dla pustych ciągów przy użyciu długości ciągu @ no__t-0 | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| CA1821 | [CA1821: Usuń puste finalizatory @ no__t-0 | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator powoduje dodatkowe obciążenie i nie zapewnia żadnych korzyści. |
| CA1822 |[CA1822: Oznacz składowe jako static @ no__t-0 | Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| CA1823 | [CA1823: Unikaj nieużywanych pól prywatnych @ no__t-0 | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| CA1824 |[CA1824: Oznacz zestawy atrybutem NeutralResourcesLanguageAttribute @ no__t-0 | Atrybut NeutralResourcesLanguage informuje Menedżera zasobów języka, który został użyty do wyświetlenia zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
| CA1825 |[CA1825: Unikaj alokacji tablic o zerowej długości @ no__t-0 | Inicjowanie tablicy o zerowej długości prowadzi do niepotrzebnej alokacji pamięci. Zamiast tego należy użyć statycznie przydzielonego wystąpienia pustej tablicy, wywołując <xref:System.Array.Empty%2A?displayProperty=nameWithType>. Alokacja pamięci jest współdzielona przez wszystkie wywołania tej metody. |
| CA1900 | [CA1900: Pola typu wartości powinny być przenośne @ no__t-0 | Reguła ta sprawdza, czy struktury, które są zadeklarowane przez użycie jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych. |
| CA1901 | [CA1901: Deklaracje P/Invoke powinny być przenośne @ no__t-0 | Ta reguła oblicza rozmiar każdego parametru oraz wartości zwróconej przez metodę P/Invoke i sprawdza, czy rozmiar parametru jest poprawny podczas przekazywania do kodu niezarządzanego w 32-bitowych i 64-bitowych systemach operacyjnych. |
| CA1903 | [CA1903: Używaj tylko interfejsu API z platformy Target Framework @ no__t-0 | Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu. |
| CA2000 | [CA2000: Usuń obiekty przed utratą zakresu @ no__t-0 | Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem. |
| CA2001 | [CA2001: Unikaj wywoływania problematycznych metod @ no__t-0 | Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę. |
| CA2002 |[CA2002: Nie blokuj obiektów o słabej tożsamości @ no__t-0 |Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. |
| CA2003 |[CA2003: Nie Traktuj włókien jako wątków @ no__t-0 | Zarządzane zarządzalny wątek jest traktowany [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] wątku. |
| CA2004 | [CA2004: Usuń wywołania do GC. Utrzymywanie aktywności przez no__t-0 | Podczas konwertowania użycia SafeHandle należy usunąć wszystkie wywołania do GC.KeepAlive (obiekt). W tym przypadku klasy nie powinny wywołać GC.KeepAlive. Założono, że nie mają one finalizatorów, ale polegają na elemencie SafeHandle, który ma sfinalizować dla nich dojście systemu operacyjnego. |
| CA2006 | [CA2006: Używanie elementu SafeHandle do hermetyzacji zasobów natywnych @ no__t-0 | Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane. |
| CA2007 | [CA2007: Nie należy bezpośrednio czekać na zadanie @ no__t-0 | Metoda asynchroniczna [czeka](/dotnet/csharp/language-reference/keywords/await) bezpośrednio na <xref:System.Threading.Tasks.Task>. Gdy Metoda asynchroniczna czeka na <xref:System.Threading.Tasks.Task> bezpośrednio, kontynuacja występuje w tym samym wątku, który utworzył zadanie. Takie zachowanie może być kosztowne pod względem wydajności i może spowodować zakleszczenie w wątku interfejsu użytkownika. Rozważ wywołanie <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>, aby sygnalizować zamiar kontynuacji. |
| CA2100 | [CA2100: Przejrzyj zapytania SQL pod kątem luk w zabezpieczeniach @ no__t-0 | Metoda ustawia właściwość System.Data.IDbCommand.CommandText przez użycie ciągu, który jest zbudowany z argumentem ciągu do metody. Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL. |
| CA2101 |[CA2101: Określ kierowanie dla argumentów ciągu P/Invoke @ no__t-0 | Element członkowski wywołania platformy zezwala na dostęp częściowo zaufanych wywołań, ma parametr ciągu i nie kieruje jawnie tego ciągu. Może to spowodować potencjalne luki w zabezpieczeniach. |
| CA2102 | [CA2102: Przechwyć wyjątki inne niż CLSCompliant w ogólnych programach obsługi @ no__t-0 | Element członkowski w zestawie, który nie jest oznaczony za pomocą atrybutu RuntimeCompatibilityAttribute lub jest oznaczony jako RuntimeCompatibility(WrapNonExceptionThrows = false), zawiera blok catch obsługujący wyjątek System.Exception i nie zawiera bezpośrednio następującego ogólnego bloku catch. |
| CA2103 | [CA2103: Przejrzyj bezwzględne zabezpieczenia @ no__t-0 |Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne. Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe. |
| CA2104 |[CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu @ no__t-0 | Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej. Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. |
| CA2105 | [CA2105: Pola tablicy nie powinny być tylko do odczytu @ no__t-0 |Po zastosowaniu tylko do odczytu (ReadOnly w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modyfikatora pola, które zawiera tablicę, pola nie można zmienić, aby odwoływać się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu. |
| CA2106 | [CA2106: Potwierdzenia zabezpieczeń @ no__t-0 | Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym. Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. |
| CA2107 | [CA2107: Przejrzyj wartość Odmów i Zezwalaj tylko na użycie @ no__t-0 |Metody PermitOnly oraz akcje zabezpieczeń CodeAccessPermission. Deny powinny być używane tylko przez te osoby, które mają zaawansowaną wiedzę o zabezpieczeniach platformy .NET. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń. |
| CA2108 | [CA2108: Przejrzyj Zabezpieczenia deklaratywne typów wartości @ no__t-0 | Publiczny lub chroniony typ wartości jest zabezpieczony przez dostęp do danych lub zapotrzebowanie na łącza. |
| CA2109 | [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń @ no__t-0 | Wykryto publiczną lub chronioną metodę obsługi zdarzeń. Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne. |
| CA2111 |[CA2111: Wskaźniki nie powinny być widoczne dla parametru @ no__t-0 | Wskaźnik nie jest prywatny, wewnętrzny ani tylko do odczytu. Złośliwy kod może zmienić wartość wskaźnika, co potencjalnie umożliwia dostęp do dowolnego miejsca w pamięci lub powoduje błędy aplikacji lub systemu. |
| CA2112 | [CA2112: Zabezpieczone typy nie powinny ujawniać pól @ no__t-0 | Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez zapotrzebowania na łącza. Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu. |
| CA2114 | [CA2114: Zabezpieczenia metody muszą być nadzbiorem typu @ no__t-0 | Metoda nie powinna mieć zabezpieczeń deklaratywnych zarówno na poziomie metody, jak i na poziomie typu dla tej samej akcji. |
| CA2115 | [CA2115: Wywołaj metodę GC. Utrzymywanie aktywności w przypadku korzystania z zasobów natywnych @ no__t-0 | Ta reguła wykrywa błędy, które mogą wystąpić, ponieważ kończy się działanie niezarządzanego zasobu, a wciąż jest on używany w kodzie niezarządzanym. |
| CA2116 | [CA2116: Metody APTCA powinny wywołać tylko metody APTCA @ no__t-0 |Gdy atrybut APTCA (AllowPartiallyTrustedCallersAttribute) jest obecny w zestawie całkowicie zaufanym i wykonuje kod w innym zestawie, który nie zezwala na dostęp częściowo zaufanych wywołań, mogą zostać wykorzystane luki w zabezpieczeniach. |
| CA2117 | [CA2117: Typy APTCA powinny być rozszerzające tylko typy podstawowe APTCA @ no__t-0 | Gdy atrybut APTCA jest obecny w pełni zaufanym zestawie, a typ w zestawie dziedziczy z typu, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest wykorzystanie luk w zabezpieczeniach. |
| CA2118 | [CA2118: Przegląd użycia SuppressUnmanagedCodeSecurityAttribute @ no__t-0 |Atrybut SuppressUnmanagedCodeSecurityAttribute zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących kod niezarządzany, który używa wywołań międzyoperacyjnych COM lub systemu operacyjnego. Ten atrybut jest używany przede wszystkim do zwiększenia wydajności, wiąże się z nimi jednak znaczące zagrożenie bezpieczeństwa. |
| CA2119 | [CA2119: Metody pieczętowania, które spełniają interfejsy prywatne @ no__t-0 | Dziedziczny typ publiczny dostarcza zastępowalną implementację metody wewnętrznego (Friend w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) interfejsu. Aby naprawić naruszenie tej zasady, należy zapobiegać zastąpieniu metody poza zestawem. |
| CA2120 | [CA2120: Bezpieczne konstruktory serializacji @ no__t-0 | Typ ten ma konstruktor, który przyjmuje obiekt System.Runtime.Serialization.SerializationInfo i obiekt System.Runtime.Serialization.StreamingContext (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale jeden lub kilka regularnych konstruktorów typu jest zabezpieczonych. |
| CA2121 | [CA2121: Konstruktory statyczne powinny być prywatne @ no__t-0 | System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie. |
| CA2122 | [CA2122: Nie ujawniaj pośrednio metod z wymaganiem linku @ no__t-0 | Element członkowski publiczny lub chroniony ma zapotrzebowanie na łącza i jest wywoływany przez element członkowski, który nie sprawdza zabezpieczeń. Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. |
| CA2123 | [CA2123: Zastępowanie żądań linków powinno być takie samo jak Base @ no__t-0 | Ta reguła dopasowuje metodę do jej metody podstawowej, która jest interfejsem lub metodą wirtualną innego typu, a następnie porównuje zapotrzebowania na łącza na każdym z nich. Jeśli zasada ta jest naruszona, złośliwy wywołujący może pominąć zapotrzebowanie na łącza przez wywołanie niezabezpieczonej metody. |
| CA2124 | [CA2124: Zawijaj podatne klauzule finally w elemencie zewnętrznym try @ no__t-0 | Metoda publiczna lub chroniona zawiera blok try/finally. Wygląda na to, że blok finally resetuje stan zabezpieczeń i sam nie jest ujęty w bloku finally. |
| CA2126 | [CA2126: Wymagania dotyczące typu linku wymagają dziedziczenia. @ no__t-0 | Niezamknięty typ publiczny jest chroniony za pomocą zapotrzebowania na łącza i ma metodę, którą można zastąpić. Ani typ, ani metoda nie są chronione za pomocą żądania dziedziczenia. |
| CA2127 | [CA2136: Elementy członkowskie nie powinny mieć sprzecznych adnotacji przezroczystości @ no__t-0 | Krytyczny kod nie może wystąpić w zestawie 100% przezroczysty. Reguła ta analizuje zestawy 100% przezroczyste dla adnotacji SecurityCritical na poziomie typu, pola i metody. |
| CA2128 |[CA2147: Metody przezroczyste nie mogą używać potwierdzeń zabezpieczeń @ no__t-0 | Ta reguła analizuje wszystkie metody i typy w zestawie, który jest w 100% przezroczysty lub mieszany przezroczysto krytyczny i zaznacza deklaratywne lub imperatywne użycie potwierdzenia. |
| CA2129 | [CA2140: Kod przezroczysty nie może odwoływać się do elementów krytycznych zabezpieczeń @ no__t-0 | Metody, które są oznaczone atrybutem SecurityTransparentAttribute, wywołują niepubliczne elementy członkowskie, które są oznaczone jako SecurityCritical. Ta reguła analizuje wszystkie metody i typy w zestawie mieszanym przezroczysto-krytycznym i oznacza wszelkie wywołania z przezroczystego kodu do niepublicznego krytycznego kodu, który nie jest oznaczony jako SecurityTreatAsSafe. |
| CA2130 | [CA2130: Stałe krytyczne dla zabezpieczeń powinny być przezroczyste @ no__t-0 | Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej. |
| CA2131 | [CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą uczestniczyć w równoważności typu @ no__t-0 | Typ uczestniczy w równoważniku typu i albo sam typ, albo element członkowski, albo pole, albo typ jest oznaczony za pomocą atrybutu SecurityCriticalAttribute. Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach, które zawierają metody krytyczne lub pola uczestniczące w równoważeniu typu. Gdy CLR wykryje taki typ, nie ładuje go z wyjątkiem TypeLoadException w czasie wykonywania. Zazwyczaj ta reguła jest wykorzystywana tylko wtedy, gdy użytkownicy ręcznie implementują równoważnik typu, zamiast opierać się wykonaniu równoważnika typu przez tlbimp i kompilatory. |
| CA2132 | [CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego @ no__t-0 |Typy i elementy członkowskie, które mają atrybut SecurityCriticalAttribute, nie mogą być używane przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical. |
| CA2133 | [CA2133: Obiekty delegowane muszą być powiązane z metodami ze spójną przezroczystością @ no__t-0 | To ostrzeżenie jest zgłaszane na metodzie, która wiąże obiekt delegowany, oznaczony za pomocą atrybutu SecurityCriticalAttribute, do metody, która jest przezroczysta lub oznaczona za pomocą SecuritySafeCriticalAttribute. Ostrzeżenie jest także zgłaszane na metodzie, która wiąże obiekt delegowany przezroczysty lub bezpieczny-krytyczny do metody krytycznej. |
| CA2134 | [CA2134: Metody muszą zachować spójność przejrzystości podczas zastępowania metod podstawowych @ no__t-0 |Ta reguła jest wykorzystywana, gdy metoda oznaczona za pomocą atrybutu SecurityCriticalAttribute zastępuje metodę, która jest przezroczysta lub oznaczona za pomocą atrybutu SecuritySafeCriticalAttribute. Reguła ta jest też wykorzystywana, gdy metoda przezroczysta lub oznaczona przy użyciu atrybutu SecuritySafeCriticalAttribute zastępuje metodę oznaczoną za pomocą atrybutu SecurityCriticalAttribute. Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs. |
| CA2135 | [CA2135: Zestawy Level 2 nie powinny zawierać LinkDemands @ no__t-0 | LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używania elementu LinkDemands do wymuszania zabezpieczeń w czasie kompilacji JIT, należy oznaczyć metody, typy i pola za pomocą atrybutu SecurityCriticalAttribute. |
| CA2136 | [CA2136: Elementy członkowskie nie powinny mieć sprzecznych adnotacji przezroczystości @ no__t-0 | Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu o większym zakresie mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład klasa, która jest oznaczona za pomocą atrybutu SecurityCriticalAttribute, nie może zawierać metody oznaczonej za pomocą atrybutu SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137: Metody przezroczyste muszą zawierać tylko możliwy do zweryfikowania kod IL @ no__t-0 | Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie. Ta reguła jest wykorzystywana, kiedy przezroczysty pod względem zabezpieczeń kod próbuje wykonać niemożliwy do zweryfikowania Microsoft Intermediate Language (MISL). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL. |
| CA2138 | [CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity @ no__t-0 | Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions @ no__t-0 | Ta reguła jest wykorzystywana przez dowolną metodę, która jest przejrzysta i próbuje obsłużyć wyjątek uszkadzający proces przy użyciu atrybutu HandleProcessCorruptedStateExceptionsAttribute. Wyjątek uszkadzający proces to klasyfikacja wyjątków CLR w wersji 4.0 wątków takich jak AccessViolationException. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej. |
| CA2140 | [CA2140: Kod przezroczysty nie może odwoływać się do elementów krytycznych zabezpieczeń @ no__t-0 | Element kodu, który jest oznaczony za pomocą atrybutu SecurityCriticalAttribute, jest krytyczny dla bezpieczeństwa. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli przezroczysty typ próbuje użyć typu krytycznego dla zabezpieczeń, zgłaszane są wyjątki TypeAccessException, MethodAccessException lub FieldAccessException. |
| CA2141 |[CA2141: Metody przezroczyste nie mogą spełniać żądań LinkDemand](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Przezroczysta pod względem bezpieczeństwa metoda wywołuje metodę w zestawie, który nie jest oznaczony za pomocą APTCA lub spełnia LinkDemand dla typu lub metody. |
| CA2142 | [CA2142: Kod przezroczysty nie powinien być chroniony za pomocą LinkDemands @ no__t-0 | Reguła ta jest zgłaszana na przezroczystej metodzie, które wymaga elementu LinkDemands, aby uzyskać do niej dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. |
| CA2143 | [CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń @ no__t-0 | Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. |
| CA2144 | [CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych @ no__t-0 | Przegląd zabezpieczeń dla kodu przezroczystego nie jest tak kompletny pod względem bezpieczeństwa, jak kodu krytycznego, ponieważ przezroczysty kod nie może wykonywać czynności wrażliwych pod względem bezpieczeństwa. Zestawy, które są ładowane z tablicy bajtowej, mogą nie być niezauważone w przezroczystym kodzie, a ta tablica bajtów może zawierać krytyczny albo, co ważniejsze, krytyczny dla bezpieczeństwa kod, który musi być poddany inspekcji. |
| CA2145 | [CA2145: Metody przezroczyste nie powinny być dekoracyjne z SuppressUnmanagedCodeSecurityAttribute @ no__t-0 | Metody, które są oznaczone przez atrybut SuppressUnmanagedCodeSecurityAttribute, mają niejawny element LinkDemand umieszczony na dowolnej metodzie, który ją wywołuje. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczanie metody, która używa zabezpieczenia SuppressUnmanagedCodeSecurity przez użycie atrybutu SecurityCriticalAttribute, sprawia, że wymóg ten jest bardziej oczywisty dla obiektów wywołujących metodę. |
| CA2146 | [CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy podstawowe i interfejsy @ no__t-0 | Reguła ta jest wykorzystywana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. |
| CA2147 |[CA2147: Metody przezroczyste nie mogą używać potwierdzeń zabezpieczeń @ no__t-0 | Kod, który jest oznaczony jako SecurityTransparentAttribute, nie ma przyznanego wystarczającego uprawnienia do potwierdzenia. |
| CA2149 | [CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego @ no__t-0 | Reguła ta jest wykorzystywana dla każdej przezroczystej metody, która wywołuje bezpośrednio kod natywny, na przykład przez metodę P/Invoke. Naruszenie tej zasady prowadzi do wyjątku MethodAccessException na poziomie 2 modelu przezroczystości i pełnego żądania dla UnmanagedCode w modelu przezroczystości poziomu 1. |
| CA2151 |[CA2151: Pola o typach krytycznych powinny mieć zabezpieczenia krytyczne @ no__t-0 | Aby używać typów krytycznych pod względem zabezpieczeń, kod odwołujący się do typu musi być albo krytyczny pod względem zabezpieczeń, albo bezpieczny-krytyczny pod względem zabezpieczeń. Ta zasada obowiązuje nawet w przypadku odwołania pośredniego. Dlatego pole mające zabezpieczenia przezroczyste lub pole bezpieczne-krytyczne pod względem zabezpieczeń jest mylące, ponieważ przezroczysty kod nadal nie będzie mógł uzyskać dostępu do pola. |
| CA2200 | [CA2200: Zgłoś ponownie, aby zachować szczegóły stosu @ no__t-0 | Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona. |
| CA2201 | [CA2201: Nie zgłaszaj typów wyjątków zarezerwowanych @ no__t-0 | Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2202 | [CA2202: Nie usuwaj obiektów wiele razy, @ no__t-0 |Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu. |
| CA2204 | [CA2204: Literały powinny być napisane poprawnie @ no__t-0 | Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft. |
| CA2205 | [CA2205: Użyj zarządzanych odpowiedników Win32 API @ no__t-0 | Jest zdefiniowana metoda Invoke systemu operacyjnego i jest dostępna metoda .NET, która ma równoważne funkcje. |
| CA2207 | [CA2207: Pola statyczne typu wartości Inicjalizacja w tekście @ no__t-0 | Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny. |
| CA2208 |[CA2208: Poprawne wystąpienie wyjątków argumentów @ no__t-0 | Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException. |
| CA2210 |[CA2210: Zestawy powinny mieć prawidłowe silne nazwy @ no__t-0 | Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. |
| CA2211 |[CA2211: Pola niebędące stałymi nie powinny być widoczne @ no__t-0 | Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania, aby synchronizować dostęp do obiektu klasy. |
| CA2212 | [CA2212: Nie należy oznaczać serwisowanych składników za pomocą metody WEBMETHOD @ no__t-0 |Metoda w typie, który dziedziczy z elementu System.EnterpriseServices.ServicedComponent, jest oznaczona za pomocą atrybutu System.Web.Services.WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne. |
| CA2213 | [CA2213: Pola jednorazowe powinny zostać usunięte @ no__t-0 | Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego. |
| CA2214 | [CA2214: Nie wywołuj metod założenia w konstruktorach @ no__t-0 | Gdy konstruktor wywołuje metodę wirtualną, konstruktor wystąpienia, który wywołuje metodę, mógł nie zostać wykonany. |
| CA2215 | [CA2215: Metody Dispose powinny wywoływać klasę bazową Dispose @ no__t-0 | Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose. |
| CA2216 |[CA2216: Typy jednorazowe powinny deklarować finalizator @ no__t-0 | Typ, który implementuje element System.IDisposable i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, tak jak opisano w Object.Finalize. |
| CA2217 | [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute @ no__t-0 |Widoczne na zewnątrz wyliczenie jest oznaczone przy użyciu FlagsAttribute i ma jedną lub więcej wartości, które nie są potęgami dwójki lub kombinacji innych zdefiniowanych wartości z wyliczenia. |
| CA2218 |[CA2218: Zastąp GetHashCode przy zastępowaniu Equals równą @ no__t-0 | GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu. |
| CA2219 | [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków @ no__t-0 | Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2220 | [CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej @ no__t-0 | Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize. |
| CA2221 |[CA2221: Finalizatory powinny być chronione @ no__t-0 | Finalizatory muszą korzystać z modyfikatora dostępu „family”. |
| CA2222 | [CA2222: Nie zmniejszaj dziedziczonej widoczności składowej @ no__t-0 |Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. |
| CA2223 | [CA2223: Elementy członkowskie powinny różnić się nie tylko zwracanym typem @ no__t-0 | Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET. |
| CA2224 | [CA2224: Zastąp wartość Equals w przypadku przeciążania operatora równą @ no__t-0 | Typ publiczny implementuje operator równości, lecz nie zastępuje metody Object.Equals. |
| CA2225 | [CA2225: Przeciążenia operatorów mają nazwane alternatywy @ no__t-0 |Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski udostępnia taką samą funkcjonalność jak operator i jest dostarczany deweloperom programującym w językach, które nie obsługują przeciążonych operatorów. |
| CA2226 | [CA2226: Operatory powinny mieć symetryczne przeciążenia @ no__t-0 | Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego. |
| CA2227 |[CA2227: Właściwości kolekcji powinny być tylko do odczytu @ no__t-0 |Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. |
| CA2228 | [CA2228: Nie dostarczaj niezwolnionych formatów zasobów @ no__t-0 | Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu .NET, mogą nie być używane przez obsługiwane wersje platformy .NET. |
| CA2229 | [CA2229: Implementuj konstruktory serializacji @ no__t-0 | Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. |
| CA2230 | [CA2230: Użyj parametrów dla argumentów zmiennych @ no__t-0 | Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params. |
| CA2231 | [CA2231: Operator przeciążenia jest równy na przesłanianiu ValueType. Equals @ no__t-0 | Typ wartości zastępuje metodę Object.Equals, ale nie implementuje operatora równości. |
| CA2232 | [CA2232: Oznacz punkty wejścia Windows Forms za pomocą STAThread @ no__t-0 | STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie. |
| CA2233 |[CA2233: Operacje nie powinny przepełniać wartości @ no__t-0 | Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzania argumentów. To gwarantuje, że wynik operacji nie jest spoza zakresu możliwych wartości dla typów danych, które są zaangażowane. |
| CA2234 | [CA2234: Przekaż obiekty System. URI zamiast ciągów @ no__t-0 | Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”. Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri. |
| CA2235 | [CA2235: Oznacz wszystkie pola, które nie są możliwe do serializacji @ no__t-0 | Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. |
| CA2236 | [CA2236: Wywoływanie metod klasy bazowej dla typów ISerializable @ no__t-0 | Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora. |
| CA2237 | [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute @ no__t-0 | Aby typy były rozpoznawalne przez CLR jako możliwe do serializacji, muszą być oznaczone za pomocą atrybutu SerializableAttribute nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez implementację interfejsu ISerializable. |
| CA2238 |[CA2238: Poprawnie Implementuj metody serializacji @ no__t-0 | Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności. |
| CA2239 | [CA2239: Zapewnianie metod deserializacji dla pól opcjonalnych @ no__t-0 | Typ ma pole oznaczone za pomocą atrybutu System.Runtime.Serialization.OptionalFieldAttribute, ale nie zapewnia on metod obsługi zdarzeń deserializacji. |
| CA2240 | [CA2240: Zaimplementuj poprawnie interfejs ISerializable @ no__t-0 | Aby naprawić naruszenie tej zasady, należy się upewnić, że metoda GetObjectData jest widoczna oraz możliwa do zastąpienia i że wszystkie pola wystąpienia są uwzględnione w procesie serializacji lub jawnie oznaczone atrybutem NonSerializedAttribute. |
| CA2241 | [CA2241: Podaj poprawne argumenty do formatowania metod @ no__t-0 | Argument formatu, który jest przekazany do elementu System.String.Format, nie zawiera elementu format, który odpowiada każdemu obiektowi argumentu lub odwrotnie. |
| CA2242 |[CA2242: Testuj poprawnie wartość NaN @ no__t-0 | To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości. |
| CA2243 |[CA2243: Literały ciągu atrybutów powinny analizować się poprawnie @ no__t-0 | Parametr o typie literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikatora GUID lub wersji. |
| CA5122 | [CA5122 Deklaracje P/Invoke nie powinny być bezpieczne-krytyczne pod względem zabezpieczeń](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Metody są oznaczone jako SecuritySafeCritical, gdy wykonują operacje zależne od zabezpieczeń, ale mogą być również bezpiecznie używane przez kod przezroczystości. Kod przezroczystości może nigdy bezpośrednio nie wywołać kodu natywnego za pośrednictwem metody P/Invoke. Dlatego oznakowanie metody P/Invoke jako bezpiecznej-krytycznej pod względem zabezpieczeń nie umożliwi jej wywołania kodu przezroczystości i jest mylące dla analizy zabezpieczeń. |
