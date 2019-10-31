---
title: Stan portu reguły FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 571ba2a0c015d6d3a3c8757c25a0058d8e3ad8e1
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188817"
---
# <a name="fxcop-rule-port-status"></a>Stan portu reguły FxCop

Jeśli wcześniej użyto statycznej analizy kodu w programie Visual Studio, możesz zastanawiać się, które z tych reguł są dostępne w bieżącej implementacji jako [analizatory FxCop](install-fxcop-analyzers.md). Ta strona zawiera listę reguł, które są portami, a także te, które nie zostały przełączone i czy istnieją plany portów.

## <a name="ported-rules"></a>Przeniesione reguły

[Strona z automatycznie wygenerowaną dokumentacją](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) w repozytorium Roslyn-analizators ma najbardziej aktualną listę reguł, które zostały przeanalizowane do analizatorów FxCop. Ta strona zawiera również dodatkowe informacje, takie jak to, czy reguła jest włączona domyślnie i czy ma skojarzoną *poprawkę kodu*. ([Poprawki kodu](../ide/quick-actions.md) są dostępne dla jednego kliknięcia w menu ikony żarówki w programie Visual Studio).

Od daty na tej stronie Lista reguł FxCop, które zostały [przeanalizowane do analizatorów FxCop](install-fxcop-analyzers.md) , obejmuje:

Identyfikator reguły | Tytuł
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Nie deklaruj statycznych składowych na typach ogólnych
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji
[CA1003](ca1003-use-generic-event-handler-instances.md) | Użyj ogólnych wystąpień procedury obsługi zdarzeń
[CA1008](ca1008-enums-should-have-zero-value.md) | Typy wyliczeniowe powinny mieć wartość zero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Kolekcje powinny implementować interfejs ogólny
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Typy abstrakcyjne nie powinny mieć konstruktorów
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Oznacz zestawy atrybutem CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Oznacz zestawy z wersją zestawu
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Oznacz zestawy atrybutem ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Oznacz atrybuty atrybutem AttributeUsage
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Zdefiniuj metody dostępu dla argumentów atrybutów
[CA1024](ca1024-use-properties-where-appropriate.md) | Używaj właściwości, o ile to możliwe
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Oznacz typy wyliczeniowe atrybutem Flags
[CA1028](ca1028-enum-storage-should-be-int32.md) | Magazyn wyliczeniowy powinien mieć wartość Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Używaj zdarzeń, o ile to możliwe
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Nie przechwytuj typów wyjątków ogólnych
[CA1032](ca1032-implement-standard-exception-constructors.md) | Zaimplementuj standardowe konstruktory wyjątków
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Metody interfejsu powinny móc zostać wywołane przez typy podrzędne
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Typy zagnieżdżone nie powinny być widoczne
[CA1036](ca1036-override-methods-on-comparable-types.md) | Przesłaniaj metody porównywalnych typów
[CA1040](ca1040-avoid-empty-interfaces.md) | Unikaj pustych interfejsów
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Udostępnij komunikat ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Użyj argumentu całkowitego lub ciągu dla indeksatorów
[CA1044](ca1044-properties-should-not-be-write-only.md) | Właściwości nie powinny być tylko do zapisu
[CA1050](ca1050-declare-types-in-namespaces.md) | Deklaruj typy w przestrzeniach nazw
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Nie deklaruj widocznych pól w wystąpieniach
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Statyczne typy posiadaczy powinny być statyczne lub NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Statyczne typy elementów zastępczych nie powinny mieć konstruktorów (CA1053 jest częścią [CA1052](ca1052-static-holder-types-should-be-sealed.md) dla analizatorów FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Parametry identyfikatora URI nie powinny być ciągami
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Zwracane wartości identyfikatora URI nie powinny być ciągami
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Właściwości identyfikatora URI nie powinny być ciągami
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Typy nie powinny rozszerzać niektórych typów podstawowych
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Przenieś PInvoke do klasy metod macierzystych
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Nie ukrywaj metod klasy bazowej
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Waliduj argumenty metod publicznych
[CA1063](ca1063-implement-idisposable-correctly.md) | Zaimplementuj poprawnie interfejs IDisposable
[CA1064](ca1064-exceptions-should-be-public.md) | Wyjątki powinny być publiczne
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach
CA1066 | Typ {0} powinien implementować > \<T IEquatable, ponieważ zastępuje on wartość Equals
CA1067 | Zastąp obiekt. Equals (Object) podczas implementowania \<T IEquatable >
[CA1068](ca1068.md) | Parametry CancellationToken muszą występować na końcu
CA1200 | Unikaj używania tagów cref z prefiksem
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Nie przekazuj literałów jako zlokalizowanych parametrów
[CA1304](ca1304-specify-cultureinfo.md) | Określ argument CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Określ argument IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Określ argument StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizuj ciągi do postaci zapisanej wielkimi literami
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Użyj porównania ciągów porządkowych
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Elementy P/Invoke nie powinny być widoczne
[CA1501](ca1501-avoid-excessive-inheritance.md) | Unikaj nadmiernego dziedziczenia
[CA1502](ca1502-avoid-excessive-complexity.md) | Unikaj nadmiernej złożoności
[CA1505](ca1505-avoid-unmaintainable-code.md) | Unikaj kodu trudnego w utrzymaniu
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Unikaj nadmiernego sprzężenia klas
[CA1507](ca1507.md) | Użyj nameof do ekspresowych nazw symboli
CA1508 | Unikaj nieaktywnego kodu warunkowego
CA1509 | Nieprawidłowy wpis w pliku specyfikacji reguł metryk kodu
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Identyfikatory nie powinny zawierać znaków podkreślenia
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Identyfikatory powinny różnić się nie tylko wielkością liter
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Identyfikatory powinny mieć poprawny sufiks
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Identyfikatory nie powinny mieć nieprawidłowych sufiksów
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Identyfikatory powinny mieć poprawny prefiks
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Identyfikatory nie powinny być zgodne ze słowami kluczowymi
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Identyfikator zawiera nazwę typu
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Nazwy właściwości nie powinny być takie same jak nazwy metod Get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Nazwy typów nie powinny być zgodne z przestrzeniami nazw
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Nazwy parametrów powinny być zgodne z deklaracją podstawową
[CA1801](ca1801.md) | Dokonaj przeglądu nieużywanych parametrów
[CA1802](ca1802.md) | Użyj literałów, tam gdzie to konieczne
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
CA1825 | Unikaj alokacji tablic o zerowej długości.
CA1826 | Nie należy używać wyliczalnych metod w kolekcjach indeksowanych. Zamiast tego użyj kolekcji bezpośrednio
[CA2000](ca2000.md) | Likwiduj obiekty przed utratą zakresu
[CA2002](ca2002.md) | Nie blokuj obiektów o słabej tożsamości
[CA2007](ca2007.md) | Rozważ wywołanie ConfigureAwait w zadaniu oczekującym
CA2008 | Nie twórz zadań bez przekazywania elementu TaskScheduler
CA2009 | Nie wywołuj ToImmutableCollection dla niezmiennej wartościcollection
CA2010 | Zawsze korzystaj z wartości zwracanej przez metody oznaczone atrybutem PreserveSigAttribute
[CA2100](ca2100.md) | Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach
[CA2101](ca2101.md) | Określ kierowanie dla argumentów ciągu P/Invoke
[CA2119](ca2119.md) | Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[CA2153](ca2153.md) | Nie Przechwytuj wyjątków uszkodzonych Stanów
[CA2200](ca2200.md) | Zgłoś ponownie, aby zachować szczegóły stosu.
[CA2201](ca2201.md) | Nie zgłaszaj wyjątków o zastrzeżonych typach
[CA2207](ca2207.md) | Pola statyczne typu wartości inicjuj bezpośrednio
[CA2208](ca2208.md) | Poprawnie twórz wystąpienia wyjątków argumentów
[CA2211](ca2211.md) | Pola niebędące stałymi nie powinny być widoczne
[CA2213](ca2213.md) | Pola możliwe do likwidacji należy likwidować
[CA2214](ca2214.md) | Nie wywołuj w konstruktorach metod, które można przesłaniać
[CA2216](ca2216.md) | Typy możliwe do likwidacji powinny deklarować finalizator
[CA2217](ca2217.md) | Nie oznaczaj typów wyliczeniowych atrybutem Flags
[CA2218](ca2218.md) | Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals
[CA2219](ca2219.md) | Nie zgłaszaj wyjątków w klauzulach finally
[CA2224](ca2224.md) | Zastąp wartość Equals przy przeciążeniu operatora Equals
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
CA2244 | Nie Duplikuj zainicjowanych elementów indeksowanych
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
CA3061 | Nie dodawaj schematu według adresu URL
[CA3075](ca3075.md) | Niezabezpieczone przetwarzanie DTD w kodzie XML
[CA3076](ca3076.md) | Niezabezpieczone przetwarzanie skryptów XSLT.
[CA3077](ca3077.md) | Niezabezpieczone przetwarzanie w projektach interfejsu API, XmlDocument i XmlTextReader
[CA3147](ca3147.md) | Oznaczanie programów obsługi zleceń przy użyciu tokenu weryfikacji
[CA5350](ca5350.md) | Nie używaj słabych algorytmów kryptograficznych
[CA5351](ca5351.md) | Nie używaj uszkodzonych algorytmów kryptograficznych
CA5358 | Nie używaj niebezpiecznych trybów szyfrowania
CA5359 | Nie wyłączaj weryfikacji certyfikatu
CA5360 | Nie wywołuj niebezpiecznych metod w deserializacji
CA5361 | Nie wyłączaj użycia silnej kryptografii SChannel
CA5362 | Nie Odwołuj się do siebie w klasie możliwej do serializacji
CA5363 | Nie należy wyłączać weryfikacji żądania
CA5364 | Nie używaj przestarzałych protokołów zabezpieczeń
CA5365 | Nie wyłączaj sprawdzania nagłówka HTTP
CA5366 | Użyj elementu XmlReader do odczytu pliku XML
CA5367 | Nie wykonuj serializacji typów z polami wskaźników
CA5368 | Ustaw ViewStateUserKey dla klas pochodnych ze strony
CA5369 | Użyj elementu XmlReader do deserializacji
CA5370 | Użyj elementu XmlReader do walidacji czytnika
CA5371 | Użyj elementu XmlReader dla odczytu schematu
CA5372 | Użyj elementu XmlReader dla XPathDocument
CA5373 | Nie używaj przestarzałej funkcji wyprowadzania klucza
CA5374 | Nie używaj XslTransform
CA5375 | Nie używaj sygnatury dostępu współdzielonego konta
CA5376 | Korzystanie z SharedAccessProtocol HttpsOnly
CA5377 | Korzystanie z zasad dostępu na poziomie kontenera
CA5378 | Nie wyłączaj protokołów ServicePointManagerSecurityProtocols
CA5379 | Nie używaj algorytmu funkcji wyprowadzania klucza słabego
CA9999 | Niezgodność wersji analizatora

## <a name="unported-rules"></a>Reguły nieportowe

Zestaw reguł, które nie zostały przełączone do [analizatorów FxCop](install-fxcop-analyzers.md) , składa się z reguł, które nie zostały jeszcze, ale nadal [mogą być](#rules-that-may-be-ported)przełączone i które są przestarzałe i [nie zostaną](#deprecated-rules)przełączone.

### <a name="rules-that-may-be-ported"></a>Reguły, które mogą być przewoźny

Następujące reguły FxCop starszej wersji nie zostały jeszcze zaimplementowane jako analizatory, ale nadal mogą być. Może to być spowodowane zablokowaniem przyczyny technicznej lub po prostu, że reguła ma niższy priorytet. Aby uzyskać więcej informacji o stanie przenoszenia poszczególnych reguł, kliknij link w kolumnie **Śledzenie problemów** .

Identyfikator reguły | Problem ze śledzeniem
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Przestarzałe reguły

Następujące reguły FxCop starszej wersji są przestarzałe i nie zostaną zaimplementowane jako analizatory. Aby uzyskać więcej informacji, możesz wyszukiwać według identyfikatora reguły (na przykład **CA1009**) na [stronie problemów z usługą GitHub dla analizatorów Roslyn](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702-compound-words-should-be-cased-correctly.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([uzasadnienie](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122 deklaracje](ca5122.md)

## <a name="see-also"></a>Zobacz także

- [Reguły Microsoft. CodeAnalysis. FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
