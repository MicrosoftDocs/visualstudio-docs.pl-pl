---
title: Podstawowe reguły zasad projektowania dla zarządzanego kodu
ms.date: 11/04/2016
description: Zapoznaj się z podstawowymi regułami wytycznych dotyczących projektowania w programie Visual Studio, które ułatwiają zrozumienie i używanie kodu. Zobacz opisy reguł.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: bde7081f69a4f92092ac6f3c5b0e8b8059e17a1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849752"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Podstawowe reguły zasad projektowania dla zarządzanego kodu

Za pomocą zestawu reguł podstawowych wytycznych dotyczących projektowania firmy Microsoft można skupić się na ułatwianiu zrozumienia i użycia kodu. Ten zestaw reguł należy dołączyć, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najlepsze rozwiązania dla kodu, który jest łatwy do utrzymania.

Podstawowe reguły wytycznych dotyczących projektowania obejmują wszystkie reguły w zestawie reguł [zalecanych przez zarządzane reguły](managed-recommended-rules-rule-set-for-managed-code.md) .

W poniższej tabeli opisano wszystkie reguły w zestawie reguł podstawowych wytycznych dotyczących projektowania firmy Microsoft.

|Reguła|Opis|
|----------|-----------------|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Nie deklaruj statycznych składowych na typach ogólnych|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Nie uwidaczniaj list ogólnych|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Użyj ogólnych wystąpień procedury obsługi zdarzeń|
|[CA1004](../code-quality/ca1004.md)|Metody ogólne powinny podawać parametr typu|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Unikaj nadmiernego użycia parametrów w typach ogólnych|
|[CA1006](../code-quality/ca1006.md)|Nie zagnieżdżaj typów ogólnych w podpisach składowych|
|[CA1007](../code-quality/ca1007.md)|Używaj typów ogólnych tam, gdzie to odpowiednie|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1009](../code-quality/ca1009.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Kolekcje powinny implementować interfejs ogólny|
|[CA1011](../code-quality/ca1011.md)|Rozważ przekazywanie typów podstawowych jako parametrów|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Typy abstrakcyjne nie powinny mieć konstruktorów|
|[CA1013](../code-quality/ca1013.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Oznacz zestawy atrybutem CLSCompliant|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Oznacz zestawy atrybutem ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Oznacz atrybuty atrybutem AttributeUsage|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Zdefiniuj metody dostępu dla argumentów atrybutów|
|[CA1023](../code-quality/ca1023.md)|Indeksatory nie powinny być wielowymiarowe|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Używaj właściwości, o ile to możliwe|
|[CA1025](../code-quality/ca1025.md)|Zastąp powtarzalne argumenty tablicą params|
|[CA1026](../code-quality/ca1026.md)|Nie należy używać parametrów domyślnych|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Oznacz typy wyliczeniowe atrybutem Flags|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Magazyn typu wyliczeniowego powinien być typu Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Używaj zdarzeń, o ile to możliwe|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Nie przechwytuj typów wyjątków ogólnych|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Zaimplementuj standardowe konstruktory wyjątków|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Typy zagnieżdżone nie powinny być widoczne|
|[CA1035](../code-quality/ca1035.md)|Implementacje interfejsu ICollection mają silnie typizowane składowe|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Przesłaniaj metody porównywalnych typów|
|[CA1038](../code-quality/ca1038.md)|Moduły wyliczające powinny być silnie typizowane|
|[CA1039](../code-quality/ca1039.md)|Listy są silnie typizowane|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Udostępnij komunikat ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Właściwości nie powinny być tylko do zapisu|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Nie przeciążaj operatora równości w typach referencyjnych|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Nie deklaruj chronionych składowych w typach zapieczętowanych|
|[CA1048](../code-quality/ca1048.md)|Nie deklaruj wirtualnych składowych w typach zapieczętowanych|
|[CA1049](../code-quality/ca1049.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Deklaruj typy w przestrzeniach nazw|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Nie deklaruj widocznych pól w wystąpieniach|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Statyczne typy przechowujące powinny być zapieczętowane|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Statyczne typy przechowujące nie powinny mieć konstruktorów|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Wartości zwracane identyfikatora URI nie powinny być ciągami|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057.md)|Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Typy nie powinny rozszerzać niektórych typów podstawowych|
|[CA1059](../code-quality/ca1059.md)|Składowe nie powinny ujawniać niektórych typów konkretnych|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Nie ukrywaj metod klasy bazowej|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Wyjątki powinny być publiczne|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1500](../code-quality/ca1500.md)|Nazwy zmiennych nie powinny być zgodne z nazwami pól|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Unikaj nadmiernej złożoności|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Identyfikatory powinny różnić się nie tylko wielkością liter|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Identyfikatory nie powinny być zgodne ze słowami kluczowymi|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Dokonaj przeglądu nieużywanych parametrów|
|[CA1804](../code-quality/ca1804.md)|Usuwaj nieużywane zmienne lokalne|
|[CA1809](../code-quality/ca1809.md)|Unikaj zbyt wielu zmiennych lokalnych|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Inicjuj pola statyczne typu referencyjnego śródwierszowo|
|[CA1811](../code-quality/ca1811.md)|Unikaj niewywołanego kodu prywatnego|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Unikaj klas wewnętrznych bez wystąpień|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Unikaj niezapieczętowanych atrybutów|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Wybieraj tablice nieregularne zamiast wielowymiarowych|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Przesłaniaj metodę equals i operator równości w typach wartości|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Właściwości nie powinny zwracać tablic|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Usuwaj puste finalizatory|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Oznaczaj składowe jako statyczne|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Unikaj nieużywanych pól prywatnych|
|[CA1900](../code-quality/ca1900.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Określ kierowanie dla argumentów ciągu P/Invoke|
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
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Nie zgłaszaj wyjątków o zastrzeżonych typach|
|[CA2202](../code-quality/ca2202.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2205](../code-quality/ca2205.md)|Użyj zarządzanych odpowiedników funkcji API Win32|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Poprawnie twórz wystąpienia wyjątków argumentów|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2212](../code-quality/ca2212.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Nie oznaczaj typów wyliczeniowych atrybutem Flags|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Nie zgłaszaj wyjątków w klauzulach wyjątków|
|[CA2220](../code-quality/ca2220.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2221](../code-quality/ca2221.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223.md)|Składowe powinny różnić się nie tylko zwracanym typem|
|[CA2224](../code-quality/ca2224.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Przeciążenia operatorów mają nazwane elementy alternatywne|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Zaimplementuj konstruktory serializacji|
|[CA2230](../code-quality/ca2230.md)|Użyj elementu params dla argumentów zmiennych|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Poprawnie implementuj metody serializacji|
|[CA2239](../code-quality/ca2239.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
|[CA2240](../code-quality/ca2240.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Podaj poprawne argumenty metod formatowania|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Poprawnie testuj nie-liczby (NaN)|
