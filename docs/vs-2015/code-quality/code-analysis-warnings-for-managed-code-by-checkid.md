---
title: Ostrzeżenia analizy kodu dla kodu zarządzanego przez CheckId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
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
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ad7c2ff14a3a78b970ff8bbf7f80dfec4ee8fbb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667701"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Ostrzeżenia analizy kodu dla zarządzanego kodu dzięki CheckId
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższa tabela zawiera ostrzeżenia analizy kodu dla kodu zarządzanego przez identyfikator CheckId ostrzeżenia.

## <a name="warnings"></a>Ostrzeżenia

|CheckId|Ostrzeżenie|Opis|
|-------------|-------------|-----------------|
|CA1000|[CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Po wywołaniu statycznego elementu członkowskiego typu ogólnego dla typu trzeba określić argument typu. Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. W tych dwóch przypadkach składnia określająca argument typu jest różna i łatwo o pomyłkę.|
|CA1001|[CA1001: Typy z polami możliwymi do likwidacji powinny być możliwe do likwidacji](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Klasa deklaruje i implementuje pole wystąpienia typu System.IDisposable, ale nie implementuje interfejsu IDisposable. Klasa, która deklaruje pole IDisposable, pośrednio posiada niezarządzany zasób i powinna implementować interfejs IDisposable.|
|CA1002|[CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)|Element System. Collections. Generic. list < (of \< (T >) >) to ogólna kolekcja, która została zaprojektowana pod kątem wydajności, a nie dziedziczenia. Dlatego też lista nie zawiera wirtualnych elementów członkowskich. Zamiast powyższych powinny zostać zastosowane kolekcje ogólne, zaprojektowane do obsługi dziedziczenia.|
|CA1003|[CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)|Typ zawiera delegata zwracającego wartość void, którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs), i zawierający element docelowy zestawu Microsoft .NET Framework 2,0.|
|CA1004|[CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. W przypadku użycia wnioskowania dla wszystkich parametrów typu składnia wywoływania ogólnych i nieogólnych metod wystąpień jest identyczna; upraszcza to użycie metod ogólnych.|
|CA1005|[CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Jest to zazwyczaj oczywiste z jednym parametrem typu, jak na liście \<T >, a w niektórych przypadkach, które mają dwa parametry typu, tak jak w słowniku \<TKey TValue >. Jeśli jednak istnieją więcej niż dwa parametry typu, poziom trudności staje się zbyt wysoki dla większości użytkowników.|
|CA1006|[CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Argument typu zagnieżdżonego jest argumentem typu, który jest również typem ogólnym. Aby wywołać element członkowski, którego podpis zawiera argument typu zagnieżdżonego, użytkownik musi zainicjować wystąpienie pierwszego typu ogólnego i przekazać go do konstruktora drugiego typu ogólnego. Wymagana procedura oraz składnia są złożone i należy ich unikać.|
|CA1007|[CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)|Metoda widoczna na zewnątrz zawiera parametr przekazany przez odwołanie do typu System.Object. Użycie metody ogólnej umożliwia przekazanie wszystkich typów podlegających ograniczeniom do metody, bez uprzedniego rzutowania typu do typu parametru przekazanego przez odwołanie.|
|CA1008|[CA1008: Wyliczenia powinny zawierać wartość zero](../code-quality/ca1008-enums-should-have-zero-value.md)|Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczanie przypisane bez flag powinno definiować element członkowski przy użyciu wartości zero, tak że wartość domyślna jest prawidłową wartością wyliczenia. Jeśli wyliczenie, w którym zastosowano atrybut FlagsAttribute, definiuje element członkowski o wartości zero, powinno być nazwane „Brak”, aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu.|
|CA1009|[CA1009: Zadeklaruj poprawnie procedury obsługi zdarzeń](../code-quality/ca1009-declare-event-handlers-correctly.md)|Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu System.Object i nosi nazwę „nadawca”. Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu System.EventArgs i nosi nazwę „e”. To dane, które są skojarzone ze zdarzeniem. Metody obsługi zdarzeń nie powinny zwracać wartości; w języku programowania C# jest to wskazywane przez zwrócony typ void.|
|CA1010|[CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może zostać użyta, aby wypełnić typy generyczne kolekcji.|
|CA1011|[CA1011: Rozważ przekazanie typów podstawowych jako parametrów](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Jeśli dodatkowa funkcjonalność dostarczana przez typ parametru pochodnego nie jest wymagana, użycie typu podstawowego umożliwia szersze wykorzystanie metody.|
|CA1012|[CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany.|
|CA1013|[CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania.|
|CA1014|[CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt wymusza, że wszystkie zestawy jawnie wskazują zgodność ze specyfikacją CLS przy użyciu <xref:System.CLSCompliantAttribute>. Jeśli ten atrybut nie jest obecny w zestawie, oznacza to, że zestaw jest niezgodny.|
|CA1016|[CA1016: Oznacz zestawy atrybutem AssemblyVersion](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|@No__t_0 używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane.|
|CA1017|[CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute określa, w jaki sposób klienci COM otrzymują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie zastąpić dla poszczególnych typów i elementów członkowskich typu. Jeśli ten atrybut jest nieobecny, zawartość zestawu jest widoczna dla klientów COM.|
|CA1018|[CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Podczas definiowania atrybutu niestandardowego należy go oznaczyć przy użyciu elementu AttributeUsageAttribute, aby wskazać, w którym miejscu kodu źródłowego ma być on zastosowany. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie.|
|CA1019|[CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis.|
|CA1020|[CA1020: Unikaj przestrzeni nazw z kilkoma typami](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Należy się upewnić, że każda z przestrzeni nazw posiada organizację logiczną i że istnieje uzasadniony powód, aby umieszczać typy w słabo wypełnionych przestrzeniach nazw.|
|CA1021|[CA1021: Unikaj parametrów out](../code-quality/ca1021-avoid-out-parameters.md)|Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między parametrami out i ref nie jest powszechnie zrozumiała.|
|CA1023|[CA1023: Indeksatory nie powinny być wielowymiarowe](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indeksatory (właściwości indeksowane) powinny używać pojedynczego indeksu. Indeksatory wielowymiarowe mogą znacznie zmniejszyć użyteczność biblioteki.|
|CA1024|[CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)|Metody publiczne lub chronione mają nazwę zaczynającą się od „Get”, nie posiadają parametrów i zwracają wartość, która nie jest tablicą. Metoda ta może być dobrym kandydatem na właściwość.|
|CA1025|[CA1025: Zastąp powtarzające się argumenty tablicą parametrów](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Użyj tablicy parametrów zamiast powtarzających się argumentów, gdy znana jest dokładna liczba argumentów i argumenty zmiennych są tego samego typu lub mogą być przekazane jako ten sam typ.|
|CA1026|[CA1026: Nie należy używać parametrów domyślnych](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Metody z wykorzystaniem parametrów domyślnych są dozwolone w ramach CLS, jednak CLS umożliwia kompilatorom ignorowanie wartości, które są przypisane do tych parametrów. Aby zapewnić odpowiednie zachowanie w językach programowania, metody z wykorzystaniem parametrów domyślnych należy zastąpić przeciążeniami metody, które dostarczają parametry domyślne.|
|CA1027|[CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj atrybut FlagsAttribute do wyliczenia, gdy jego stałe nazwane mogą zostać sensownie połączone.|
|CA1028|[CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie typ danych System.Int32 jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to wymagane ani zalecane dla większości scenariuszy.|
|CA1030|[CA1030: Używaj zdarzeń wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1030-use-events-where-appropriate.md)|Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, powinna ona zostać wywołana przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.|
|CA1031|[CA1031: Nie przechwytuj ogólnych typów wyjątków](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Ogólne wyjątki nie powinny być przechwytywane. Przechwytuj wyjątek bardziej precyzyjny lub zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w bloku catch.|
|CA1032|[CA1032: Zaimplementuj standardowe konstruktory wyjątku](../code-quality/ca1032-implement-standard-exception-constructors.md)|Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków.|
|CA1033|[CA1033: Typy podrzędne powinny móc wywoływać metody interfejsu](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.|
|CA1034|[CA1034: Typy zagnieżdżone nie powinny być widoczne](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Typ zagnieżdżony to typ, który jest zadeklarowany wewnątrz zakresu innego typu. Typy zagnieżdżone są przydatne w przypadku hermetyzacji szczegółów implementacji prywatnej typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz.|
|CA1035|[CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Ta reguła wymaga implementacji ICollection w celu dostarczenia mocno typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ Object w przypadku używania funkcjonalności dostarczonej przez interfejs. Ta reguła zakłada, że typ, który implementuje ICollection, robi to tak, aby zarządzać kolekcją wystąpień typów mocniejszych niż Object.|
|CA1036|[CA1036: Przesłoń metody dla typów obsługujących porównywanie](../code-quality/ca1036-override-methods-on-comparable-types.md)|Typ publiczny lub chroniony implementuje interfejs System.IComparable. Nie zastępuje on metody Object.Equals ani nie przeciąża specyficznego dla języka operatora równości, nierówności, mniejsze lub większe niż.|
|CA1038|[CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Ta reguła wymaga implementacji IEnumerator w celu dostarczenia silnie typizowanej wersji właściwości Current, tak aby użytkownicy nie musieli rzutować wartości zwróconej na typ silny w przypadku używania funkcjonalności dostarczonej przez interfejs.|
|CA1039|[CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)|Ta reguła wymaga implementacji IList w celu dostarczenia silnie typizowanych elementów członkowskich, tak aby użytkownicy nie musieli rzutować argumentów na typ System.Object w przypadku używania funkcjonalności dostarczonej przez interfejs.|
|CA1040|[CA1040: Unikaj pustych interfejsów](../code-quality/ca1040-avoid-empty-interfaces.md)|Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich; dlatego też nie definiuje kontraktu, który można zaimplementować.|
|CA1041|[CA1041: Określ komunikat ObsoleteAttribute](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Typ lub element członkowski jest oznaczony za pomocą atrybutu System.ObsoleteAttribute, który nie ma określonej właściwości ObsoleteAttribute.Message. Podczas kompilowania typu lub elementu członkowskiego, który jest oznaczony za pomocą ObsoleteAttribute, wyświetlana jest właściwość Wiadomość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim.|
|CA1043|[CA1043: Używaj argumentu integral lub string dla indeksatorów](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Indeksatory (właściwości indeksowane) powinny używać dla indeksu typów całkowitych lub ciągu. Typy te są zwykle używane do indeksowania struktur danych i zwiększają one użyteczność biblioteki. Użycie typu Object powinno zostać ograniczone do przypadków, w których nie może zostać określony typ całkowity lub ciąg w czasie projektowania.|
|CA1044|[CA1044: Właściwości nie powinny być tylko do zapisu](../code-quality/ca1044-properties-should-not-be-write-only.md)|Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Dzieje się tak dlatego, że umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwianie przeglądania tej wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność.|
|CA1045|[CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Architekci biblioteki, którzy tworzą dla wszystkich, nie powinni oczekiwać od użytkowników dobrej znajomości parametrów out lub ref.|
|CA1046|[CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt.|
|CA1047|[CA1047: Nie deklaruj składowych chronionych w typach zapieczętowanych](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Z definicji po typach zapieczętowanych nie można dziedziczyć, co oznacza, że nie można wywołać metody chronionej na typach zapieczętowanych.|
|CA1048|[CA1048: Nie deklaruj składowych wirtualnych w typach zapieczętowanych](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Metody wirtualne są zadeklarowane w typach tak, aby typy dziedziczące mogły zmieniać implementację metod wirtualnych. Z definicji po typie zapieczętowanym nie można dziedziczyć. Powoduje to, że metoda wirtualna w typie zapieczętowanym jest całkowicie nieprzydatna.|
|CA1049|[CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, które przydzielają zasoby niezarządzane, powinny implementować interfejs IDisposable, umożliwiając metodom wywołującym zwalnianie tych zasobów na żądanie i skrócenie czasu istnienia obiektów, które zawierają te zasoby.|
|CA1050|[CA1050: Deklaruj typy w przestrzeniach nazw](../code-quality/ca1050-declare-types-in-namespaces.md)|Typy są zadeklarowane w przestrzeniach nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów.|
|CA1051|[CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być prywatne lub wewnętrzne i dostępne przy użyciu właściwości.|
|CA1052|[CA1052: Statyczne typy przechowujące powinny być zapieczętowane](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowany za pomocą modyfikatora sealed (C# Reference) (NotInheritable). Typ, po którym nie będzie dziedziczenia, powinien być oznakowany przy użyciu modyfikatora sealed, aby zapobiec użyciu go jako typu podstawowego.|
|CA1053|[CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny. Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Przeciążenie typu ciąg powinno wywoływać, dla bezpieczeństwa, przeciążenie jednolitego identyfikatora zasobów (URI) przy użyciu argumentu typu ciąg.|
|CA1054|[CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, powinno zostać dostarczone odpowiadające przeciążenie, pobierające wystąpienie klasy URI, które dostarcza te usługi w bezpieczny sposób.|
|CA1055|[CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Reguła ta zakłada, że metoda zwraca identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób.|
|CA1056|[CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Reguła ta zakłada, że właściwość reprezentuje identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób.|
|CA1057|[CA1057: Przeciążenia identyfikatora URI w postaci ciągu wywołują przeciążenia metody System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpieniem parametru typu ciąg parametrem System.Uri. Przeciążenie, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia, które przyjmuje parametr identyfikatora URI.|
|CA1058|[CA1058: Typy nie powinny rozszerzać pewnych typów podstawowych](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Użyj jednej z alternatyw.|
|CA1059|[CA1059: Składowe nie powinny ujawniać pewnych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Konkretny typ jest typem posiadającym pełną implementację i dlatego może zostać utworzone jego wystąpienie. Aby włączyć powszechne użycie elementu członkowskiego, zamień konkretny typ, używając sugerowanego interfejsu.|
|CA1060|[CA1060: Przenieś wywołania P/Invoke do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Metody wywoływania platformy, takie jak te, które są oznaczone za pomocą atrybutu System. Runtime. InteropServices. DllImportAttribute lub metod, które są zdefiniowane za pomocą słowa kluczowego Declare w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], uzyskują dostęp do kodu niezarządzanego. Metody te powinny być klasami NativeMethods, SafeNativeMethods lub UnsafeNativeMethods.|
|CA1061|[CA1061: Nie ukrywaj metod klasy podstawowej](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Metoda w typie podstawowym jest ukryta przez metodę o identycznej nazwie typu pochodnego, gdy sygnatura parametru metody pochodnej różni się tylko typami, które są słabiej dziedziczone niż odpowiadające typy w sygnaturze parametru metody podstawowej.|
|CA1062|[CA1062 Zweryfikuj argumenty metod publicznych](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Wszystkie argumenty odwołania, które są przekazywane do metody widocznej na zewnątrz, powinny być sprawdzane pod kątem wartości null.|
|CA1063|[CA1063: Zaimplementuj poprawnie interfejs IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md)|Wszystkie typy IDisposable powinny poprawnie implementować wzorzec Dispose.|
|CA1064|[CA1064: Wyjątki powinny być publiczne](../code-quality/ca1064-exceptions-should-be-public.md)|Wyjątek wewnętrzny jest widoczny tylko wewnątrz własnego zakresu wewnętrznego. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wyjątek wewnętrzny jest dziedziczony z T:System.Exception, T:System.SystemException lub T:System.ApplicationException, kod zewnętrzny nie ma wystarczających informacji, aby wiedzieć, co należy zrobić z wyjątkiem.|
|CA1065|[CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Metoda, od której nie oczekiwano zgłaszania wyjątków, zgłasza wyjątek.|
|CA1300|[CA1300: Określ wyliczenie MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Aby poprawnie wyświetlić okno komunikatu dla kultur stosujących pismo od prawej do lewej, członkowie RightAlign i RtlReading wyliczenia MessageBoxOptions muszą być przekazani do metody Show.|
|CA1301|[CA1301: Unikaj duplikowania akceleratorów](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane.|
|CA1302|[CA1302: Nie umieszczaj w kodzie na stałe ciągów specyficznych dla ustawień regionalnych](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Wyliczenie System.Environment.SpecialFolder zawiera elementy, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w poszczególnych systemach operacyjnych; użytkownik może zmienić niektóre z tych lokalizacji; lokalizacje są zlokalizowane. Metoda Environment.GetFolderPath zwraca lokalizacje, które są skojarzone z wyliczeniem Environment.SpecialFolder, zlokalizowane i odpowiednie dla danego komputera.|
|CA1303|[CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Metoda widoczna na zewnątrz przekazuje literał ciągu jako parametr do konstruktora lub metody w bibliotece klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] i ten ciąg powinien być Lokalizowalny.|
|CA1304|[CA1304: Określ klasę CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|
|CA1305|[CA1305: Określ interfejs IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|
|CA1306|[CA1306: Określ ustawienia regionalne dla typów danych](../code-quality/ca1306-set-locale-for-data-types.md)|Ustawienia regionalne określą specyficzne dla kultur elementy prezentacji danych, takie jak formatowanie, które jest używane dla wartości liczbowych, symbole walut i porządek sortowania. Podczas tworzenia elementu DataTable lub DataSet należy jawnie ustawić ustawienia regionalne.|
|CA1307|[CA1307: Określ wyliczenie StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison.|
|CA1308|[CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery.|
|CA1309|[CA1309: Używaj wyliczenia StringComparison stosującego reguły sortowania oparte na wartości](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny.|
|CA1400|[CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece.|
|CA1401|[CA1401: Metody P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Metoda publiczna lub chroniona w typie publicznym ma atrybut System. Runtime. InteropServices. DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Takie metody nie powinny być udostępniane.|
|CA1402|[CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń.|
|CA1403|[CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typ wartości widoczny dla modelu COM jest oznaczony za pomocą atrybutu System. Runtime. InteropServices. StructLayoutAttribute o wartości LayoutKind. Auto. Układ tych typów może się zmieniać między wersjami [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], co spowoduje przerwanie klientów COM, którzy oczekują określonego układu.|
|CA1404|[CA1404: Wywołaj metodę GetLastError natychmiast po wywołaniu P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wykonano wywołanie metody Marshal. metodę GetLastWin32Error lub równoważnej funkcji GetLastError [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)], a bezpośrednio poprzednie wywołanie nie jest metodą Invoke systemu operacyjnego.|
|CA1405|[CA1405: Typy podstawowe typu widocznego dla modelu COM powinny być widoczne dla modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM.|
|CA1406|[CA1406: Unikaj argumentów typu Int64 w przypadku klientów programu Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Klienci Visual Basic 6 COM nie mogą uzyskać dostępu do 64-bitowych liczb całkowitych.|
|CA1407|[CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Model COM nie obsługuje metod statycznych.|
|CA1408|[CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania.|
|CA1409|[CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego.|
|CA1410|[CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Typ deklaruje metodę, która jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute, ale nie deklaruje metody oznaczonej za pomocą atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute lub odwrotnie.|
|CA1411|[CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metoda oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute lub atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute jest widoczna na zewnątrz.|
|CA1412|[CA1412: Oznacz interfejsy ComSource jako interfejsy IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch.|
|CA1413|[CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń.|
|CA1414|[CA1414: Oznacz argumenty logiczne metody P/Invoke za pomocą atrybutu MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym.|
|CA1415|[CA1415: Poprawnie zadeklaruj metody P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Ta reguła szuka systemu operacyjnego wywoływanie deklaracji metody, które są przeznaczone dla funkcji [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)], które mają wskaźnik do POKRYWAJĄCego się z parametrami struktury, a odpowiedni parametr zarządzany nie jest wskaźnikiem do struktury system. Threading. NativeOverlapped.|
|CA1500|[CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Metoda wystąpienia deklaruje parametr lub zmienną lokalną, których nazwa pasuje do pola wystąpienia typu deklarującego, prowadząc do błędów.|
|CA1501|[CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)|Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania.|
|CA1502|[CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502-avoid-excessive-complexity.md)|Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych.|
|CA1504|[CA1504: Przejrzyj mylące nazwy pól](../code-quality/ca1504-review-misleading-field-names.md)|Nazwa pola wystąpienia zaczyna się od "s_" lub nazwa statycznego pola udostępnionego w Visual Basic) rozpoczyna się od "m_".|
|CA1505|[CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505-avoid-unmaintainable-code.md)|Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania.|
|CA1506|[CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.|
|CA1600|[CA1600: Nie używaj priorytetu procesu bezczynności](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają System.Diagnostics.ProcessPriorityClass.Idle, zajmują procesor, gdy może on być bezczynny, a zatem będą blokować stan gotowości.|
|CA1601|[CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.|
|CA1700|[CA1700: Nie nadawaj wartościom wyliczenia nazwy „Reserved”](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą.|
|CA1701|[CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Każdy wyraz w ciągu zasobu jest podzielony na tokeny oparte na obudowie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły.|
|CA1702|[CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.|
|CA1703|[CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|CA1704|[CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|CA1707|[CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.|
|CA1708|[CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter.|
|CA1709|[CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Według konwencji nazwy parametrów używają notacji CamelCase, a przestrzenie nazw, typy i elementy członkowskie notacji PascalCase.|
|CA1710|[CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają przyrostek skojarzony z typem bazowym lub interfejsem.|
|CA1711|[CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.|
|CA1712|[CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Nazwy elementów członkowskich wyliczenia nie mają prefiksu od nazwy typu, ponieważ narzędzia programistyczne dostarczają informacje na temat typu.|
|CA1713|[CA1713 Zdarzenia nie powinny mieć prefiksu Before ani After](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji.|
|CA1714|[CA1714: Wyliczenia flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Publiczne wyliczenie ma atrybut System.FlagsAttribute, a jego nazwa nie kończy się na „s”. Typy oznaczone przy użyciu FlagsAttribute mają nazwy w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość.|
|CA1715|[CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Nazwa interfejsu, który jest widoczny na zewnątrz, nie zaczyna się od wielkiej litery „I”. Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery „T”.|
|CA1716|[CA1716: Identyfikatory nie powinny odpowiadać słowom kluczowym](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego.|
|CA1717|[CA1717: Tylko wyliczenia FlagsAttribute powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia.|
|CA1719|[CA1719: Nazwy parametrów nie powinny odpowiadać nazwom składowych](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.|
|CA1720|[CA1720: Identyfikatory nie powinny zawierać nazw typów](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych.|
|CA1721|[CA1721: Nazwy właściwości nie powinny odpowiadać metodom Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.|
|CA1722|[CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu.|
|CA1724|[CA1724: Nazwy typów nie powinny pasować do przestrzeni nazw](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw, które są zdefiniowane w bibliotece klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.|
|CA1725|[CA1725: Nazwy parametrów powinny pasować do deklaracji podstawowej](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.|
|CA1726|[CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie „Flag” lub „Flags”.|
|CA1800|[CA1800: Nie rzutuj niepotrzebnie](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji.|
|CA1801|[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody zawiera parametr, który nie jest używany w jej treści.|
|CA1802|[CA1802: Używaj literałów wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1802-use-literals-where-appropriate.md)|Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) i jest inicjowane przy użyciu wartości, która jest obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na wartość const (const w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), tak aby była obliczana w czasie kompilacji, a nie w czasie wykonywania.|
|CA1804|[CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)|Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.|
|CA1806|[CA1806: Nie ignoruj wyników metod](../code-quality/ca1806-do-not-ignore-method-results.md)|Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany.|
|CA1809|[CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)|Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”. Aby zwiększyć szansę, że wszystkie zmienne lokalne są przechowywane, Ogranicz liczbę zmiennych lokalnych do 64.|
|CA1810|[CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność.|
|CA1811|[CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)|Prywatny lub wewnętrzny element członkowski (na poziomie zestawu) nie ma obiektów wywołujących w zestawie; nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego ani przez obiekt delegowany.|
|CA1812|[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.|
|CA1813|[CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)|Biblioteka klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zapewnia metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność.|
|CA1814|[CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy, mogą mieć różne rozmiary, co zapewnia większą oszczędność miejsca w przypadku niektórych zestawów danych.|
|CA1815|[CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals.|
|CA1816|[CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (mi w Visual Basic).|
|CA1819|[CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)|Tablice zwracane przez właściwości nie są zabezpieczone przed zapisem, nawet gdy mają właściwość tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości.|
|CA1820|[CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals.|
|CA1821|[CA1821: Usuwaj puste finalizatory](../code-quality/ca1821-remove-empty-finalizers.md)|Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator powoduje dodatkowe obciążenie i nie zapewnia żadnych korzyści.|
|CA1822|[CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822-mark-members-as-static.md)|Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone jako statyczne (udostępnione w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność.|
|CA1823|[CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823-avoid-unused-private-fields.md)|Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.|
|CA1824|[CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.|
|CA1900|[CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Reguła ta sprawdza, czy struktury, które są zadeklarowane przez użycie jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych.|
|CA1901|[CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Ta reguła oblicza rozmiar każdego parametru oraz wartości zwróconej przez metodę P/Invoke i sprawdza, czy rozmiar parametru jest poprawny podczas przekazywania do kodu niezarządzanego w 32-bitowych i 64-bitowych systemach operacyjnych.|
|CA1903|[CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|
|CA2000|[CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|
|CA2001|[CA2001: Unikaj wywoływania problematycznych metod](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.|
|CA2002|[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|
|CA2003|[CA2003: Nie traktuj włókien jak wątków](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Zarządzany wątek jest traktowany jako wątek [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)].|
|CA2004|[CA2004: Usuń wywołania funkcji GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Podczas konwertowania użycia SafeHandle należy usunąć wszystkie wywołania do GC.KeepAlive (obiekt). W tym przypadku klasy nie powinny wywołać GC.KeepAlive. Założono, że nie mają one finalizatorów, ale polegają na elemencie SafeHandle, który ma sfinalizować dla nich dojście systemu operacyjnego.|
|CA2006|[CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane.|
|CA2100|[CA2100: Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Metoda ustawia właściwość System.Data.IDbCommand.CommandText przez użycie ciągu, który jest zbudowany z argumentem ciągu do metody. Zasada ta zakłada, że argument ciągu zawiera dane wejściowe użytkownika. Ciąg polecenia SQL zbudowany z danych wejściowych użytkownika jest narażony na ataki przez wstrzyknięcie kodu SQL.|
|CA2101|[CA2101: Określ marshaling dla argumentów ciągu wywołania P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Element członkowski wywołania platformy zezwala na dostęp częściowo zaufanych wywołań, ma parametr ciągu i nie kieruje jawnie tego ciągu. Może to spowodować potencjalne luki w zabezpieczeniach.|
|CA2102|[CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Element członkowski w zestawie, który nie jest oznaczony za pomocą atrybutu RuntimeCompatibilityAttribute lub jest oznaczony jako RuntimeCompatibility(WrapNonExceptionThrows = false), zawiera blok catch obsługujący wyjątek System.Exception i nie zawiera bezpośrednio następującego ogólnego bloku catch.|
|CA2103|[CA2103: Przejrzyj zabezpieczenia imperatywne](../code-quality/ca2103-review-imperative-security.md)|Metoda używa imperatywnych zabezpieczeń i może konstruować uprawnienia za pomocą informacji o stanie lub wartości zwrotnych, które można zmienić, dopóki żądanie jest aktywne. Należy używać zabezpieczeń deklaracyjnych wszędzie, gdzie to możliwe.|
|CA2104|[CA2104: Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej. Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane.|
|CA2105|[CA2105: Pola tablicy nie powinny być tylko do odczytu](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Po zastosowaniu modyfikatora tylko do odczytu (ReadOnly w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) do pola, które zawiera tablicę, pola nie można zmienić, aby odwoływać się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu.|
|CA2106|[CA2106: Zabezpiecz asercje](../code-quality/ca2106-secure-asserts.md)|Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym. Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie.|
|CA2107|[CA2107: Przejrzyj użycie akcji Deny i Permit Only](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Metody PermitOnly oraz akcje zabezpieczeń CodeAccessPermission. Deny powinny być używane tylko przez te osoby, które mają zaawansowaną wiedzę o zabezpieczeniach [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń.|
|CA2108|[CA2108: Przejrzyj zabezpieczenia deklaratywne typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Publiczny lub chroniony typ wartości jest zabezpieczony przez dostęp do danych lub zapotrzebowanie na łącza.|
|CA2109|[CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109-review-visible-event-handlers.md)|Wykryto publiczną lub chronioną metodę obsługi zdarzeń. Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne.|
|CA2111|[CA2111: Wskaźniki nie powinny być widoczne](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźnik nie jest prywatny, wewnętrzny ani tylko do odczytu. Złośliwy kod może zmienić wartość wskaźnika, co potencjalnie umożliwia dostęp do dowolnego miejsca w pamięci lub powoduje błędy aplikacji lub systemu.|
|CA2112|[CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez zapotrzebowania na łącza. Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu.|
|CA2114|[CA2114: Zabezpieczenie metody powinno być nadzbiorem typu](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Metoda nie powinna mieć zabezpieczeń deklaratywnych zarówno na poziomie metody, jak i na poziomie typu dla tej samej akcji.|
|CA2115|[CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Ta reguła wykrywa błędy, które mogą wystąpić, ponieważ kończy się działanie niezarządzanego zasobu, a wciąż jest on używany w kodzie niezarządzanym.|
|CA2116|[CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Gdy atrybut APTCA (AllowPartiallyTrustedCallersAttribute) jest obecny w zestawie całkowicie zaufanym i wykonuje kod w innym zestawie, który nie zezwala na dostęp częściowo zaufanych wywołań, mogą zostać wykorzystane luki w zabezpieczeniach.|
|CA2117|[CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Gdy atrybut APTCA jest obecny w pełni zaufanym zestawie, a typ w zestawie dziedziczy z typu, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest wykorzystanie luk w zabezpieczeniach.|
|CA2118|[CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Atrybut SuppressUnmanagedCodeSecurityAttribute zmienia domyślne zachowanie systemu zabezpieczeń dla elementów członkowskich wykonujących kod niezarządzany, który używa wywołań międzyoperacyjnych COM lub systemu operacyjnego. Ten atrybut jest używany przede wszystkim do zwiększenia wydajności, wiąże się z nimi jednak znaczące zagrożenie bezpieczeństwa.|
|CA2119|[CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Dziedziczony typ publiczny zapewnia implementację metody wewnętrznej (zaprzyjaźnionej w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Aby naprawić naruszenie tej zasady, należy zapobiegać zastąpieniu metody poza zestawem.|
|CA2120|[CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)|Typ ten ma konstruktor, który przyjmuje obiekt System.Runtime.Serialization.SerializationInfo i obiekt System.Runtime.Serialization.StreamingContext (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale jeden lub kilka regularnych konstruktorów typu jest zabezpieczonych.|
|CA2121|[CA2121: Konstruktory statyczne powinny być prywatne](../code-quality/ca2121-static-constructors-should-be-private.md)|System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie.|
|CA2122|[CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Element członkowski publiczny lub chroniony ma zapotrzebowanie na łącza i jest wywoływany przez element członkowski, który nie sprawdza zabezpieczeń. Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego.|
|CA2123|[CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Ta reguła dopasowuje metodę do jej metody podstawowej, która jest interfejsem lub metodą wirtualną innego typu, a następnie porównuje zapotrzebowania na łącza na każdym z nich. Jeśli zasada ta jest naruszona, złośliwy wywołujący może pominąć zapotrzebowanie na łącza przez wywołanie niezabezpieczonej metody.|
|CA2124|[CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Metoda publiczna lub chroniona zawiera blok try/finally. Wygląda na to, że blok finally resetuje stan zabezpieczeń i sam nie jest ujęty w bloku finally.|
|CA2126|[CA2126: Żądania LinkDemand dla typu wymagają żądań dziedziczenia](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Niezamknięty typ publiczny jest chroniony za pomocą zapotrzebowania na łącza i ma metodę, którą można zastąpić. Ani typ, ani metoda nie są chronione za pomocą żądania dziedziczenia.|
|CA2127|[CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Krytyczny kod nie może wystąpić w zestawie, który jest w 100% przezroczysty. Reguła ta analizuje zestawy w 100% przezroczyste dla adnotacji SecurityCritical na poziomie typu, pola i metody.|
|CA2128|[CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Reguła ta analizuje wszystkie metody i typy w zestawie, który jest w 100% przezroczysty lub mieszany przezroczysto-krytyczny i zaznacza deklaratywne lub imperatywne użycie potwierdzenia.|
|CA2129|[CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Metody, które są oznaczone atrybutem SecurityTransparentAttribute, wywołują niepubliczne elementy członkowskie, które są oznaczone jako SecurityCritical. Ta reguła analizuje wszystkie metody i typy w zestawie mieszanym przezroczysto-krytycznym i oznacza wszelkie wywołania z przezroczystego kodu do niepublicznego krytycznego kodu, który nie jest oznaczony jako SecurityTreatAsSafe.|
|CA2130|[CA2130: Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej.|
|CA2131|[CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typ uczestniczy w równoważniku typu i albo sam typ, albo element członkowski, albo pole, albo typ jest oznaczony za pomocą atrybutu SecurityCriticalAttribute. Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach, które zawierają metody krytyczne lub pola uczestniczące w równoważeniu typu. Gdy CLR wykryje taki typ, nie ładuje go z wyjątkiem TypeLoadException w czasie wykonywania. Zazwyczaj ta reguła jest wykorzystywana tylko wtedy, gdy użytkownicy ręcznie implementują równoważnik typu, zamiast opierać się wykonaniu równoważnika typu przez tlbimp i kompilatory.|
|CA2132|[CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Typy i elementy członkowskie, które mają atrybut SecurityCriticalAttribute, nie mogą być używane przez kod aplikacji Silverlight. Typy i elementy o kluczowym znaczeniu zabezpieczeń mogą być używane tylko przez zaufany kod w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.|
|CA2133|[CA2133: Delegaci muszą być powiązani z metodami ze spójną przezroczystością](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|To ostrzeżenie jest zgłaszane na metodzie, która wiąże obiekt delegowany, oznaczony za pomocą atrybutu SecurityCriticalAttribute, do metody, która jest przezroczysta lub oznaczona za pomocą SecuritySafeCriticalAttribute. Ostrzeżenie jest także zgłaszane na metodzie, która wiąże obiekt delegowany przezroczysty lub bezpieczny-krytyczny do metody krytycznej.|
|CA2134|[CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Ta reguła jest wykorzystywana, gdy metoda oznaczona za pomocą atrybutu SecurityCriticalAttribute zastępuje metodę, która jest przezroczysta lub oznaczona za pomocą atrybutu SecuritySafeCriticalAttribute. Reguła ta jest też wykorzystywana, gdy metoda przezroczysta lub oznaczona przy użyciu atrybutu SecuritySafeCriticalAttribute zastępuje metodę oznaczoną za pomocą atrybutu SecurityCriticalAttribute. Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs.|
|CA2135|[CA2135: Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używania elementu LinkDemands do wymuszania zabezpieczeń w czasie kompilacji JIT, należy oznaczyć metody, typy i pola za pomocą atrybutu SecurityCriticalAttribute.|
|CA2136|[CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu o większym zakresie mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład klasa, która jest oznaczona za pomocą atrybutu SecurityCriticalAttribute, nie może zawierać metody oznaczonej za pomocą atrybutu SecuritySafeCriticalAttribute.|
|CA2137|[CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie. Ta reguła jest wykorzystywana, kiedy przezroczysty pod względem zabezpieczeń kod próbuje wykonać niemożliwy do zweryfikowania Microsoft Intermediate Language (MISL). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL.|
|CA2138|[CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute.|
|CA2139|[CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Ta reguła jest wykorzystywana przez dowolną metodę, która jest przejrzysta i próbuje obsłużyć wyjątek uszkadzający proces przy użyciu atrybutu HandleProcessCorruptedStateExceptionsAttribute. Wyjątek uszkadzający proces to klasyfikacja wyjątków CLR w wersji 4.0 wątków takich jak AccessViolationException. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej.|
|CA2140|[CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Element kodu, który jest oznaczony za pomocą atrybutu SecurityCriticalAttribute, jest krytyczny dla bezpieczeństwa. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli przezroczysty typ próbuje użyć typu krytycznego dla zabezpieczeń, zgłaszane są wyjątki TypeAccessException, MethodAccessException lub FieldAccessException.|
|CA2141|[CA2141: Metody przezroczyste nie mogą spełniać żądań LinkDemand](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Przezroczysta pod względem bezpieczeństwa metoda wywołuje metodę w zestawie, który nie jest oznaczony za pomocą APTCA lub spełnia LinkDemand dla typu lub metody.|
|CA2142|[CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Reguła ta jest zgłaszana na przezroczystej metodzie, które wymaga elementu LinkDemands, aby uzyskać do niej dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień.|
|CA2143|[CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania.|
|CA2144|[CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Przegląd zabezpieczeń dla kodu przezroczystego nie jest tak kompletny pod względem bezpieczeństwa, jak kodu krytycznego, ponieważ przezroczysty kod nie może wykonywać czynności wrażliwych pod względem bezpieczeństwa. Zestawy, które są ładowane z tablicy bajtowej, mogą nie być niezauważone w przezroczystym kodzie, a ta tablica bajtów może zawierać krytyczny albo, co ważniejsze, krytyczny dla bezpieczeństwa kod, który musi być poddany inspekcji.|
|CA2145|[CA2145: Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Metody, które są oznaczone przez atrybut SuppressUnmanagedCodeSecurityAttribute, mają niejawny element LinkDemand umieszczony na dowolnej metodzie, który ją wywołuje. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczanie metody, która używa zabezpieczenia SuppressUnmanagedCodeSecurity przez użycie atrybutu SecurityCriticalAttribute, sprawia, że wymóg ten jest bardziej oczywisty dla obiektów wywołujących metodę.|
|CA2146|[CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Reguła ta jest wykorzystywana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa.|
|CA2147|[CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Kod, który jest oznaczony jako SecurityTransparentAttribute, nie ma przyznanego wystarczającego uprawnienia do potwierdzenia.|
|CA2149|[CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Reguła ta jest wykorzystywana dla każdej przezroczystej metody, która wywołuje bezpośrednio kod natywny, na przykład przez metodę P/Invoke. Naruszenie tej zasady prowadzi do wyjątku MethodAccessException na poziomie 2 modelu przezroczystości i pełnego żądania dla UnmanagedCode w modelu przezroczystości poziomu 1.|
|CA2151|[CA2151: Pola typu krytycznego powinny być krytyczne pod względem zabezpieczeń](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md)|Aby używać typów krytycznych pod względem zabezpieczeń, kod odwołujący się do typu musi być albo krytyczny pod względem zabezpieczeń, albo bezpieczny-krytyczny pod względem zabezpieczeń. Ta zasada obowiązuje nawet w przypadku odwołania pośredniego. Dlatego pole mające zabezpieczenia przezroczyste lub pole bezpieczne-krytyczne pod względem zabezpieczeń jest mylące, ponieważ przezroczysty kod nadal nie będzie mógł uzyskać dostępu do pola.|
|CA2200|[CA2200: Zgłoś ponownie wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona.|
|CA2201|[CA2201: Nie wywołuj zastrzeżonych typów wyjątku](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania.|
|CA2202|[CA2202: Nie likwiduj obiektów wiele razy](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu.|
|CA2204|[CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.|
|CA2205|[CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Metoda Invoke systemu operacyjnego jest zdefiniowana, a metoda, która ma równoważne funkcje, znajduje się w bibliotece klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|
|CA2207|[CA2207: Pola statyczne typu wartości inicjuj bezpośrednio](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.|
|CA2208|[CA2208: Poprawnie twórz wystąpienia wyjątków argumentów](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException.|
|CA2210|[CA2210: Zestawy powinny mieć prawidłowe silne nazwy](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze.|
|CA2211|[CA2211: Pola, które nie są stałe, nie powinny być widoczne](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania, aby synchronizować dostęp do obiektu klasy.|
|CA2212|[CA2212: Nie oznaczaj obsługiwanych składników za pomocą atrybutu WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Metoda w typie, który dziedziczy z elementu System.EnterpriseServices.ServicedComponent, jest oznaczona za pomocą atrybutu System.Web.Services.WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne.|
|CA2213|[CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego.|
|CA2214|[CA2214: Nie wywołuj metod, które można przesłonić, w konstruktorach](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Gdy konstruktor wywołuje metodę wirtualną, konstruktor wystąpienia, który wywołuje metodę, mógł nie zostać wykonany.|
|CA2215|[CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose.|
|CA2216|[CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typ, który implementuje element System.IDisposable i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, tak jak opisano w Object.Finalize.|
|CA2217|[CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Widoczne na zewnątrz wyliczenie jest oznaczone przy użyciu FlagsAttribute i ma jedną lub więcej wartości, które nie są potęgami dwójki lub kombinacji innych zdefiniowanych wartości z wyliczenia.|
|CA2218|[CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu.|
|CA2219|[CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątku](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania.|
|CA2220|[CA2220: Finalizatory powinny wywoływać finalizatory klasy podstawowej](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize.|
|CA2221|[CA2221: Finalizatory powinny być chronione](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory muszą korzystać z modyfikatora dostępu „family”.|
|CA2222|[CA2222: Nie obniżaj dziedziczonej widoczności składowych](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej.|
|CA2223|[CA2223: Składniki powinny różnić się nie tylko zwracanym typem](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET.|
|CA2224|[CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Typ publiczny implementuje operator równości, lecz nie zastępuje metody Object.Equals.|
|CA2225|[CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski udostępnia taką samą funkcjonalność jak operator i jest dostarczany deweloperom programującym w językach, które nie obsługują przeciążonych operatorów.|
|CA2226|[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego.|
|CA2227|[CA2227: Właściwości kolekcji powinny być tylko do odczytu](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków.|
|CA2228|[CA2228: Nie dostarczaj nieopublikowanych formatów zasobów](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnej [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] mogą nie być używane przez obsługiwane wersje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|
|CA2229|[CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)|Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.|
|CA2230|[CA2230: Użyj parametrów dla argumentów zmiennych](../code-quality/ca2230-use-params-for-variable-arguments.md)|Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params.|
|CA2231|[CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Typ wartości zastępuje metodę Object.Equals, ale nie implementuje operatora równości.|
|CA2232|[CA2232: Oznacz punkty wejścia platformy Windows Forms za pomocą atrybutu STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie.|
|CA2233|[CA2233: Operacje nie powinny powodować przepełnienia](../code-quality/ca2233-operations-should-not-overflow.md)|Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzania argumentów. To gwarantuje, że wynik operacji nie jest spoza zakresu możliwych wartości dla typów danych, które są zaangażowane.|
|CA2234|[CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”. Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri.|
|CA2235|[CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.|
|CA2236|[CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora.|
|CA2237|[CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Aby typy były rozpoznawalne przez CLR jako możliwe do serializacji, muszą być oznaczone za pomocą atrybutu SerializableAttribute nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez implementację interfejsu ISerializable.|
|CA2238|[CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.|
|CA2239|[CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Typ ma pole oznaczone za pomocą atrybutu System.Runtime.Serialization.OptionalFieldAttribute, ale nie zapewnia on metod obsługi zdarzeń deserializacji.|
|CA2240|[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)|Aby naprawić naruszenie tej zasady, należy się upewnić, że metoda GetObjectData jest widoczna oraz możliwa do zastąpienia i że wszystkie pola wystąpienia są uwzględnione w procesie serializacji lub jawnie oznaczone atrybutem NonSerializedAttribute.|
|CA2241|[CA2241: Określ poprawne argumenty dla metod formatowania](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Argument formatu, który jest przekazany do elementu System.String.Format, nie zawiera elementu format, który odpowiada każdemu obiektowi argumentu lub odwrotnie.|
|CA2242|[CA2242: Poprawnie testuj nie-liczby (NaN)](../code-quality/ca2242-test-for-nan-correctly.md)|To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości.|
|CA2243|[CA2243: Analiza literałów typu string atrybutów powinna przebiegać poprawnie](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Parametr o typie literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikatora GUID lub wersji.|
|CA5122|[CA5122 Deklaracje P/Invoke nie powinny być bezpieczne-krytyczne pod względem zabezpieczeń](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md)|Metody są oznaczone jako SecuritySafeCritical, gdy wykonują operacje zależne od zabezpieczeń, ale mogą być również bezpiecznie używane przez kod przezroczystości. Kod przezroczystości może nigdy bezpośrednio nie wywołać kodu natywnego za pośrednictwem metody P/Invoke. Dlatego oznakowanie metody P/Invoke jako bezpiecznej-krytycznej pod względem zabezpieczeń nie umożliwi jej wywołania kodu przezroczystości i jest mylące dla analizy zabezpieczeń.|
