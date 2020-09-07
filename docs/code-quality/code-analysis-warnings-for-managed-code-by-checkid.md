---
title: Omówienie reguł jakości kodu
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
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
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
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
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
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
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e4b728fab6eb47501bb0d1bb752d22c0c29a8b4
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509448"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Ostrzeżenia analizy kodu dla kodu zarządzanego według CheckId

Poniższa tabela zawiera ostrzeżenia analizy kodu dla kodu zarządzanego przez identyfikator CheckId ostrzeżenia.

| CheckId | Ostrzeżenie | Opis |
|---------| - | - |
| CA1000 | [CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000.md) | Po wywołaniu statycznego elementu członkowskiego typu ogólnego dla typu trzeba określić argument typu. Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. W tych dwóch przypadkach składnia określająca argument typu jest różna i łatwo o pomyłkę. |
| CA1001 | [CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji](../code-quality/ca1001.md) | Klasa deklaruje i implementuje pole wystąpienia typu System.IDisposable, ale nie implementuje interfejsu IDisposable. Klasa, która deklaruje pole IDisposable, pośrednio posiada niezarządzany zasób i powinna implementować interfejs IDisposable. |
| CA1002 | [CA1002: Nie uwidaczniaj list ogólnych](../code-quality/ca1002.md) | System. Collections. Generic. list< (of \<(T> ) >) to ogólna kolekcja, która została zaprojektowana pod kątem wydajności, a nie dziedziczenia. Dlatego też lista nie zawiera wirtualnych elementów członkowskich. Zamiast powyższych powinny zostać zastosowane kolekcje ogólne, zaprojektowane do obsługi dziedziczenia. |
| CA1003 | [CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń](../code-quality/ca1003.md) |Typ zawiera delegata zwracającego wartość void, którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs), i zawierający element docelowy zestawu Microsoft .NET Framework 2,0. |
| CA1005 | [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005.md) | Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Zwykle jest oczywiste z jednym parametrem typu, jak na liście \<T> , a w niektórych przypadkach, które mają dwa parametry typu, jak w słowniku \<TKey, TValue> . Jeśli jednak istnieją więcej niż dwa parametry typu, poziom trudności staje się zbyt wysoki dla większości użytkowników. |
| CA1008 | [CA1008: Typy wyliczeniowe powinny mieć wartość zero](../code-quality/ca1008.md) | Wartość domyślna niezainicjowanego typu wyliczeniowego, podobnie jak inne typy wartości, wynosi zero. Wyliczanie przypisane bez flag powinno definiować element członkowski przy użyciu wartości zero, tak że wartość domyślna jest prawidłową wartością wyliczenia. Jeśli wyliczenie, w którym zastosowano atrybut FlagsAttribute, definiuje element członkowski o wartości zero, powinno być nazwane „Brak”, aby wskazać, że żadne wartości nie zostały ustawione w wyliczeniu. |
| CA1010 | [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010.md) | Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może zostać użyta, aby wypełnić typy generyczne kolekcji. |
| CA1012 | [CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów](../code-quality/ca1012.md) | Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany. |
| CA1014 | [CA1014: Oznacz zestawy atrybutem CLSCompliant](../code-quality/ca1014.md) | The Common Language Specification (CLS) definiuje ograniczenia nazw, typów danych i reguł, z którymi muszą być zgodne zestawy, jeśli zostaną użyte w językach programowania. Dobry projekt wymusza, że wszystkie zestawy jawnie wskazują zgodność ze specyfikacją CLS przy użyciu <xref:System.CLSCompliantAttribute> . Jeśli ten atrybut nie jest obecny w zestawie, oznacza to, że zestaw jest niezgodny. |
| CA1016 | [CA1016: Oznacz zestawy atrybutem AssemblyVersion](../code-quality/ca1016.md) | Platforma .NET używa numeru wersji do unikatowego identyfikowania zestawu i powiązania z typami w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane. |
| CA1017 | [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute określa, w jaki sposób klienci COM otrzymują dostęp do kodu zarządzanego. Zasada dobrego projektowania nakazuje, aby zestawy jawnie wskazywały widoczność COM. Widoczność COM można ustawić dla całego zestawu, a następnie zastąpić dla poszczególnych typów i elementów członkowskich typu. Jeśli ten atrybut jest nieobecny, zawartość zestawu jest widoczna dla klientów COM. |
| CA1018 | [CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018.md) | Podczas definiowania atrybutu niestandardowego należy go oznaczyć przy użyciu elementu AttributeUsageAttribute, aby wskazać, w którym miejscu kodu źródłowego ma być on zastosowany. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. |
| CA1019 | [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019.md) | Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis. |
| CA1021 | [CA1021: Unikaj parametrów out](../code-quality/ca1021.md) | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między parametrami out i ref nie jest powszechnie zrozumiała. |
| CA1024 | [CA1024: Używaj właściwości, o ile to możliwe](../code-quality/ca1024.md) | Metody publiczne lub chronione mają nazwę zaczynającą się od „Get”, nie posiadają parametrów i zwracają wartość, która nie jest tablicą. Metoda ta może być dobrym kandydatem na właściwość. |
| CA1027 |[CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027.md) | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj atrybut FlagsAttribute do wyliczenia, gdy jego stałe nazwane mogą zostać sensownie połączone. |
| CA1028 | [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028.md) | Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Domyślnie typ danych System.Int32 jest używany do przechowywania wartości stałej. Mimo że można zmienić ten typ podstawowy, nie jest to wymagane ani zalecane dla większości scenariuszy. |
| CA1030 | [CA1030: Używaj zdarzeń, o ile to możliwe](../code-quality/ca1030.md) |Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Jeśli metoda jest wywoływana w odpowiedzi na jasno określoną zmianę stanu, powinna ona zostać wywołana przez program obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę. |
| CA1031 | [CA1031: Nie przechwytuj typów wyjątków ogólnych](../code-quality/ca1031.md) | Ogólne wyjątki nie powinny być przechwytywane. Przechwytuj wyjątek bardziej precyzyjny lub zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w bloku catch. |
| CA1032 |[CA1032: Zaimplementuj standardowe konstruktory wyjątków](../code-quality/ca1032.md) | Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. |
| CA1033 | [CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne](../code-quality/ca1033.md) | Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie. |
| CA1034 | [CA1034: Typy zagnieżdżone nie powinny być widoczne](../code-quality/ca1034.md) | Typ zagnieżdżony to typ, który jest zadeklarowany wewnątrz zakresu innego typu. Typy zagnieżdżone są przydatne w przypadku hermetyzacji szczegółów implementacji prywatnej typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz. |
| CA1036 | [CA1036: Przesłaniaj metody porównywalnych typów](../code-quality/ca1036.md) |Typ publiczny lub chroniony implementuje interfejs System.IComparable. Nie zastępuje on metody Object.Equals ani nie przeciąża specyficznego dla języka operatora równości, nierówności, mniejsze lub większe niż. |
| CA1040 |[CA1040: Unikaj pustych interfejsów](../code-quality/ca1040.md) | Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich; dlatego też nie definiuje kontraktu, który można zaimplementować. |
| CA1041 | [CA1041: Udostępnij komunikat ObsoleteAttribute](../code-quality/ca1041.md) | Typ lub element członkowski jest oznaczony za pomocą atrybutu System.ObsoleteAttribute, który nie ma określonej właściwości ObsoleteAttribute.Message. Podczas kompilowania typu lub elementu członkowskiego, który jest oznaczony za pomocą ObsoleteAttribute, wyświetlana jest właściwość Wiadomość atrybutu. Dostarcza to informacje użytkownika o przestarzałym typie lub elemencie członkowskim. |
| CA1043 | [CA1043: Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów](../code-quality/ca1043.md) | Indeksatory (właściwości indeksowane) powinny używać dla indeksu typów całkowitych lub ciągu. Typy te są zwykle używane do indeksowania struktur danych i zwiększają one użyteczność biblioteki. Użycie typu Object powinno zostać ograniczone do przypadków, w których nie może zostać określony typ całkowity lub ciąg w czasie projektowania. |
| CA1044 | [CA1044: Właściwości nie powinny być tylko do zapisu](../code-quality/ca1044.md) | Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Dzieje się tak dlatego, że umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwianie przeglądania tej wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność. |
| CA1045 |[CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045.md) | Przekazywanie typów przez odwołanie (używając out lub ref) wymaga doświadczenia w zakresie wskaźników, rozumienia różnicy między typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać od użytkowników, aby Master pracował z `out` lub `ref` parametrami. |
| CA1046 | [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046.md) | Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt. |
| CA1047 |[CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych](../code-quality/ca1047.md) | Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Z definicji po typach zapieczętowanych nie można dziedziczyć, co oznacza, że nie można wywołać metody chronionej na typach zapieczętowanych. |
| CA1050 | [CA1050: Deklaruj typy w przestrzeniach nazw](../code-quality/ca1050.md) | Typy są zadeklarowane w przestrzeniach nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów. |
| CA1051 | [CA1051: Nie deklaruj widocznych pól w wystąpieniach](../code-quality/ca1051.md) | Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być prywatne lub wewnętrzne i dostępne przy użyciu właściwości. |
| CA1052 | [CA1052: Statyczne typy przechowujące powinny być zapieczętowane](../code-quality/ca1052.md) | Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowany za pomocą modyfikatora sealed (C# Reference) (NotInheritable). Typ, po którym nie będzie dziedziczenia, powinien być oznakowany przy użyciu modyfikatora sealed, aby zapobiec użyciu go jako typu podstawowego. |
| CA1053 |[CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053.md) | Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny. Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Przeciążenie typu ciąg powinno wywoływać, dla bezpieczeństwa, przeciążenie jednolitego identyfikatora zasobów (URI) przy użyciu argumentu typu ciąg. |
| CA1054 | [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054.md) | Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, powinno zostać dostarczone odpowiadające przeciążenie, pobierające wystąpienie klasy URI, które dostarcza te usługi w bezpieczny sposób. |
| CA1055 | [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055.md) | Reguła ta zakłada, że metoda zwraca identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1056 | [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056.md) | Reguła ta zakłada, że właściwość reprezentuje identyfikator URI. Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Klasa System.Uri udostępnia te usługi w bezpieczny sposób. |
| CA1058 | [CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych](../code-quality/ca1058.md) | Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Użyj jednej z alternatyw. |
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
| CA1303 | [CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów](../code-quality/ca1303.md) | Metoda widoczna na zewnątrz przekazuje literał ciągu jako parametr do konstruktora lub metody .NET, a ten ciąg powinien być Lokalizowalny. |
| CA1304 | [CA1304: Określ argument CultureInfo](../code-quality/ca1304.md) | Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1305 | [CA1305: Określ argument IFormatProvider](../code-quality/ca1305.md) | Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych. |
| CA1307 | [CA1307: Określ parametr StringComparison w celu zapewnienia jednoznaczności](../code-quality/ca1307.md) | Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison. |
| CA1308 |[CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami](../code-quality/ca1308.md) | Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery. |
| CA1309 | [CA1309: Użyj porządkowego ustawienia właściwości StringComparison](../code-quality/ca1309.md) | Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny. |
| CA1310 | [CA1310: Określ parametr StringComparison w celu zapewnienia poprawności](../code-quality/ca1310.md) | Operacja porównywania ciągów używa przeciążenia metody, które nie ustawia parametru StringComparison i domyślnie używa porównania ciągów specyficznych dla kultury. |
| CA1401 | [CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401.md) | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Takie metody nie powinny być udostępniane. |
| CA1417 | [CA1417: nie należy używać `OutAttribute` w parametrach ciągu dla elementu P/Invoke](../code-quality/ca1417.md) | Parametry ciągu przesyłane przez wartość z `OutAttribute` mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami. |
| CA1501 | [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501.md) | Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia. Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. |
| CA1502 | [CA1502: Unikaj nadmiernej złożoności](../code-quality/ca1502.md) | Ta reguła mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określona przez liczbę i złożoność rozgałęzień warunkowych. |
| CA1505 | [CA1505: Unikaj kodu trudnego w utrzymaniu](../code-quality/ca1505.md) | Typ lub metoda ma niską wartość indeksu konserwacji. Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i są dobrymi kandydatami do przeprojektowania. |
| CA1506 | [CA1506: Unikaj nadmiernego sprzężenia klas](../code-quality/ca1506.md) | Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda. |
| CA1507 | [CA1507: Użyj operatora nameof zamiast ciągu](../code-quality/ca1507.md) | Literał ciągu jest używany jako argument, w którym `nameof` można użyć wyrażenia. |
| CA1508 | [CA1508: Unikaj martwego kodu warunku](../code-quality/ca1508.md) | Metoda ma kod warunkowy, który zawsze jest obliczany `true` lub `false` w czasie wykonywania. Prowadzi to do nieaktywnego kodu w `false` gałęzi warunku. |
| CA1509 | [CA1509: Nieprawidłowy wpis w pliku konfiguracji metryk kodu](../code-quality/ca1509.md) | Reguły metryk kodu, takie jak [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) i [CA1506](ca1506.md), dostarczyły plik konfiguracji o nazwie `CodeMetricsConfig.txt` z nieprawidłowym wpisem. |
| CA1700 | [CA1700: Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”](../code-quality/ca1700.md) | Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. |
| CA1707 | [CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia](../code-quality/ca1707.md) | Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry. |
| CA1708 | [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708.md) | Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. |
| CA1710 | [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710.md) |Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają przyrostek skojarzony z typem bazowym lub interfejsem. |
| CA1711 | [CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów](../code-quality/ca1711.md) | Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów. |
| CA1712 | [CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych](../code-quality/ca1712.md) | Nazwy elementów członkowskich wyliczenia nie mają prefiksu od nazwy typu, ponieważ narzędzia programistyczne dostarczają informacje na temat typu. |
| CA1713 | [CA1713: Zdarzenia nie powinny mieć prefiksu „before” ani „after”](../code-quality/ca1713.md) | Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. |
| CA1714 | [CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714.md) | Publiczne wyliczenie ma atrybut System.FlagsAttribute, a jego nazwa nie kończy się na „s”. Typy oznaczone przy użyciu FlagsAttribute mają nazwy w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. |
| CA1715 | [CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715.md) | Nazwa interfejsu, który jest widoczny na zewnątrz, nie zaczyna się od wielkiej litery „I”. Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery „T”. |
| CA1716 | [CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi](../code-quality/ca1716.md) | Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego. |
| CA1717 | [CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1717.md) | Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia. |
| CA1720 |[CA1720: Identyfikatory nie powinny zawierać nazw typów](../code-quality/ca1720.md) | Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych. |
| CA1721 | [CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get](../code-quality/ca1721.md) |Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje. |
| CA1724 | [CA1724: Nazwy typów nie powinny być takie same jak nazwy przestrzeni nazw](../code-quality/ca1724.md) | Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw platformy .NET. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki. |
| CA1725 | [CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową](../code-quality/ca1725.md) | Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody. |
| CA1801 | [CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801.md) | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| CA1802 |[CA1802: Używaj literałów w odpowiednich miejscach](../code-quality/ca1802.md) |Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) i jest inicjowane przy użyciu wartości obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na pole const (const w), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aby wartość była obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| CA1805 | [CA1805: Nie inicjuj niepotrzebnie](../code-quality/ca1805.md) | Środowisko uruchomieniowe platformy .NET inicjuje wszystkie pola typów odwołań do ich wartości domyślnych przed uruchomieniem konstruktora. W większości przypadków jawne zainicjowanie pola do jego wartości domyślnej jest nadmiarowe, co zwiększa koszty konserwacji i może obniżyć wydajność (na przykład większy rozmiar zestawu). |
| CA1806 | [CA1806: Nie ignoruj wyników metod](../code-quality/ca1806.md) | Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany. |
| CA1810 | [CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810.md) | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
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
| CA1834 |[CA1834: Użyj StringBuilder.Append(char) dla ciągów z pojedynczym znakiem](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> ma `Append` Przeciążenie, które przyjmuje `char` jako argument. Preferuj wywołania `char` przeciążenia ze względu na wydajność. |
| CA1835 |[CA1835: Preferuj przeciążenia oparte na Memory' dla elementu "ReadAsync" i "WriteAsync"](../code-quality/ca1835.md) | Element "Stream" ma Przeciążenie "ReadAsync", które przyjmuje &lt; &gt; jako pierwszy argument "bajt pamięci", i Przeciążenie "WriteAsync", które pobiera "ReadOnlyMemory &lt; Byte &gt; " jako pierwszy argument. Preferuj wywoływanie przeciążeń opartych na pamięci, co jest bardziej wydajne. |
| CA1836 |[CA1836: Preferuj `IsEmpty` , `Count` Jeśli są dostępne](../code-quality/ca1836.md) | Preferuj `IsEmpty` Właściwość, która jest bardziej wydajna niż `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> lub, <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> Aby określić, czy obiekt zawiera elementy, czy nie. |
| CA1837 | [CA1837: Użyj `Environment.ProcessId` zamiast `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` jest prostsze i szybsze niż `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838: Unikaj `StringBuilder` parametrów dla P/Invoke](../code-quality/ca1838.md) | Kierowanie elementu "StringBuilder" zawsze tworzy natywną kopię bufora, co powoduje utworzenie wielu alokacji dla jednej operacji organizowania. |
| CA2000 | [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000.md) | Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem. |
| CA2002 |[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002.md) |Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. |
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
| CA2109 | [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109.md) | Wykryto publiczną lub chronioną metodę obsługi zdarzeń. Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne. |
| CA2119 | [CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych](../code-quality/ca2119.md) | Dziedziczony typ publiczny zapewnia implementację metody wewnętrznej (zaprzyjaźnionej w programie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Aby naprawić naruszenie tej zasady, należy zapobiegać zastąpieniu metody poza zestawem. |
| CA2153 |[CA2153: zapobiegaj obsłudze wyjątków uszkodzonego stanu](../code-quality/ca2153.md) | Wyjątki uszkodzonych Stanów (rozszerzeń klienta) wskazują, że uszkodzenie pamięci istnieje w procesie. Ich przechwycenie zamiast zezwalania na awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać lukę w uszkodzonym regionie pamięci. |
| CA2200 | [CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200.md) | Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona. |
| CA2201 | [CA2201: Nie zgłaszaj wyjątków o zastrzeżonych typach](../code-quality/ca2201.md) | Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2207 | [CA2207: Pola statyczne typu wartości inicjuj bezpośrednio](../code-quality/ca2207.md) | Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny. |
| CA2208 |[CA2208: Poprawnie twórz wystąpienia wyjątków argumentów](../code-quality/ca2208.md) | Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException. |
| CA2211 |[CA2211: Pola niebędące stałymi nie powinny być widoczne](../code-quality/ca2211.md) | Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania, aby synchronizować dostęp do obiektu klasy. |
| CA2213 | [CA2213: Pola możliwe do likwidacji należy likwidować](../code-quality/ca2213.md) | Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego. |
| CA2214 | [CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać](../code-quality/ca2214.md) | Gdy konstruktor wywołuje metodę wirtualną, konstruktor wystąpienia, który wywołuje metodę, mógł nie zostać wykonany. |
| CA2215 | [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215.md) | Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose. |
| CA2216 |[CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216.md) | Typ, który implementuje element System.IDisposable i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, tak jak opisano w Object.Finalize. |
| CA2217 | [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217.md) |Widoczne na zewnątrz wyliczenie jest oznaczone przy użyciu FlagsAttribute i ma jedną lub więcej wartości, które nie są potęgami dwójki lub kombinacji innych zdefiniowanych wartości z wyliczenia. |
| CA2219 | [CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków](../code-quality/ca2219.md) | Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Dzięki temu oryginalny błąd jest trudny do wykrycia i debugowania. |
| CA2225 | [CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne](../code-quality/ca2225.md) |Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski udostępnia taką samą funkcjonalność jak operator i jest dostarczany deweloperom programującym w językach, które nie obsługują przeciążonych operatorów. |
| CA2226 | [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226.md) | Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego. |
| CA2227 |[CA2227: Właściwości kolekcji powinny być tylko do odczytu](../code-quality/ca2227.md) |Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. |
| CA2229 | [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229.md) | Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. |
| CA2231 | [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231.md) | Typ wartości zastępuje metodę Object.Equals, ale nie implementuje operatora równości. |
| CA2234 | [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234.md) | Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”. Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri. |
| CA2235 | [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235.md) | Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. |
| CA2237 | [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237.md) | Aby typy były rozpoznawalne przez CLR jako możliwe do serializacji, muszą być oznaczone za pomocą atrybutu SerializableAttribute nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez implementację interfejsu ISerializable. |
| CA2241 | [CA2241: Podaj poprawne argumenty metod formatowania](../code-quality/ca2241.md) | Argument formatu, który jest przekazany do elementu System.String.Format, nie zawiera elementu format, który odpowiada każdemu obiektowi argumentu lub odwrotnie. |
| CA2242 |[CA2242: Poprawnie testuj nie-liczby (NaN)](../code-quality/ca2242.md) | To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości. |
| CA2243 |[CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie](../code-quality/ca2243.md) | Parametr o typie literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikatora GUID lub wersji. |
| CA2244 | [CA2244: Nie duplikuj inicjowania indeksowanych elementów](../code-quality/ca2244.md) | Inicjator obiektu ma więcej niż jeden indeks elementu indeksowanego z tym samym indeksem stałym. Wszystkie oprócz ostatniego inicjatora są nadmiarowe. |
| CA2245 | [CA2245: Nie przypisuj właściwości do jej samej](../code-quality/ca2245.md) | Właściwość została przypadkowo przypisana do samej siebie. |
| CA2246 | [CA2246: Nie przypisuj symbolu i jego składowej w tej samej instrukcji](../code-quality/ca2246.md) | Przypisanie symbolu i jego elementu członkowskiego, czyli pola lub właściwości, w tej samej instrukcji nie jest zalecane. Nie jest jasne, jeśli dostęp do elementu członkowskiego był przeznaczony do użycia starej wartości symbolu przed przypisaniem lub nową wartością z przypisania w tej instrukcji. |
| CA2247 | [CA2247: argument przesłany do konstruktora TaskCompletionSource powinien być opcji TaskCreationOptions wyliczeniem zamiast TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource ma konstruktory, które przyjmują opcji TaskCreationOptions, które kontrolują podstawowe zadanie, i konstruktorów, które przyjmują stan obiektu, który jest przechowywany w zadaniu.  Przypadkowe przekazanie TaskContinuationOptions zamiast opcji TaskCreationOptions spowoduje wywołanie opcji jako stanu. |
| CA2248 | [CA2248: Podaj poprawny argument wyliczenia dla metody Enum.HasFlag](../code-quality/ca2248.md) | Typ wyliczeniowy przesłany jako argument `HasFlag` wywołania metody różni się od typu wyliczeniowego wywołującego. |
| CA2249 | [CA2249: Rozważ użycie metody String.Contains zamiast String.IndexOf](../code-quality/ca2249.md) | Wywołania, do `string.IndexOf` których wynik służy do sprawdzania obecności/braku podciągu, mogą zostać zastąpione przez `string.Contains` . |
| CA2300 | [CA2300: Nie używaj niezabezpieczonego deserializatora BinaryFormatter](../code-quality/ca2300.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2301 | [CA2301: Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder](../code-quality/ca2301.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2302 | [CA2302: Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize](../code-quality/ca2302.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2305 | [CA2305: Nie używaj niezabezpieczonego deserializatora LosFormatter](../code-quality/ca2305.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2310 | [CA2310: Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer](../code-quality/ca2310.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2311 | [CA2311: Nie wykonuj deserializacji bez uprzedniego ustawienia właściwości NetDataContractSerializer.Binder](../code-quality/ca2311.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2312 | [CA2312: Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją](../code-quality/ca2312.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2315 | [CA2315: Nie używaj niezabezpieczonego deserializatora ObjectStateFormatter](../code-quality/ca2315.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2321 | [CA2321: Nie wykonuj deserializacji za pomocą obiektu JavaScriptSerializer zainicjowanego przy użyciu parametru SimpleTypeResolver](../code-quality/ca2321.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2322 | [CA2322: Upewnij się, że obiekt JavaScriptSerializer nie został zainicjowany przy użyciu parametru SimpleTypeResolver przed deserializacją](../code-quality/ca2322.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2326 | [CA2326: Nie używaj wartości TypeNameHandling innych niż None](../code-quality/ca2326.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2327 | [CA2327: Nie używaj niezabezpieczonych ustawień JsonSerializerSettings](../code-quality/ca2327.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2328 | [CA2328: Upewnij się, że ustawienia JsonSerializerSettings zostały zabezpieczone](../code-quality/ca2328.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2329 | [CA2329: Nie deserializuj przy użyciu rozwiązania JsonSerializer za pomocą niezabezpieczonej konfiguracji](../code-quality/ca2329.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2330 | [CA2330: Upewnij się, że podczas deserializacji rozwiązania JsonSerializer ma bezpieczną konfigurację](../code-quality/ca2330.md) | Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. |
| CA2350 | [CA2350: Upewnij się, że dane wejściowe elementu DataTable.ReadXml () są zaufane](ca2350.md) | Podczas deserializacji <xref:System.Data.DataTable> z niezaufanymi danymi wejściowymi, osoba atakująca może przedrzemieślniczić złośliwe dane wejściowe w celu przeprowadzenia ataku typu "odmowa usługi". Mogą wystąpić nieznane luki w zabezpieczeniach dotyczące zdalnego wykonywania kodu. |
| CA2351 | [CA2351: Upewnij się, że dane wejściowe elementu DataSet.ReadXml () są zaufane](ca2351.md) | Podczas deserializacji <xref:System.Data.DataSet> z niezaufanymi danymi wejściowymi, osoba atakująca może przedrzemieślniczić złośliwe dane wejściowe w celu przeprowadzenia ataku typu "odmowa usługi". Mogą wystąpić nieznane luki w zabezpieczeniach dotyczące zdalnego wykonywania kodu. |
| CA2352 | [CA2352: Niebezpieczny element DataSet lub DataTable w typie możliwym do serializacji może być podatny na ataki polegające na zdalnym wykonaniu kodu](ca2352.md) | Klasa lub struktura oznaczona przy użyciu <xref:System.SerializableAttribute> zawiera <xref:System.Data.DataSet> pole lub <xref:System.Data.DataTable> Właściwość i nie ma <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Niebezpieczny element DataSet lub DataTable w typie możliwym do serializacji](ca2353.md) | Klasa lub struktura oznaczona przy użyciu atrybutu serializacji XML lub atrybutu kontraktu danych zawiera <xref:System.Data.DataSet> <xref:System.Data.DataTable> pole or lub właściwość. |
| CA2354 | [CA2354: Niebezpieczny element DataSet lub DataTable w deserializowanym wykresie obiektu może być podatny na atak polegający na zdalnym wykonaniu kodu](ca2354.md) | Deserializacja z <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> serializowaną, a wykres obiektu typu rzutowego może zawierać <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Niebezpieczny element DataSet lub DataTable w deserializowanym wykresie obiektu](ca2355.md) | Deserializacja, gdy wykres obiektu rzutowanego lub określonego typu może zawierać <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: niebezpieczny zestaw danych lub DataTable w grafie obiektów deserializowanych sieci Web](ca2356.md) | Metoda z <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> lub <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> ma parametr, który może odwoływać się do <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: Upewnij się, że automatycznie wygenerowana klasa zawierająca element DataSet.ReadXml() nie jest używana z niezaufanymi danymi](ca2361.md) | Podczas deserializacji <xref:System.Data.DataSet> z niezaufanymi danymi wejściowymi, osoba atakująca może przedrzemieślniczić złośliwe dane wejściowe w celu przeprowadzenia ataku typu "odmowa usługi". Mogą wystąpić nieznane luki w zabezpieczeniach dotyczące zdalnego wykonywania kodu. |
| CA2362 | [CA2362: Niebezpieczny element DataSet lub DataTable w automatycznie wygenerowanym typie, który można serializować, może być narażony na ataki polegające na zdalnym wykonaniu kodu](ca2362.md) | Podczas deserializacji niezaufanych danych wejściowych przy użyciu programu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i deserializowany obiekt Graph zawiera <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> , osoba atakująca może nawiązać złośliwy ładunek w celu wykonania ataku zdalnego wykonywania kodu. |
| CA3001 | [CA3001: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL](../code-quality/ca3001.md) | Podczas pracy z niezaufanymi poleceniami wejściowymi i SQL należy zastanowić się nad atakami polegającymi na iniekcji SQL. Atak wykorzystujący wstrzyknięcie kodu SQL może wykonywać złośliwe polecenia SQL, narażając zabezpieczenia i integralność aplikacji. |
| CA3002 | [CA3002: Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami](../code-quality/ca3002.md) | Podczas pracy z niezaufanymi danymi wejściowymi z żądań sieci Web należy zastanowić się, jak ataki między środowiskami (XSS). Atak typu "XSS" powoduje dodanie niezaufanych danych wejściowych do nieprzetworzonych danych wyjściowych HTML, co umożliwia osobie atakującej wykonywanie złośliwych skryptów lub złośliwie modyfikowanie zawartości na stronie sieci Web. |
| CA3003 | [CA3003: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku](../code-quality/ca3003.md) | Podczas pracy z niezaufanymi danymi wejściowymi z żądań sieci Web należy zastanowić się nad użyciem danych wejściowych sterowanych przez użytkownika podczas określania ścieżek do plików. |
| CA3004 | [CA3004: Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji](../code-quality/ca3004.md) | Odłączanie informacji o wyjątkach daje osobom atakującym wgląd w wewnętrzne dane aplikacji, co może pomóc atakującym znaleźć inne luki w zabezpieczeniach. |
| CA3006 | [CA3006: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu](../code-quality/ca3006.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy zastanowić się nad atakami polegającymi na iniekcji poleceń. Atak polegający na iniekcji poleceń może wykonywać złośliwe polecenia w podstawowym systemie operacyjnym, narażając zabezpieczenia i integralność serwera. |
| CA3007 | [CA3007: Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania](../code-quality/ca3007.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze luki w zabezpieczeniach dotyczące otwartych przekierowań. Osoba atakująca może wykorzystać lukę w zabezpieczeniach Open Redirect, aby użyć witryny sieci Web w celu uzyskania oryginalnego adresu URL, ale przekierować niepodejrzanego gościa do phishingu lub innej złośliwej strony sieci Web. |
| CA3008 | [CA3008: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath](../code-quality/ca3008.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy zastanowić się nad atakami z użyciem kodu XPath. Konstruowanie zapytań XPath przy użyciu niezaufanych danych wejściowych może pozwolić osobie atakującej na złośliwe manipulowanie kwerendą w celu zwrócenia niezamierzonego wyniku i może ujawnić zawartość pliku XML z kwerendą. |
| CA3009 | [CA3009: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML](../code-quality/ca3009.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki kodu XML. |
| CA3010 | [CA3010: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML](../code-quality/ca3010.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki kodu XAML. XAML jest językiem znaczników, który bezpośrednio reprezentuje Tworzenie wystąpienia obiektu i wykonywanie. Oznacza to, że elementy utworzone w języku XAML mogą korzystać z zasobów systemowych (np. dostępu do sieci i we/wy systemu plików). |
| CA3011 | [CA3011: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL](../code-quality/ca3011.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy zastanowić się nad ładowaniem niezaufanego kodu. Jeśli aplikacja sieci Web ładuje niezaufany kod, osoba atakująca może dodawać złośliwe biblioteki DLL do procesu i wykonywać złośliwe kod. |
| CA3012 | [CA3012: Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego](../code-quality/ca3012.md) | Podczas pracy z niezaufanymi danymi wejściowymi należy mieć na uwadze ataki z iniekcją wyrażeń regularnych. Osoba atakująca może użyć iniekcji wyrażenia regularnego w celu złośliwego zmodyfikowania wyrażeń regularnych, aby wyrażenie regularne pasowało do nieoczekiwanych wyników, lub aby wyrażenie regularne zużywać nadmierny procesor w wyniku ataku typu "odmowa usługi". |
| CA3061 | [CA3061: Nie dodawaj schematu według adresu URL](../code-quality/ca3061.md) | Nie używaj niebezpiecznego przeciążenia metody Add, ponieważ może to spowodować niebezpieczne odwołania zewnętrzne. |
| CA3075 | [CA3075: Niezabezpieczone przetwarzanie definicji DTD](../code-quality/ca3075.md) | Jeśli używasz niezabezpieczonych wystąpień DTDProcessing lub referencyjnych źródeł zewnętrznych, Analizator może zaakceptować niezaufane dane wejściowe i ujawnić poufne informacje osobom atakującym. |
| CA3076 | [CA3076: Niezabezpieczone wykonywanie skryptu XSLT](../code-quality/ca3076.md) | W przypadku wykonywania Extensible Stylesheet Language transformacji (XSLT) w aplikacjach .NET w niezabezpieczony sposób procesor może rozpoznać niezaufane odwołania do identyfikatorów URI, które mogą ujawnić poufne informacje osobom atakującym, prowadząc do odmowy usługi i ataków między lokacjami. |
| CA3077 | [CA3077: Niezabezpieczone przetwarzanie w elemencie Design interfejsu API, dokumencie XML i czytniku tekstu dla kodu XML](../code-quality/ca3077.md) | Podczas projektowania interfejsu API pochodnego od XmlDocument i XMLTextReader należy mieć na uwadze, że DtdProcessing. Używanie niezabezpieczonych wystąpień DTDProcessing w przypadku odwoływania się do lub rozpoznawania zewnętrznych źródeł jednostek lub ustawiania niezabezpieczonych wartości w kodzie XML może prowadzić do ujawnienia informacji. |
| CA3147 | [CA3147: Oznaczanie procedur obsługi zleceń za pomocą tokenu ValidateAntiForgeryToken](../code-quality/ca3147.md) | Podczas projektowania kontrolera MVC ASP.NET należy zastanowić się, że zachodzą przypadki fałszerstwa żądań między witrynami. Atakujący sfałszowanie żądań między lokacjami może wysyłać złośliwych żądań od uwierzytelnionego użytkownika do kontrolera MVC ASP.NET. |
| CA5350 | [CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350.md) | Słabe algorytmy szyfrowania i funkcje wyznaczania wartości skrótu są obecnie używane z wielu powodów, ale nie powinny być używane do zagwarantowania poufności lub integralności chronionych danych. Ta reguła jest wyzwalana po znalezieniu w kodzie algorytmów TripleDES, SHA1 lub RIPEMD160.|
| CA5351 | [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351.md) | Uszkodzone algorytmy kryptograficzne nie są uważane za bezpieczne, a ich użycie nie powinno być zdecydowanie zalecane. Ta reguła jest wyzwalana, gdy odnajdzie algorytm wyznaczania wartości skrótu MD5 lub algorytmy szyfrowania DES lub RC2 w kodzie. |
| CA5358 | [CA5358: Nie używaj niebezpiecznych trybów szyfrowania](../code-quality/ca5358.md) | Nie używaj niebezpiecznych trybów szyfrowania |
| CA5359 | [CA5359 nie wyłączaj weryfikacji certyfikatu](../code-quality/ca5359.md) | Certyfikat może pomóc uwierzytelnić tożsamość serwera programu. Klienci powinni sprawdzić poprawność certyfikatu serwera, aby upewnić się, że żądania są wysyłane do zamierzonego serwera. Jeśli ServerCertificateValidationCallback zawsze zwróci `true` , każdy certyfikat przejdzie pomyślnie weryfikację. |
| CA5360 | [CA5360 nie wywoływać niebezpiecznych metod w deserializacji](../code-quality/ca5360.md) | Niezabezpieczona deserializacja jest luką w zabezpieczeniach, która występuje, gdy niezaufane dane są używane do nadużycia logiki aplikacji, wynoszą atak typu "odmowa usługi" (DoS), a nawet wykonują dowolny kod podczas deserializacji. Często Złośliwi użytkownicy mogą nadużyć tych funkcji deserializacji, gdy aplikacja deserializacji dane niezaufane, które są pod kontrolą. W celu wywołaj metody niebezpieczne w procesie deserializacji. Pomyślne niezabezpieczone ataki deserializacji mogą pozwolić atakującemu na przeprowadzanie ataków, takich jak ataki systemu DoS, obejścia uwierzytelniania i zdalne wykonywanie kodu. |
| CA5361 | [CA5361: Nie wyłączaj użycia silnej kryptografii w pakiecie SChannel](../code-quality/ca5361.md) | Ustawienie `Switch.System.Net.DontEnableSchUseStrongCrypto` `true` obniżania poziomu kryptografii używanej w połączeniach wychodzących Transport Layer Security (TLS). Słabsze Kryptografia może naruszać poufność komunikacji między aplikacją a serwerem, ułatwiając atakującym eavesdrop poufnych danych. |
| CA5362 | [CA5362 potencjalny cykl odwołań w grafie obiektu deserializowanego](../code-quality/ca5362.md) | W przypadku deserializacji niezaufanych danych, każdy kod przetwarzania deserializowanego grafu obiektów musi obsługiwać cykle odwołań bez przechodzenia do nieskończonych pętli. Obejmuje to zarówno kod, który jest częścią wywołania zwrotnego deserializacji i kod, który przetwarza Graf obiektu po zakończeniu deserializacji. W przeciwnym razie atakujący może przeprowadzić atak typu "odmowa usługi" ze złośliwymi danymi zawierającymi cykl referencyjny. |
| CA5363 | [CA5363: Nie wyłączaj weryfikacji żądań](../code-quality/ca5363.md) | Sprawdzanie poprawności żądań jest funkcją w ASP.NET, która sprawdza żądania HTTP i określa, czy zawierają potencjalnie niebezpieczną zawartość, która może prowadzić do ataków iniekcji, w tym skryptów między lokacjami. |
| CA5364 | [CA5364: Nie używaj przestarzałych protokołów zabezpieczeń](../code-quality/ca5364.md) | Transport Layer Security (TLS) zabezpiecza komunikację między komputerami, najczęściej przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS). Starsze wersje protokołu TLS są mniej bezpieczne niż TLS 1,2 i TLS 1,3 i coraz bardziej mogą mieć nowe luki w zabezpieczeniach. Unikaj stosowania starszych wersji protokołów, aby zminimalizować ryzyko. |
| CA5365 | [CA5365 nie wyłączaj sprawdzania nagłówka HTTP](../code-quality/ca5365.md) | Sprawdzanie nagłówka HTTP włącza kodowanie znaku powrotu karetki i znaków nowego wiersza, \r i \n, które znajdują się w nagłówkach odpowiedzi. To kodowanie może ułatwić uniknięcie ataków wykorzystujących niezaufane dane zawarte w nagłówku przez program. |
| CA5366 | [CA5366 Użyj elementu XmlReader do odczytu pliku XML](../code-quality/ca5366.md) | Korzystanie z programu <xref:System.Data.DataSet> do odczytywania danych XML z niezaufanymi danymi może ładować niebezpieczne odwołania zewnętrzne, które powinny być ograniczone przy użyciu programu <xref:System.Xml.XmlReader> z bezpiecznym mechanizmem rozwiązywania konfliktów lub z wyłączonym przetwarzaniem DTD. |
| CA5367 | [CA5367 nie serializować typów z polami wskaźników](../code-quality/ca5367.md) | Ta reguła sprawdza, czy istnieje Klasa możliwa do serializacji z polem wskaźnika lub właściwością. Elementy członkowskie, które nie mogą być serializowane, mogą być wskaźnikami, takimi jak statyczne elementy członkowskie lub pola oznaczone przy użyciu <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Ustaw ViewStateUserKey dla klas pochodnych ze strony](../code-quality/ca5368.md) | Ustawienie <xref:System.Web.UI.Page.ViewStateUserKey> właściwości może pomóc w zapobieganiu atakom w aplikacji przez umożliwienie przypisania identyfikatora do zmiennej stanu widoku dla poszczególnych użytkowników, tak aby atakujący nie mogli użyć zmiennej do wygenerowania ataku. W przeciwnym razie zostaną wystąpiły luki w zabezpieczeniach związane z fałszerstwem żądań między lokacjami. |
| CA5369 | [CA5369: Używaj elementu XmlReader do deserializacji](../code-quality/ca5369.md) | Przetwarzanie niezaufanych schematów DTD i XML może umożliwić ładowanie niebezpiecznych odwołań zewnętrznych, które powinny być ograniczone przy użyciu elementu XmlReader z bezpiecznym mechanizmem rozwiązywania konfliktów lub z wyłączonym przetwarzaniem schematu DTD i XML. |
| CA5370 | [CA5370: Używaj elementu XmlReader do weryfikacji czytelnika](../code-quality/ca5370.md) | Przetwarzanie niezaufanych schematów DTD i XML może umożliwić ładowanie niebezpiecznych odwołań zewnętrznych. To niebezpieczne ładowanie może być ograniczone przy użyciu elementu XmlReader z bezpiecznym mechanizmem rozwiązywania konfliktów lub z wyłączonym przetwarzaniem schematu DTD i XML. |
| CA5371 | [CA5371: Używaj elementu XmlReader do odczytywania schematu](../code-quality/ca5371.md) | Przetwarzanie niezaufanych schematów DTD i XML może umożliwić ładowanie niebezpiecznych odwołań zewnętrznych. Używanie elementu XmlReader z bezpiecznym programem rozpoznawania nazw lub z wyłączonym przetwarzaniem schematu DTD i XML jest ograniczone. |
| CA5372 | [CA5372: Używaj elementu XmlReader dla elementu XPathDocument](../code-quality/ca5372.md) | Przetwarzanie kodu XML z niezaufanych danych może ładować niebezpieczne odwołania zewnętrzne, które mogą być ograniczone przy użyciu elementu XmlReader z bezpiecznym mechanizmem rozwiązywania konfliktów lub z wyłączonym przetwarzaniem DTD. |
| CA5373 | [CA5373: Nie używaj przestarzałej funkcji wyprowadzania klucza](../code-quality/ca5373.md) | Ta zasada wykrywa wywoływanie metod wyprowadzania słabych kluczy <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> i `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> użyto słabego algorytmu PBKDF1. |
| CA5374 | [CA5374 nie należy używać XslTransform](../code-quality/ca5374.md) | Ta reguła sprawdza, czy <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> jest tworzone wystąpienie w kodzie. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> jest już przestarzałe i nie należy go używać. |
| CA5375 | [CA5375 nie używaj sygnatury dostępu współdzielonego konta](../code-quality/ca5375.md) | Sygnatura dostępu współdzielonego konta może delegować dostęp do operacji odczytu, zapisu i usuwania dla kontenerów obiektów blob, tabel, kolejek i udziałów plików, które nie są dozwolone przy użyciu sygnatury dostępu współdzielonego usługi. Nie obsługuje jednak zasad na poziomie kontenera i zapewnia mniejszą elastyczność i kontrolę nad udzielonymi uprawnieniami. Po otrzymaniu złośliwych użytkowników Twoje konto magazynu zostanie łatwo naruszone. |
| CA5376 | [CA5376 Użyj SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | Sygnatury dostępu współdzielonego to dane poufne, których nie można transportować w postaci zwykłego tekstu na HTTP |
| CA5377 | [CA5377 użycie zasad dostępu na poziomie kontenera](../code-quality/ca5377.md) | Zasady dostępu na poziomie kontenera można zmodyfikować lub odwołać w dowolnym momencie. Zapewnia większą elastyczność i kontrolę nad udzielonymi uprawnieniami. |
| CA5378 | [CA5378: Nie wyłączaj protokołów ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Ustawienie `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` `true` ograniczające połączenia Transport Layer Security (TLS) środowiska Windows Communication Framework z użyciem protokołu TLS 1,0. Ta wersja protokołu TLS zostanie wycofana. |
| CA5379 | [CA5379 nie używaj algorytmu funkcji wyprowadzania klucza słabego](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Klasa domyślnie używa <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algorytmu. Należy określić algorytm wyznaczania wartości skrótu, który ma być używany w niektórych przeciążeniach konstruktora z <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> lub wyższym. Uwaga, <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> Właściwość ma tylko `get` metodę dostępu i nie ma `overriden` modyfikatora. |
| CA5380 | [CA5380: Nie dodawaj certyfikatów do magazynu głównego](../code-quality/ca5380.md) | Ta reguła wykrywa kod, który dodaje certyfikat do magazynu certyfikatów zaufanych głównych urzędów certyfikacji. Domyślnie magazyn certyfikatów zaufanych głównych urzędów certyfikacji jest skonfigurowany przy użyciu zestawu publicznych urzędów certyfikacji, które spełniają wymagania programu certyfikatów głównych firmy Microsoft. |
| CA5381 | [CA5381: Upewnij się, że certyfikaty nie są dodawane do magazynu głównego](../code-quality/ca5381.md) | Ta reguła wykrywa kod, który potencjalnie dodaje certyfikat do magazynu certyfikatów zaufanych głównych urzędów certyfikacji. Domyślnie magazyn certyfikatów zaufanych głównych urzędów certyfikacji jest skonfigurowany przy użyciu zestawu publicznych urzędów certyfikacji (CA), które spełniają wymagania programu certyfikatów głównych firmy Microsoft. |
| CA5382 | [CA5382 używanie bezpiecznych plików cookie w ASP.NET Core](../code-quality/ca5382.md) | Aplikacje dostępne za pośrednictwem protokołu HTTPS muszą używać bezpiecznych plików cookie, które wskazują przeglądarkę, że plik cookie powinien być przesyłany tylko przy użyciu SSL (SSL). |
| CA5383 | [CA5383 Zadbaj o używanie bezpiecznych plików cookie w ASP.NET Core](../code-quality/ca5383.md) | Aplikacje dostępne za pośrednictwem protokołu HTTPS muszą używać bezpiecznych plików cookie, które wskazują przeglądarkę, że plik cookie powinien być przesyłany tylko przy użyciu SSL (SSL). |
| CA5384 | [CA5384 nie używają algorytmu podpisu cyfrowego (DSA)](../code-quality/ca5384.md) | DSA jest słabym algorytmem szyfrowania. |
| CA5385 | [CA5385 używać algorytmu Rivest – Shamir – Adleman (RSA) o odpowiednim rozmiarze klucza](../code-quality/ca5385.md) | Klucz RSA mniejszy niż 2048 bitów jest bardziej narażony na ataki typu "odmowa". |
| CA5386 | [CA5386: Unikaj kodowania na stałe wartości SecurityProtocolType](../code-quality/ca5386.md) | Transport Layer Security (TLS) zabezpiecza komunikację między komputerami, najczęściej przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS). Protokół TLS 1,0 i TLS 1,1 są przestarzałe, podczas gdy protokoły TLS 1,2 i TLS 1,3 są aktualne. W przyszłości protokoły TLS 1,2 i TLS 1,3 mogą być przestarzałe. Aby upewnić się, że aplikacja pozostaje zabezpieczona, należy unikać zakodowana wersji protokołu i docelowej co najmniej .NET Framework v 4.7.1. |
| CA5387 | [CA5387 nie używaj słabej funkcji wyprowadzania klucza z niewystarczającą liczbą iteracji](../code-quality/ca5387.md) | Ta reguła sprawdza, czy klucz kryptograficzny został wygenerowany przy <xref:System.Security.Cryptography.Rfc2898DeriveBytes> użyciu liczby iteracji mniejszej niż 100 000. Wyższa liczba iteracji może pomóc wyeliminować ataki słownikowe próbujące złamać wygenerowany klucz kryptograficzny. |
| CA5388 | [CA5388 zapewnia wystarczającą liczbę iteracji podczas korzystania z funkcji wyprowadzania klucza słabego](../code-quality/ca5388.md) | Ta reguła sprawdza, czy klucz kryptograficzny został wygenerowany za <xref:System.Security.Cryptography.Rfc2898DeriveBytes> pomocą liczby iteracji, która może być mniejsza niż 100 000. Wyższa liczba iteracji może pomóc wyeliminować ataki słownikowe próbujące złamać wygenerowany klucz kryptograficzny. |
| CA5389 | [CA5389: Nie dodawaj ścieżki elementu archiwum do docelowej ścieżki systemu plików](../code-quality/ca5389.md) | Ścieżka pliku może być względna i może prowadzić do dostępu do systemu plików poza oczekiwaną ścieżką docelową systemu plików, co prowadzi do złośliwych zmian konfiguracji i zdalnego wykonywania kodu za pośrednictwem techniki "Ustal i czekaj". |
| CA5390 | [CA5390 klucz szyfrowania nie jest kodem twardym](../code-quality/ca5390.md) | Aby algorytm symetryczny był prawidłowy, klucz tajny musi być znany tylko nadawcy i odbiornik. Gdy klucz jest zakodowany, można go łatwo odnaleźć. Nawet przy użyciu skompilowanych plików binarnych, złośliwi użytkownicy mogą łatwo go wyodrębnić. Po naruszeniu zabezpieczeń klucza prywatnego tekst szyfru można odszyfrować bezpośrednio i nie jest już chroniony. |
| CA5391 | [CA5391 używaj tokenów antysfałszowanych w kontrolerach ASP.NET Core MVC](../code-quality/ca5391.md) | Obsługa `POST` , `PUT` , `PATCH` , lub `DELETE` żądanie bez weryfikowania tokenu antysfałszowanego może być narażona na ataki fałszerstwa żądań między lokacjami. Atakujący sfałszowanie żądań między lokacjami może wysyłać złośliwych żądań od uwierzytelnionego użytkownika do kontrolera ASP.NET Core MVC. |
| CA5392 | [CA5392 użycie atrybutu DefaultDllImportSearchPaths dla elementu P/Invoke](../code-quality/ca5392.md) | Domyślnie funkcja P/Invoke korzysta z <xref:System.Runtime.InteropServices.DllImportAttribute> sondowania wielu katalogów, w tym bieżącego katalogu roboczego biblioteki do załadowania. Może to być problem z zabezpieczeniami dla niektórych aplikacji, co prowadzi do przejęcia biblioteki DLL. |
| CA5393 | [CA5393 nie używają niebezpiecznej wartości DllImportSearchPath](../code-quality/ca5393.md) | Może istnieć złośliwa Biblioteka DLL w domyślnych katalogach wyszukiwania bibliotek DLL i katalogach zestawów. Lub, w zależności od tego, gdzie jest uruchomiona aplikacja, może istnieć złośliwa Biblioteka DLL w katalogu aplikacji. |
| CA5394 | [CA5394 nie używaj niezabezpieczonego losowości](../code-quality/ca5394.md) | Użycie kryptografii z kryptograficznie słabym generatorem liczb losowych może pozwolić osobie atakującej na przewidywalność wygenerowania wartości z uwzględnieniem zabezpieczeń. |
| CA5395 | [CA5395 chybień HttpVerb atrybutu dla metod akcji](../code-quality/ca5395.md) | Wszystkie metody akcji, które tworzą, edytują, usuwają lub w inny sposób modyfikują dane, muszą być chronione przy użyciu atrybutu antysfałszowanego z ataków fałszerstwa żądań między lokacjami. Wykonanie operacji GET powinno być bezpieczną operacją, która nie ma efektów ubocznych i nie modyfikuje utrwalonych danych. |
| CA5396 | [CA5396 Ustaw HttpOnly na wartość true dla HttpCookie](../code-quality/ca5396.md) | W celu zapewnienia kompleksowej oceny należy zapewnić, że poufne pliki cookie HTTP są oznaczane jako HttpOnly. Oznacza to, że przeglądarki sieci Web powinny uniemożliwić uzyskiwanie dostępu do plików cookie przez skrypty. Wprowadzane złośliwe skrypty są typowym sposobem kradzieży plików cookie. |
| CA5397 | [CA5397: Nie używaj przestarzałych wartości SslProtocols](../code-quality/ca5397.md) | Transport Layer Security (TLS) zabezpiecza komunikację między komputerami, najczęściej przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS). Starsze wersje protokołu TLS są mniej bezpieczne niż TLS 1,2 i TLS 1,3 i coraz bardziej mogą mieć nowe luki w zabezpieczeniach. Unikaj stosowania starszych wersji protokołów, aby zminimalizować ryzyko. |
| CA5398 | [CA5398: Unikaj zapisanych na stałe wartości SslProtocols](../code-quality/ca5398.md) | Transport Layer Security (TLS) zabezpiecza komunikację między komputerami, najczęściej przy użyciu protokołu Hypertext Transfer Protocol Secure (HTTPS). Protokół TLS 1,0 i TLS 1,1 są przestarzałe, podczas gdy protokoły TLS 1,2 i TLS 1,3 są aktualne. W przyszłości protokoły TLS 1,2 i TLS 1,3 mogą być przestarzałe. Aby upewnić się, że aplikacja pozostaje zabezpieczona, należy unikać zakodowana wersji protokołu. |
| CA5399 | [CA5399 ostatecznie Wyłącz sprawdzanie listy odwołania certyfikatów HttpClient](../code-quality/ca5399.md) | Odwołany certyfikat nie jest już zaufany. Mogą one być używane przez osoby atakujące, które przechodzą z pewnych złośliwych danych lub kradzieży poufnych danych w komunikacji przy użyciu protokołu HTTPS. |
| CA5400 | [CA5400 upewnij się, że sprawdzanie listy odwołania certyfikatów HttpClient nie jest wyłączone](../code-quality/ca5400.md) | Odwołany certyfikat nie jest już zaufany. Mogą one być używane przez osoby atakujące, które przechodzą z pewnych złośliwych danych lub kradzieży poufnych danych w komunikacji przy użyciu protokołu HTTPS. |
| CA5401 | [CA5401 nie używaj modułu szyfrującego z wartością niedomyślną IV](../code-quality/ca5401.md) | Szyfrowanie symetryczne powinno zawsze używać niepowtarzalnych wektorów inicjalizacji, aby zapobiec atakom słownikowym. |
| CA5402 | [CA5402 Użyj szyfrowania z wartością domyślną IV](../code-quality/ca5402.md) | Szyfrowanie symetryczne powinno zawsze używać niepowtarzalnych wektorów inicjalizacji, aby zapobiec atakom słownikowym. |
| CA5403 | [CA5403: Nie zapisuj certyfikatu na stałe w kodzie](../code-quality/ca5403.md) | `data`Parametr lub `rawData` <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> konstruktora or jest zakodowany na stałe. |
| IL3000 | [IL3000 Unikaj dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczy plik](../code-quality/il3000.md) | Unikaj używania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku |
| IL3001 | [IL3001 unikać uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku](../code-quality/il3001.md) | Należy unikać uzyskiwania dostępu do ścieżki pliku zestawu podczas publikowania jako pojedynczego pliku |
