---
title: Stan portu reguły FxCop
ms.date: 05/21/2019
description: Dowiedz się więcej na temat reguł statycznej analizy kodu, które zostały przeanalizowane do analizatorów .NET w programie Visual Studio. Wyświetlanie reguł portów i zasobów podczas przenoszenia aktualizacji.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dde5a3d8ccf5557905395ee03d108e995ecffe7e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039578"
---
# <a name="fxcop-rule-port-status"></a>Stan portu reguły FxCop

Jeśli wcześniej użyto statycznej analizy kodu w programie Visual Studio, możesz zastanawiać się, które z tych reguł są dostępne w bieżącej implementacji jako [analizatory .NET](install-net-analyzers.md). Ta strona zawiera listę reguł, które zostały przemieszczone. Zobacz [nieportowe reguły](fxcop-unported-rules.md) dla tych, które nie zostały przełączone i czy istnieją plany dotyczące ich przenoszenia.

## <a name="ported-rules"></a>Przeniesione reguły

[Strona z automatycznie wygenerowaną dokumentacją](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) w repozytorium Roslyn-analizators ma najbardziej aktualną listę reguł, które zostały przeanalizowane do analizatorów Roslyn. Ta strona zawiera również dodatkowe informacje, takie jak to, czy reguła jest włączona domyślnie i czy ma skojarzoną *poprawkę kodu*. ([Poprawki kodu](../ide/quick-actions.md) są dostępne dla jednego kliknięcia w menu ikony żarówki w programie Visual Studio).

Od daty na tej stronie Lista reguł FxCop, które zostały [przeanalizowane do analizatorów .NET](install-net-analyzers.md) , obejmuje:

Identyfikator zasady | Tytuł
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Nie deklaruj statycznych składowych na typach ogólnych
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Nie uwidaczniaj list ogólnych
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Użyj ogólnych wystąpień procedury obsługi zdarzeń
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Unikaj nadmiernego użycia parametrów w typach ogólnych
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Typy wyliczeniowe powinny mieć wartość zero
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Kolekcje powinny implementować interfejs ogólny
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Typy abstrakcyjne nie powinny mieć konstruktorów
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Oznacz zestawy atrybutem CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Oznacz zestawy z wersją zestawu
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Oznacz zestawy atrybutem ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Oznacz atrybuty atrybutem AttributeUsage
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Zdefiniuj metody dostępu dla argumentów atrybutów
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Unikaj parametrów out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Używaj właściwości, o ile to możliwe
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Oznacz typy wyliczeniowe atrybutem Flags
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Magazyn wyliczeniowy powinien mieć wartość Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Używaj zdarzeń, o ile to możliwe
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Nie przechwytuj typów wyjątków ogólnych
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Zaimplementuj standardowe konstruktory wyjątków
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Metody interfejsu powinny móc zostać wywołane przez typy podrzędne
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Typy zagnieżdżone nie powinny być widoczne
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Przesłaniaj metody porównywalnych typów
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Unikaj pustych interfejsów
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Udostępnij komunikat ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Użyj argumentu całkowitego lub ciągu dla indeksatorów
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Właściwości nie powinny być tylko do zapisu
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Nie przekazuj typów przez odwołanie
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Nie przeciążaj operatora równości w typach referencyjnych
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Nie deklaruj chronionych składowych w typach zapieczętowanych
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Deklaruj typy w przestrzeniach nazw
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Nie deklaruj widocznych pól w wystąpieniach
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Statyczne typy posiadaczy powinny być statyczne lub NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Statyczne typy posiadaczy nie powinny mieć konstruktorów (CA1053 jest częścią [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) dla analizatorów .NET)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Parametry identyfikatora URI nie powinny być ciągami
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Zwracane wartości identyfikatora URI nie powinny być ciągami
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Właściwości identyfikatora URI nie powinny być ciągami
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Typy nie powinny rozszerzać niektórych typów podstawowych
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Przenieś PInvoke do klasy metod macierzystych
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Nie ukrywaj metod klasy bazowej
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Waliduj argumenty metod publicznych
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Zaimplementuj poprawnie interfejs IDisposable
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Wyjątki powinny być publiczne
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Typ {0} powinien implementować IEquatable \<T> , ponieważ zastępuje on wartość Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Zastąp obiekt. Equals (Object) podczas implementowania IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Nie przekazuj literałów jako zlokalizowanych parametrów
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Określ argument CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Określ argument IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Określ StringComparison dla jasności
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Normalizuj ciągi do postaci zapisanej wielkimi literami
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Użyj porównania ciągów porządkowych
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | Elementy P/Invoke nie powinny być widoczne
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Unikaj nadmiernego dziedziczenia
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Unikaj nadmiernej złożoności
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Unikaj kodu trudnego w utrzymaniu
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Unikaj nadmiernego sprzężenia klas
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Identyfikatory nie powinny zawierać znaków podkreślenia
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Identyfikatory powinny różnić się nie tylko wielkością liter
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Identyfikatory powinny mieć poprawny sufiks
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Identyfikatory nie powinny mieć nieprawidłowych sufiksów
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Zdarzenia nie powinny mieć prefiksu „before” ani „after”
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Identyfikatory powinny mieć poprawny prefiks
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Identyfikatory nie powinny być zgodne ze słowami kluczowymi
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | Identyfikator zawiera nazwę typu
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Nazwy właściwości nie powinny być takie same jak nazwy metod Get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Nazwy typów nie powinny być zgodne z przestrzeniami nazw
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Nazwy parametrów powinny być zgodne z deklaracją podstawową
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Dokonaj przeglądu nieużywanych parametrów
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Użyj literałów, tam gdzie to konieczne
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Nie Inicjuj niepotrzebnych
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Nie ignoruj wyników metod
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Inicjuj pola statyczne typu referencyjnego śródwierszowo
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Unikaj klas wewnętrznych bez wystąpień
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Unikaj niezapieczętowanych atrybutów
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Wybieraj tablice nieregularne zamiast wielowymiarowych
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Przesłaniaj metodę equals i operator równości w typach wartości
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Metody Dispose powinny wywoływać SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Właściwości nie powinny zwracać tablic
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Testuj obecność pustych ciągów przy użyciu długości ciągu
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Usuń puste finalizatory
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Oznaczaj składowe jako statyczne
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Unikaj nieużywanych pól prywatnych
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Unikaj alokacji tablic o zerowej długości.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Likwiduj obiekty przed utratą zakresu
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Nie blokuj obiektów o słabej tożsamości
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Określ kierowanie dla argumentów ciągu P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Przejrzyj widoczne procedury obsługi zdarzeń
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Nie Przechwytuj wyjątków uszkodzonych Stanów
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Zgłoś ponownie, aby zachować szczegóły stosu.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Nie zgłaszaj wyjątków o zastrzeżonych typach
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Pola statyczne typu wartości inicjuj bezpośrednio
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Poprawnie twórz wystąpienia wyjątków argumentów
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Pola niebędące stałymi nie powinny być widoczne
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Pola możliwe do likwidacji należy likwidować
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Nie wywołuj w konstruktorach metod, które można przesłaniać
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Metody Dispose powinny wywoływać metodę Dispose klasy bazowej
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Typy możliwe do likwidacji powinny deklarować finalizator
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Nie oznaczaj typów wyliczeniowych atrybutem Flags
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Nie zgłaszaj wyjątków w klauzulach finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Przeciążenia operatorów mają nazwane elementy alternatywne
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Operatory powinny mieć symetryczne przeciążenia
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Właściwości kolekcji powinny być tylko do odczytu
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Zaimplementuj konstruktory serializacji
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Operator przeciążenia jest równy w przypadku przesłaniania typu wartości równego
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Przekazanie obiektów URI systemu zamiast ciągów
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Oznacz wszystkie pola nieprzeznaczone do serializacji
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Oznacz typy ISerializable z możliwością serializacji
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Podaj poprawne argumenty metod formatowania
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Poprawnie testuj nie-liczby (NaN)
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Analiza literałów ciągów atrybutów powinna przebiegać poprawnie
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Nie używaj niezabezpieczonego deserializatora BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Nie używaj niezabezpieczonego deserializatora LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Nie wykonuj deserializacji bez uprzedniego ustawienia właściwości NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Nie używaj niezabezpieczonego deserializatora ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Nie wykonuj deserializacji za pomocą obiektu JavaScriptSerializer zainicjowanego przy użyciu parametru SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Upewnij się, że obiekt JavaScriptSerializer nie został zainicjowany przy użyciu parametru SimpleTypeResolver przed deserializacją
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Nie dodawaj schematu według adresu URL
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Niezabezpieczone przetwarzanie DTD w kodzie XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Niezabezpieczone przetwarzanie skryptów XSLT.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Niezabezpieczone przetwarzanie w projektach interfejsu API, XmlDocument i XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Oznaczanie programów obsługi zleceń przy użyciu tokenu weryfikacji
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Nie używaj słabych algorytmów kryptograficznych
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Nie używaj uszkodzonych algorytmów kryptograficznych
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Nie używaj niebezpiecznych trybów szyfrowania
CA5359 | Nie wyłączaj weryfikacji certyfikatu
CA5360 | Nie wywołuj niebezpiecznych metod w deserializacji
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Nie wyłączaj użycia silnej kryptografii SChannel
CA5362 | Nie Odwołuj się do siebie w klasie możliwej do serializacji
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Nie należy wyłączać weryfikacji żądania
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Nie używaj przestarzałych protokołów zabezpieczeń
CA5365 | Nie wyłączaj sprawdzania nagłówka HTTP
CA5366 | Użyj elementu XmlReader do odczytu pliku XML
CA5367 | Nie wykonuj serializacji typów z polami wskaźników
CA5368 | Ustaw ViewStateUserKey dla klas pochodnych ze strony
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Użyj elementu XmlReader do deserializacji
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Użyj elementu XmlReader do walidacji czytnika
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Użyj elementu XmlReader dla odczytu schematu
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Użyj elementu XmlReader dla XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Nie używaj przestarzałej funkcji wyprowadzania klucza
CA5374 | Nie używaj XslTransform
CA5375 | Nie używaj sygnatury dostępu współdzielonego konta
CA5376 | Korzystanie z SharedAccessProtocol HttpsOnly
CA5377 | Korzystanie z zasad dostępu na poziomie kontenera
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Nie wyłączaj protokołów ServicePointManagerSecurityProtocols
CA5379 | Nie używaj algorytmu funkcji wyprowadzania klucza słabego
CA9999 | Niezgodność wersji analizatora

## <a name="see-also"></a>Zobacz też

- [Reguły programu .NET Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
