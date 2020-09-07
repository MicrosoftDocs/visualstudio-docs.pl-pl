---
title: Stan portu reguły FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508369"
---
# <a name="fxcop-rule-port-status"></a>Stan portu reguły FxCop

Jeśli wcześniej użyto statycznej analizy kodu w programie Visual Studio, możesz zastanawiać się, które z tych reguł są dostępne w bieżącej implementacji jako [analizatory FxCop](install-fxcop-analyzers.md). Ta strona zawiera listę reguł, które zostały przemieszczone. Zobacz [nieportowe reguły](fxcop-unported-rules.md) dla tych, które nie zostały przełączone i czy istnieją plany dotyczące ich przenoszenia.

## <a name="ported-rules"></a>Przeniesione reguły

[Strona z automatycznie wygenerowaną dokumentacją](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) w repozytorium Roslyn-analizators ma najbardziej aktualną listę reguł, które zostały przeanalizowane do analizatorów FxCop. Ta strona zawiera również dodatkowe informacje, takie jak to, czy reguła jest włączona domyślnie i czy ma skojarzoną *poprawkę kodu*. ([Poprawki kodu](../ide/quick-actions.md) są dostępne dla jednego kliknięcia w menu ikony żarówki w programie Visual Studio).

Od daty na tej stronie Lista reguł FxCop, które zostały [przeanalizowane do analizatorów FxCop](install-fxcop-analyzers.md) , obejmuje:

Identyfikator zasady | Tytuł
--------|---------
[CA1000](ca1000.md) | Nie deklaruj statycznych składowych na typach ogólnych
[CA1001](ca1001.md) | Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji
[CA1002](ca1002.md) | Nie uwidaczniaj list ogólnych
[CA1003](ca1003.md) | Użyj ogólnych wystąpień procedury obsługi zdarzeń
[CA1005](ca1005.md) | Unikaj nadmiernego użycia parametrów w typach ogólnych
[CA1008](ca1008.md) | Typy wyliczeniowe powinny mieć wartość zero
[CA1010](ca1010.md) | Kolekcje powinny implementować interfejs ogólny
[CA1012](ca1012.md) | Typy abstrakcyjne nie powinny mieć konstruktorów
[CA1014](ca1014.md) | Oznacz zestawy atrybutem CLSCompliant
[CA1016](ca1016.md) | Oznacz zestawy z wersją zestawu
[CA1017](ca1017.md) | Oznacz zestawy atrybutem ComVisible
[CA1018](ca1018.md) | Oznacz atrybuty atrybutem AttributeUsage
[CA1019](ca1019.md) | Zdefiniuj metody dostępu dla argumentów atrybutów
[CA1021](ca1021.md) | Unikaj parametrów out
[CA1024](ca1024.md) | Używaj właściwości, o ile to możliwe
[CA1027](ca1027.md) | Oznacz typy wyliczeniowe atrybutem Flags
[CA1028](ca1028.md) | Magazyn wyliczeniowy powinien mieć wartość Int32
[CA1030](ca1030.md) | Używaj zdarzeń, o ile to możliwe
[CA1031](ca1031.md) | Nie przechwytuj typów wyjątków ogólnych
[CA1032](ca1032.md) | Zaimplementuj standardowe konstruktory wyjątków
[CA1033](ca1033.md) | Metody interfejsu powinny móc zostać wywołane przez typy podrzędne
[CA1034](ca1034.md) | Typy zagnieżdżone nie powinny być widoczne
[CA1036](ca1036.md) | Przesłaniaj metody porównywalnych typów
[CA1040](ca1040.md) | Unikaj pustych interfejsów
[CA1041](ca1041.md) | Udostępnij komunikat ObsoleteAttribute
[CA1043](ca1043.md) | Użyj argumentu całkowitego lub ciągu dla indeksatorów
[CA1044](ca1044.md) | Właściwości nie powinny być tylko do zapisu
[CA1045](ca1045.md) | Nie przekazuj typów przez odwołanie
[CA1046](ca1046.md) | Nie przeciążaj operatora równości w typach referencyjnych
[CA1047](ca1047.md) | Nie deklaruj chronionych składowych w typach zapieczętowanych
[CA1050](ca1050.md) | Deklaruj typy w przestrzeniach nazw
[CA1051](ca1051.md) | Nie deklaruj widocznych pól w wystąpieniach
[CA1052](ca1052.md) | Statyczne typy posiadaczy powinny być statyczne lub NotInheritable
[CA1053](ca1053.md) | Statyczne typy elementów zastępczych nie powinny mieć konstruktorów (CA1053 jest częścią [CA1052](ca1052.md) dla analizatorów FxCop)
[CA1054](ca1054.md) | Parametry identyfikatora URI nie powinny być ciągami
[CA1055](ca1055.md) | Zwracane wartości identyfikatora URI nie powinny być ciągami
[CA1056](ca1056.md) | Właściwości identyfikatora URI nie powinny być ciągami
[CA1058](ca1058.md) | Typy nie powinny rozszerzać niektórych typów podstawowych
[CA1060](ca1060.md) | Przenieś PInvoke do klasy metod macierzystych
[CA1061](ca1061.md) | Nie ukrywaj metod klasy bazowej
[CA1062](ca1062.md) | Waliduj argumenty metod publicznych
[CA1063](ca1063.md) | Zaimplementuj poprawnie interfejs IDisposable
[CA1064](ca1064.md) | Wyjątki powinny być publiczne
[CA1065](ca1065.md) | Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach
[CA1066](ca1066.md) | Typ {0} powinien implementować IEquatable \<T> , ponieważ zastępuje on wartość Equals
[CA1067](ca1067.md) | Zastąp obiekt. Equals (Object) podczas implementowania IEquatable\<T>
[CA1303](ca1303.md) | Nie przekazuj literałów jako zlokalizowanych parametrów
[CA1304](ca1304.md) | Określ argument CultureInfo
[CA1305](ca1305.md) | Określ argument IFormatProvider
[CA1307](ca1307.md) | Określ StringComparison dla jasności
[CA1308](ca1308.md) | Normalizuj ciągi do postaci zapisanej wielkimi literami
[CA1309](ca1309.md) | Użyj porównania ciągów porządkowych
[CA1401](ca1401.md) | Elementy P/Invoke nie powinny być widoczne
[CA1501](ca1501.md) | Unikaj nadmiernego dziedziczenia
[CA1502](ca1502.md) | Unikaj nadmiernej złożoności
[CA1505](ca1505.md) | Unikaj kodu trudnego w utrzymaniu
[CA1506](ca1506.md) | Unikaj nadmiernego sprzężenia klas
[CA1700](ca1700.md) | Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”
[CA1707](ca1707.md) | Identyfikatory nie powinny zawierać znaków podkreślenia
[CA1708](ca1708.md) | Identyfikatory powinny różnić się nie tylko wielkością liter
[CA1710](ca1710.md) | Identyfikatory powinny mieć poprawny sufiks
[CA1711](ca1711.md) | Identyfikatory nie powinny mieć nieprawidłowych sufiksów
[CA1712](ca1712.md) | Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych
[CA1713](ca1713.md) | Zdarzenia nie powinny mieć prefiksu „before” ani „after”
[CA1714](ca1714.md) | Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1715](ca1715.md) | Identyfikatory powinny mieć poprawny prefiks
[CA1716](ca1716.md) | Identyfikatory nie powinny być zgodne ze słowami kluczowymi
[CA1717](ca1717.md) | Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1720](ca1720.md) | Identyfikator zawiera nazwę typu
[CA1721](ca1721.md) | Nazwy właściwości nie powinny być takie same jak nazwy metod Get
[CA1724](ca1724.md) | Nazwy typów nie powinny być zgodne z przestrzeniami nazw
[CA1725](ca1725.md) | Nazwy parametrów powinny być zgodne z deklaracją podstawową
[CA1801](ca1801.md) | Dokonaj przeglądu nieużywanych parametrów
[CA1802](ca1802.md) | Użyj literałów, tam gdzie to konieczne
[CA1805](ca1805.md) | Nie Inicjuj niepotrzebnych
[CA1806](ca1806.md) | Nie ignoruj wyników metod
[CA1810](ca1810.md) | Inicjuj pola statyczne typu referencyjnego śródwierszowo
[CA1812](ca1812.md) | Unikaj klas wewnętrznych bez wystąpień
[CA1813](ca1813.md) | Unikaj niezapieczętowanych atrybutów
[CA1814](ca1814.md) | Wybieraj tablice nieregularne zamiast wielowymiarowych
[CA1815](ca1815.md) | Przesłaniaj metodę equals i operator równości w typach wartości
[CA1816](ca1816.md) | Metody Dispose powinny wywoływać SuppressFinalize
[CA1819](ca1819.md) | Właściwości nie powinny zwracać tablic
[CA1820](ca1820.md) | Testuj obecność pustych ciągów przy użyciu długości ciągu
[CA1821](ca1821.md) | Usuń puste finalizatory
[CA1822](ca1822.md) | Oznaczaj składowe jako statyczne
[CA1823](ca1823.md) | Unikaj nieużywanych pól prywatnych
[CA1824](ca1824.md) | Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | Unikaj alokacji tablic o zerowej długości.
[CA2000](ca2000.md) | Likwiduj obiekty przed utratą zakresu
[CA2002](ca2002.md) | Nie blokuj obiektów o słabej tożsamości
[CA2100](ca2100.md) | Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach
[CA2101](ca2101.md) | Określ kierowanie dla argumentów ciągu P/Invoke
[CA2109](ca2109.md) | Przejrzyj widoczne procedury obsługi zdarzeń
[CA2119](ca2119.md) | Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[CA2153](ca2153.md) | Nie Przechwytuj wyjątków uszkodzonych Stanów
[CA2200](ca2200.md) | Zgłoś ponownie, aby zachować szczegóły stosu.
[CA2201](ca2201.md) | Nie zgłaszaj wyjątków o zastrzeżonych typach
[CA2207](ca2207.md) | Pola statyczne typu wartości inicjuj bezpośrednio
[CA2208](ca2208.md) | Poprawnie twórz wystąpienia wyjątków argumentów
[CA2211](ca2211.md) | Pola niebędące stałymi nie powinny być widoczne
[CA2213](ca2213.md) | Pola możliwe do likwidacji należy likwidować
[CA2214](ca2214.md) | Nie wywołuj w konstruktorach metod, które można przesłaniać
[CA2215](ca2215.md) | Metody Dispose powinny wywoływać metodę Dispose klasy bazowej
[CA2216](ca2216.md) | Typy możliwe do likwidacji powinny deklarować finalizator
[CA2217](ca2217.md) | Nie oznaczaj typów wyliczeniowych atrybutem Flags
[CA2219](ca2219.md) | Nie zgłaszaj wyjątków w klauzulach finally
[CA2225](ca2225.md) | Przeciążenia operatorów mają nazwane elementy alternatywne
[CA2226](ca2226.md) | Operatory powinny mieć symetryczne przeciążenia
[CA2227](ca2227.md) | Właściwości kolekcji powinny być tylko do odczytu
[CA2229](ca2229.md) | Zaimplementuj konstruktory serializacji
[CA2231](ca2231.md) | Operator przeciążenia jest równy w przypadku przesłaniania typu wartości równego
[CA2234](ca2234.md) | Przekazanie obiektów URI systemu zamiast ciągów
[CA2235](ca2235.md) | Oznacz wszystkie pola nieprzeznaczone do serializacji
[CA2237](ca2237.md) | Oznacz typy ISerializable z możliwością serializacji
[CA2241](ca2241.md) | Podaj poprawne argumenty metod formatowania
[CA2242](ca2242.md) | Poprawnie testuj nie-liczby (NaN)
[CA2243](ca2243.md) | Analiza literałów ciągów atrybutów powinna przebiegać poprawnie
[CA2300](ca2300.md) | Nie używaj niezabezpieczonego deserializatora BinaryFormatter
[CA2301](ca2301.md) | Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder
[CA2302](ca2302.md) | Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize
[CA2305](ca2305.md) | Nie używaj niezabezpieczonego deserializatora LosFormatter
[CA2310](ca2310.md) | Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer
[CA2311](ca2311.md) | Nie wykonuj deserializacji bez uprzedniego ustawienia właściwości NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją
[CA2315](ca2315.md) | Nie używaj niezabezpieczonego deserializatora ObjectStateFormatter
[CA2321](ca2321.md) | Nie wykonuj deserializacji za pomocą obiektu JavaScriptSerializer zainicjowanego przy użyciu parametru SimpleTypeResolver
[CA2322](ca2322.md) | Upewnij się, że obiekt JavaScriptSerializer nie został zainicjowany przy użyciu parametru SimpleTypeResolver przed deserializacją
[CA3001](ca3001.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL
[CA3002](ca3002.md) | Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami
[CA3003](ca3003.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku
[CA3004](ca3004.md) | Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji
[CA3005](ca3005.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP
[CA3006](ca3006.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu
[CA3007](ca3007.md) | Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania
[CA3008](ca3008.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath
[CA3009](ca3009.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML
[CA3010](ca3010.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML
[CA3011](ca3011.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL
[CA3012](ca3012.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego
[CA3061](ca3061.md) | Nie dodawaj schematu według adresu URL
[CA3075](ca3075.md) | Niezabezpieczone przetwarzanie DTD w kodzie XML
[CA3076](ca3076.md) | Niezabezpieczone przetwarzanie skryptów XSLT.
[CA3077](ca3077.md) | Niezabezpieczone przetwarzanie w projektach interfejsu API, XmlDocument i XmlTextReader
[CA3147](ca3147.md) | Oznaczanie programów obsługi zleceń przy użyciu tokenu weryfikacji
[CA5350](ca5350.md) | Nie używaj słabych algorytmów kryptograficznych
[CA5351](ca5351.md) | Nie używaj uszkodzonych algorytmów kryptograficznych
[CA5358](ca5358.md) | Nie używaj niebezpiecznych trybów szyfrowania
CA5359 | Nie wyłączaj weryfikacji certyfikatu
CA5360 | Nie wywołuj niebezpiecznych metod w deserializacji
[CA5361](ca5361.md) | Nie wyłączaj użycia silnej kryptografii SChannel
CA5362 | Nie Odwołuj się do siebie w klasie możliwej do serializacji
[CA5363](ca5363.md) | Nie należy wyłączać weryfikacji żądania
[CA5364](ca5364.md) | Nie używaj przestarzałych protokołów zabezpieczeń
CA5365 | Nie wyłączaj sprawdzania nagłówka HTTP
CA5366 | Użyj elementu XmlReader do odczytu pliku XML
CA5367 | Nie wykonuj serializacji typów z polami wskaźników
CA5368 | Ustaw ViewStateUserKey dla klas pochodnych ze strony
[CA5369](ca5369.md) | Użyj elementu XmlReader do deserializacji
[CA5370](ca5370.md) | Użyj elementu XmlReader do walidacji czytnika
[CA5371](ca5371.md) | Użyj elementu XmlReader dla odczytu schematu
[CA5372](ca5372.md) | Użyj elementu XmlReader dla XPathDocument
[CA5373](ca5373.md) | Nie używaj przestarzałej funkcji wyprowadzania klucza
CA5374 | Nie używaj XslTransform
CA5375 | Nie używaj sygnatury dostępu współdzielonego konta
CA5376 | Korzystanie z SharedAccessProtocol HttpsOnly
CA5377 | Korzystanie z zasad dostępu na poziomie kontenera
[CA5378](ca5378.md) | Nie wyłączaj protokołów ServicePointManagerSecurityProtocols
CA5379 | Nie używaj algorytmu funkcji wyprowadzania klucza słabego
CA9999 | Niezgodność wersji analizatora

## <a name="see-also"></a>Zobacz także

- [Reguły Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
