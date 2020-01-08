---
title: Rozszerzone wytyczne dotyczące reguł projektowania dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: aad09901de2017ae14b65ec6e79f3153557c4d81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587644"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Rozszerzone wytyczne dotyczące reguł projektowania dla zarządzanego kodu

Zestaw reguł dla rozszerzonych wytycznych projektowych firmy Microsoft jest rozszerzany na podstawowe reguły dotyczące wytycznych projektowych w celu zmaksymalizowania raportowanych problemów z użytecznością i konserwacją. Dodatkowy nacisk jest umieszczany w wytycznych dotyczących nazewnictwa. Należy rozważyć uwzględnienie tego zestawu reguł, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najwyższe standardy do pisania kodu, który jest łatwy w obsłudze.

Rozszerzone reguły wskazówek dotyczących projektowania obejmują wszystkie reguły w podstawowych zestawach [reguł dla wytycznych projektowych](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , które obejmują reguły z zestawu reguł [zarządzanych zalecanych reguł](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

W poniższej tabeli opisano wszystkie reguły w zestawie reguł dla rozszerzonych wytycznych dotyczących projektowania firmy Microsoft.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1009](../code-quality/ca1009.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016.md)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1033](../code-quality/ca1033.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1060](../code-quality/ca1060.md)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Nie ukrywaj metod klasy bazowej|
|[CA1063](../code-quality/ca1063.md)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](../code-quality/ca1065.md)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401.md)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1821](../code-quality/ca1821.md)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2122](../code-quality/ca2122.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200.md)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2207](../code-quality/ca2207.md)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2212](../code-quality/ca2212.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](../code-quality/ca2213.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](../code-quality/ca2214.md)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](../code-quality/ca2216.md)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2229](../code-quality/ca2229.md)|Zaimplementuj konstruktory serializacji|
|[CA2231](../code-quality/ca2231.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2235](../code-quality/ca2235.md)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](../code-quality/ca2237.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Poprawnie implementuj metody serializacji|
|[CA2240](../code-quality/ca2240.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](../code-quality/ca2241.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242.md)|Poprawnie testuj nie-liczby (NaN)|
|[CA1000](../code-quality/ca1000.md)|Nie deklaruj statycznych składowych na typach ogólnych|
|[CA1002](../code-quality/ca1002.md)|Nie uwidaczniaj list ogólnych|
|[CA1003](../code-quality/ca1003.md)|Użyj ogólnych wystąpień procedury obsługi zdarzeń|
|[CA1004](../code-quality/ca1004.md)|Metody ogólne powinny podawać parametr typu|
|[CA1005](../code-quality/ca1005.md)|Unikaj nadmiernego użycia parametrów w typach ogólnych|
|[CA1006](../code-quality/ca1006.md)|Nie zagnieżdżaj typów ogólnych w podpisach składowych|
|[CA1007](../code-quality/ca1007.md)|Używaj typów ogólnych tam, gdzie to odpowiednie|
|[CA1008](../code-quality/ca1008.md)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1010](../code-quality/ca1010.md)|Kolekcje powinny implementować interfejs ogólny|
|[CA1011](../code-quality/ca1011.md)|Rozważ przekazywanie typów podstawowych jako parametrów|
|[CA1012](../code-quality/ca1012.md)|Typy abstrakcyjne nie powinny mieć konstruktorów|
|[CA1013](../code-quality/ca1013.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|
|[CA1014](../code-quality/ca1014.md)|Oznacz zestawy atrybutem CLSCompliant|
|[CA1017](../code-quality/ca1017.md)|Oznacz zestawy atrybutem ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|Oznacz atrybuty atrybutem AttributeUsage|
|[CA1019](../code-quality/ca1019.md)|Zdefiniuj metody dostępu dla argumentów atrybutów|
|[CA1023](../code-quality/ca1023.md)|Indeksatory nie powinny być wielowymiarowe|
|[CA1024](../code-quality/ca1024.md)|Używaj właściwości, o ile to możliwe|
|[CA1025](../code-quality/ca1025.md)|Zastąp powtarzalne argumenty tablicą params|
|[CA1026](../code-quality/ca1026.md)|Nie należy używać parametrów domyślnych|
|[CA1027](../code-quality/ca1027.md)|Oznacz typy wyliczeniowe atrybutem Flags|
|[CA1028](../code-quality/ca1028.md)|Magazyn typu wyliczeniowego powinien być typu Int32|
|[CA1030](../code-quality/ca1030.md)|Używaj zdarzeń, o ile to możliwe|
|[CA1031](../code-quality/ca1031.md)|Nie przechwytuj typów wyjątków ogólnych|
|[CA1032](../code-quality/ca1032.md)|Zaimplementuj standardowe konstruktory wyjątków|
|[CA1034](../code-quality/ca1034.md)|Typy zagnieżdżone nie powinny być widoczne|
|[CA1035](../code-quality/ca1035.md)|Implementacje interfejsu ICollection mają silnie typizowane składowe|
|[CA1036](../code-quality/ca1036.md)|Przesłaniaj metody porównywalnych typów|
|[CA1038](../code-quality/ca1038.md)|Moduły wyliczające powinny być silnie typizowane|
|[CA1039](../code-quality/ca1039.md)|Listy są silnie typizowane|
|[CA1041](../code-quality/ca1041.md)|Udostępnij komunikat ObsoleteAttribute|
|[CA1043](../code-quality/ca1043.md)|Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów|
|[CA1044](../code-quality/ca1044.md)|Właściwości nie powinny być tylko do zapisu|
|[CA1046](../code-quality/ca1046.md)|Nie przeciążaj operatora równości w typach referencyjnych|
|[CA1047](../code-quality/ca1047.md)|Nie deklaruj chronionych składowych w typach zapieczętowanych|
|[CA1048](../code-quality/ca1048.md)|Nie deklaruj wirtualnych składowych w typach zapieczętowanych|
|[CA1050](../code-quality/ca1050.md)|Deklaruj typy w przestrzeniach nazw|
|[CA1051](../code-quality/ca1051.md)|Nie deklaruj widocznych pól w wystąpieniach|
|[CA1052](../code-quality/ca1052.md)|Statyczne typy przechowujące powinny być zapieczętowane|
|[CA1053](../code-quality/ca1053.md)|Statyczne typy przechowujące nie powinny mieć konstruktorów|
|[CA1054](../code-quality/ca1054.md)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](../code-quality/ca1055.md)|Wartości zwracane identyfikatora URI nie powinny być ciągami|
|[CA1056](../code-quality/ca1056.md)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057.md)|Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri|
|[CA1058](../code-quality/ca1058.md)|Typy nie powinny rozszerzać niektórych typów podstawowych|
|[CA1059](../code-quality/ca1059.md)|Składowe nie powinny ujawniać niektórych typów konkretnych|
|[CA1064](../code-quality/ca1064.md)|Wyjątki powinny być publiczne|
|[CA1500](../code-quality/ca1500.md)|Nazwy zmiennych nie powinny być zgodne z nazwami pól|
|[CA1502](../code-quality/ca1502.md)|Unikaj nadmiernej złożoności|
|[CA1708](../code-quality/ca1708.md)|Identyfikatory powinny różnić się nie tylko wielkością liter|
|[CA1716](../code-quality/ca1716.md)|Identyfikatory nie powinny być zgodne ze słowami kluczowymi|
|[CA1801](../code-quality/ca1801.md)|Dokonaj przeglądu nieużywanych parametrów|
|[CA1804](../code-quality/ca1804.md)|Usuwaj nieużywane zmienne lokalne|
|[CA1809](../code-quality/ca1809.md)|Unikaj zbyt wielu zmiennych lokalnych|
|[CA1810](../code-quality/ca1810.md)|Inicjuj pola statyczne typu referencyjnego śródwierszowo|
|[CA1811](../code-quality/ca1811.md)|Unikaj niewywołanego kodu prywatnego|
|[CA1812](../code-quality/ca1812.md)|Unikaj klas wewnętrznych bez wystąpień|
|[CA1813](../code-quality/ca1813.md)|Unikaj niezapieczętowanych atrybutów|
|[CA1814](../code-quality/ca1814.md)|Wybieraj tablice nieregularne zamiast wielowymiarowych|
|[CA1815](../code-quality/ca1815.md)|Przesłaniaj metodę equals i operator równości w typach wartości|
|[CA1819](../code-quality/ca1819.md)|Właściwości nie powinny zwracać tablic|
|[CA1820](../code-quality/ca1820.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1822](../code-quality/ca1822.md)|Oznaczaj składowe jako statyczne|
|[CA1823](../code-quality/ca1823.md)|Unikaj nieużywanych pól prywatnych|
|[CA2201](../code-quality/ca2201.md)|Nie zgłaszaj wyjątków o zastrzeżonych typach|
|[CA2205](../code-quality/ca2205.md)|Użyj zarządzanych odpowiedników funkcji API Win32|
|[CA2208](../code-quality/ca2208.md)|Poprawnie twórz wystąpienia wyjątków argumentów|
|[CA2211](../code-quality/ca2211.md)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2217](../code-quality/ca2217.md)|Nie oznaczaj typów wyliczeniowych atrybutem Flags|
|[CA2219](../code-quality/ca2219.md)|Nie zgłaszaj wyjątków w klauzulach wyjątków|
|[CA2221](../code-quality/ca2221.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223.md)|Składowe powinny różnić się nie tylko zwracanym typem|
|[CA2224](../code-quality/ca2224.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|
|[CA2225](../code-quality/ca2225.md)|Przeciążenia operatorów mają nazwane elementy alternatywne|
|[CA2226](../code-quality/ca2226.md)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](../code-quality/ca2227.md)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2230](../code-quality/ca2230.md)|Użyj elementu params dla argumentów zmiennych|
|[CA2234](../code-quality/ca2234.md)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2239](../code-quality/ca2239.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
|[CA1020](../code-quality/ca1020.md)|Unikaj przestrzeni nazw z małą liczbą typów|
|[CA1021](../code-quality/ca1021.md)|Unikaj parametrów out|
|[CA1040](../code-quality/ca1040.md)|Unikaj pustych interfejsów|
|[CA1045](../code-quality/ca1045.md)|Nie przekazuj typów przez odwołanie|
|[CA1062](../code-quality/ca1062.md)|Waliduj argumenty metod publicznych|
|[CA1501](../code-quality/ca1501.md)|Unikaj nadmiernego dziedziczenia|
|[CA1504](../code-quality/ca1504.md)|Sprawdź pod kątem mylących nazw pól|
|[CA1505](../code-quality/ca1505.md)|Unikaj kodu trudnego w utrzymaniu|
|[CA1506](../code-quality/ca1506.md)|Unikaj nadmiernego sprzężenia klas|
|[CA1700](../code-quality/ca1700.md)|Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”|
|[CA1701](../code-quality/ca1701.md)|Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter|
|[CA1702](../code-quality/ca1702.md)|W wyrazach złożonych należy poprawnie używać wielkości liter|
|[CA1703](../code-quality/ca1703.md)|Pisownia ciągów zasobów powinna być poprawna|
|[CA1704](../code-quality/ca1704.md)|Pisownia identyfikatorów powinna być poprawna|
|[CA1707](../code-quality/ca1707.md)|Identyfikatory nie powinny zawierać znaków podkreślenia|
|[CA1709](../code-quality/ca1709.md)|Identyfikatory powinny mieć prawidłową wielkość liter|
|[CA1710](../code-quality/ca1710.md)|Identyfikatory powinny mieć poprawny sufiks|
|[CA1711](../code-quality/ca1711.md)|Identyfikatory nie powinny mieć nieprawidłowych sufiksów|
|[CA1712](../code-quality/ca1712.md)|Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych|
|[CA1713](../code-quality/ca1713.md)|Zdarzenia nie powinny mieć prefiksu „before” ani „after”|
|[CA1714](../code-quality/ca1714.md)|Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej|
|[CA1715](../code-quality/ca1715.md)|Identyfikatory powinny mieć poprawny prefiks|
|[CA1717](../code-quality/ca1717.md)|Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej|
|[CA1719](../code-quality/ca1719.md)|Nazwy parametrów nie powinny być zgodne z nazwami składowych|
|[CA1720](../code-quality/ca1720.md)|Identyfikatory nie powinny zawierać nazw typów|
|[CA1721](../code-quality/ca1721.md)|Nazwy właściwości nie powinny być takie same jak nazwy metod Get|
|[CA1722](../code-quality/ca1722.md)|Identyfikatory nie powinny mieć nieprawidłowych prefiksów|
|[CA1724](../code-quality/ca1724.md)|Nazwy typów nie powinny być takie same jak nazwy przestrzeni nazw|
|[CA1725](../code-quality/ca1725.md)|Nazwy parametrów powinny być zgodne z deklaracją podstawową|
|[CA1726](../code-quality/ca1726.md)|Używaj preferowanych terminów|
|[CA2204](../code-quality/ca2204.md)|Pisownia literałów powinna być poprawna|
