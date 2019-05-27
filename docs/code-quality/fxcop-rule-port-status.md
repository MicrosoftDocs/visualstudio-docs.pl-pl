---
title: Stan portu reguł programu FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0d78e7dcd7dfd203a15510037b277b8c2633805e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038669"
---
# <a name="fxcop-rule-port-status"></a>Stan portu reguł programu FxCop

Jeśli wcześniej używano statycznej analizy kodu w poprzedniej wersji programu Visual Studio, możesz się zastanawiać, której te zasady są dostępne w bieżącej implementacji jako [analizatory FxCop analizujące kod](install-fxcop-analyzers.md). Ta strona zawiera listę reguł, które są przenoszone, a także tych, które nie zostały wydajnej i tego, czy istnieją plany do portu je.

## <a name="ported-rules"></a>Przenieść reguły

[Stronę z dokumentacją dotyczącą wygenerowany automatycznie](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) w analizatorów roslyn repozytorium zawiera najbardziej aktualną listę reguł, które wydajnej analizatory FxCop analizujące kod. Ta strona ma również dodatkowe informacje, takie jak czy zasada jest domyślnie włączona, a jeśli ma skojarzoną *poprawki kodu*. ([Poprawki kodu](../ide/quick-actions.md) dostępnych poprawek jednym kliknięciem w menu ikona żarówki z funkcją w programie Visual Studio.)

W dniu na tej stronie reguły wydajnej do listy programu FxCop [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) obejmuje:

Identyfikator reguły | Tytuł
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Nie deklaruj statycznych składowych na typach ogólnych
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji
[CA1003](ca1003-use-generic-event-handler-instances.md) | Użyj ogólnych wystąpień procedury obsługi zdarzeń
[CA1008](ca1008-enums-should-have-zero-value.md) | Typy wyliczeniowe powinny mieć wartość zero
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Kolekcje powinny implementować interfejs ogólny
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Typy abstrakcyjne nie powinny mieć konstruktorów
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Oznacz zestawy atrybutem CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Oznacz zestawy atrybutem wersji zestawu
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Oznacz zestawy atrybutem ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Oznacz atrybuty atrybutem AttributeUsage
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Zdefiniuj metody dostępu dla argumentów atrybutów
[CA1024](ca1024-use-properties-where-appropriate.md) | Używaj właściwości, o ile to możliwe
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Oznacz typy wyliczeniowe atrybutem Flags
[CA1028](ca1028-enum-storage-should-be-int32.md) | Magazyn typu wyliczeniowego powinien być typu Int32
[CA1030](ca1030-use-events-where-appropriate.md) | Używaj zdarzeń, o ile to możliwe
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Nie przechwytuj typów wyjątków ogólnych
[CA1032](ca1032-implement-standard-exception-constructors.md) | Zaimplementuj standardowe konstruktory wyjątków
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Metody interfejsu powinny móc zostać wywołane przez typy podrzędne
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Typy zagnieżdżone nie powinny być widoczne
[CA1036](ca1036-override-methods-on-comparable-types.md) | Przesłaniaj metody porównywalnych typów
[CA1040](ca1040-avoid-empty-interfaces.md) | Unikaj pustych interfejsów
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Udostępnij komunikat ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Całkowite użycie lub argumentu ciągu dla indeksatorów
[CA1044](ca1044-properties-should-not-be-write-only.md) | Właściwości nie powinny być tylko do zapisu
[CA1050](ca1050-declare-types-in-namespaces.md) | Deklaruj typy w przestrzeniach nazw
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Nie deklaruj widocznych pól w wystąpieniach
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Statyczne typy przechowujące powinny być statyczne lub NotInheritable (patrz uwaga pod tą tabelą)
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Statyczne typy przechowujące nie powinny mieć konstruktorów (patrz uwaga pod tą tabelą)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Parametry identyfikatora URI nie powinny być ciągami
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Identyfikator URI zwracanych wartości nie powinny być ciągami
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Właściwości identyfikatora URI nie powinny być ciągami
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Typy nie powinny rozszerzać niektórych typów podstawowych
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Przenieś o do metod macierzystych klas
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Nie ukrywaj metod klasy bazowej
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Waliduj argumenty metod publicznych
[CA1063](ca1063-implement-idisposable-correctly.md) | Poprawnie zaimplementuj interfejs IDisposable
[CA1064](ca1064-exceptions-should-be-public.md) | Wyjątki powinny być publiczne
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach
CA1066 | Typ {0} powinny implementować IEquatable<T> ponieważ zastępuje ona równa się
CA1067 | Zastąp Object.Equals(object) podczas implementowania IEquatable<T>
CA1068 | Token anulowania parametry muszą pochodzić ostatni
CA1200 | Należy unikać cref tagi z prefiksem
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Nie przekazuj literałów jako zlokalizowanych parametrów
[CA1304](ca1304-specify-cultureinfo.md) | Określ argument CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Określ argument IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Określ argument StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Normalizuj ciągi do postaci zapisanej wielkimi literami
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Użyj porównania porządkowego ciągu
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Elementy P/Invoke nie powinny być widoczne
[CA1501](ca1501-avoid-excessive-inheritance.md) | Unikaj nadmiernego dziedziczenia
[CA1502](ca1502-avoid-excessive-complexity.md) | Unikaj nadmiernej złożoności
[CA1505](ca1505-avoid-unmaintainable-code.md) | Unikaj kodu trudnego w utrzymaniu
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Unikaj nadmiernego sprzężenia klas
[CA1507](ca1507.md) | Umożliwia nameof express nazwy symboli
CA1508 | Unikaj dead warunkowego kodu
CA1509 | Nieprawidłowy wpis w pliku specyfikacji reguły metryk kodu
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
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Nazwy typów nie powinny odpowiadać nazwom
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Nazwy parametrów powinny być zgodne z deklaracją podstawową
[CA1801](ca1801-review-unused-parameters.md) | Dokonaj przeglądu nieużywanych parametrów
[CA1802](ca1802-use-literals-where-appropriate.md) | Używaj literałów wszędzie, gdzie jest to odpowiednie
[CA1806](ca1806-do-not-ignore-method-results.md) | Nie ignoruj wyników metod
[CA1810](ca1810-initialize-reference-type-static-fields-inline.md) | Inicjuj pola statyczne typu referencyjnego śródwierszowo
[CA1812](ca1812-avoid-uninstantiated-internal-classes.md) | Unikaj klas wewnętrznych bez wystąpień
[CA1813](ca1813-avoid-unsealed-attributes.md) | Unikaj niezapieczętowanych atrybutów
[CA1814](ca1814-prefer-jagged-arrays-over-multidimensional.md) | Wybieraj tablice nieregularne zamiast wielowymiarowych
[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md) | Przesłaniaj metodę equals i operator równości w typach wartości
[CA1816](ca1816-call-gc-suppressfinalize-correctly.md) | Metody Dispose powinny wywoływać SuppressFinalize
[CA1819](ca1819-properties-should-not-return-arrays.md) | Właściwości nie powinny zwracać tablic
[CA1820](ca1820-test-for-empty-strings-using-string-length.md) | Testuj obecność pustych ciągów przy użyciu długości ciągu
[CA1821](ca1821-remove-empty-finalizers.md) | Usuwaj puste finalizatory
[CA1822](ca1822-mark-members-as-static.md) | Oznaczaj składowe jako statyczne
[CA1823](ca1823-avoid-unused-private-fields.md) | Unikaj nieużywanych pól prywatnych
[CA1824](ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute
CA1825 | Należy unikać alokacje tablicę o zerowej długości.
CA1826 | Nie należy używać metod Wyliczalny w kolekcjach można indeksować. Zamiast tego użyć kolekcji bezpośrednio
[CA2000](ca2000-dispose-objects-before-losing-scope.md) | Likwiduj obiekty przed utratą zakresu
[CA2002](ca2002-do-not-lock-on-objects-with-weak-identity.md) | Nie blokuj obiektów o słabej tożsamości
[CA2007](ca2007-do-not-directly-await-task.md) | Należy wziąć pod uwagę podczas wywoływania ConfigureAwait w oczekiwane zadanie
CA2008 | Nie należy tworzyć zadań bez przekazywania TaskScheduler
CA2009 | Nie wywołuj ToImmutableCollection wartość ImmutableCollection
CA2010 | Zawsze będą mogli skorzystać wartości zwracanej przez metody oznaczone PreserveSigAttribute
[CA2100](ca2100-review-sql-queries-for-security-vulnerabilities.md) | Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach
[CA2101](ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Określ kierowanie dla argumentów ciągu P/Invoke
[CA2119](ca2119-seal-methods-that-satisfy-private-interfaces.md) | Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[CA2153](ca2153-avoid-handling-corrupted-state-exceptions.md) | Nie przechwytuj uszkodzonych wyjątków stanu
[CA2200](ca2200-rethrow-to-preserve-stack-details.md) | Zgłoś ponownie, aby zachować szczegóły stosu.
[CA2201](ca2201-do-not-raise-reserved-exception-types.md) | Nie zgłaszaj wyjątków o zastrzeżonych typach
[CA2207](ca2207-initialize-value-type-static-fields-inline.md) | Pola statyczne typu wartości inicjuj bezpośrednio
[CA2208](ca2208-instantiate-argument-exceptions-correctly.md) | Poprawnie twórz wystąpienia wyjątków argumentów
[CA2211](ca2211-non-constant-fields-should-not-be-visible.md) | Pola niebędące stałymi nie powinny być widoczne
[CA2213](ca2213-disposable-fields-should-be-disposed.md) | Pola możliwe do likwidacji należy likwidować
[CA2214](ca2214-do-not-call-overridable-methods-in-constructors.md) | Nie wywołuj w konstruktorach metod, które można przesłaniać
[CA2216](ca2216-disposable-types-should-declare-finalizer.md) | Typy możliwe do likwidacji powinny deklarować finalizator
[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md) | Nie oznaczaj typów wyliczeniowych atrybutem Flags
[CA2218](ca2218-override-gethashcode-on-overriding-equals.md) | Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals
[CA2219](ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Nie zgłaszaj wyjątków w klauzulach finally
[CA2224](ca2224-override-equals-on-overloading-operator-equals.md) | Przesłaniaj metodę Equals w przypadku przeciążania operacji operatora równa się
[CA2225](ca2225-operator-overloads-have-named-alternates.md) | Przeciążenia operatorów mają nazwane elementy alternatywne
[CA2226](ca2226-operators-should-have-symmetrical-overloads.md) | Operatory powinny mieć symetryczne przeciążenia
[CA2227](ca2227-collection-properties-should-be-read-only.md) | Właściwości kolekcji powinny być tylko do odczytu
[CA2229](ca2229-implement-serialization-constructors.md) | Zaimplementuj konstruktory serializacji
[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Dokonaj przeciążenia operatora równości w przypadku przesłaniania wartości typu równa się
[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) | Przekaż system obiekty uri zamiast ciągów
[CA2235](ca2235-mark-all-non-serializable-fields.md) | Oznacz wszystkie pola nieprzeznaczone do serializacji
[CA2237](ca2237-mark-iserializable-types-with-serializableattribute.md) | Oznacz typy ISerializable atrybutem możliwy do serializacji
[CA2241](ca2241-provide-correct-arguments-to-formatting-methods.md) | Podaj poprawne argumenty metod formatowania
[CA2242](ca2242-test-for-nan-correctly.md) | Poprawnie testuj nie-liczby (NaN)
[CA2243](ca2243-attribute-string-literals-should-parse-correctly.md) | Analiza literałów ciągów atrybutów powinna przebiegać poprawnie
CA2244 | Nie zduplikowane inicjalizacje indeksowanego elementu
[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md) | Nie używaj niezabezpieczonego deserializatora BinaryFormatter
[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) | Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder
[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) | Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize
[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md) | Nie używaj niezabezpieczonego deserializatora LosFormatter
[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md) | Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer
[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) | Nie wykonuj deserializacji bez uprzedniego ustawienia właściwości NetDataContractSerializer.Binder
[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) | Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją
[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md) | Nie używaj niezabezpieczonego deserializatora ObjectStateFormatter
[CA2321](ca2321.md) | Nie wykonuj deserializacji za pomocą obiektu JavaScriptSerializer zainicjowanego przy użyciu parametru SimpleTypeResolver
[CA2322](ca2322.md) | Upewnij się, że obiekt JavaScriptSerializer nie został zainicjowany przy użyciu parametru SimpleTypeResolver przed deserializacją
[CA3001](ca3001-review-code-for-sql-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL
[CA3002](ca3002-review-code-for-xss-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami
[CA3003](ca3003-review-code-for-file-path-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku
[CA3004](ca3004-review-code-for-information-disclosure-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji
[CA3005](ca3005-review-code-for-ldap-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP
[CA3006](ca3006-review-code-for-process-command-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu
[CA3007](ca3007-review-code-for-open-redirect-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania
[CA3008](ca3008-review-code-for-xpath-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath
[CA3009](ca3009-review-code-for-xml-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML
[CA3010](ca3010-review-code-for-xaml-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML
[CA3011](ca3011-review-code-for-dll-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL
[CA3012](ca3012-review-code-for-regex-injection-vulnerabilities.md) | Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego
CA3061 | Nie należy dodawać schematu według adresu URL
[CA3075](ca3075-insecure-dtd-processing.md) | DTD niezabezpieczone przetwarzanie w formacie XML
[CA3076](ca3076-insecure-xslt-script-execution.md) | Niezabezpieczone przetwarzanie skryptu XSLT.
[CA3077](ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md) | Niezabezpieczone przetwarzanie w projekt interfejsu API, XmlDocument i klasy XmlTextReader
[CA3147](ca3147-mark-verb-handlers-with-validateantiforgerytoken.md) | Znacznik zlecenie obsługi za pomocą walidacji tokenu Antiforgery
[CA5350](ca5350-do-not-use-weak-cryptographic-algorithms.md) | Nie używaj słabych algorytmów kryptograficznych
[CA5351](ca5351-do-not-use-broken-cryptographic-algorithms.md) | Nie używaj uszkodzonych algorytmów kryptograficznych
CA5358 | Nie należy używać szyfrowania niebezpieczne tryby
CA5359 | Nie należy wyłączać sprawdzanie poprawności certyfikatu
CA5360 | Nie wywołuj metody niebezpiecznych w Rozszeregowaniu
CA5361 | Nie można wyłączyć SChannel stosowanie silnych usług kryptograficznych
CA5362 | Nie można znaleźć samodzielnie w klasie serializacji
CA5363 | Nie wyłączono weryfikację żądań
CA5364 | Nie należy używać protokołów zabezpieczeń przestarzałe
CA5365 | Nie należy wyłączać nagłówków HTTP, sprawdzanie
CA5366 | Element XmlReader na użytek odczytu zestaw danych Xml
CA5367 | Nie serializować typy z polami wskaźnika
CA5368 | Ustaw ViewStateUserKey dla klas pochodzących ze strony
CA5369 | Element XmlReader na użytek Deserialize
CA5370 | Sprawdzanie poprawności czytelnika na użytek XmlReader
CA5371 | Element XmlReader na użytek odczytu schematu
CA5372 | Element XmlReader na użytek obiektu XPathDocument
CA5373 | Nie należy używać funkcji przestarzałe wyprowadzania klucza
CA5374 | Nie należy używać klasy XslTransform
CA5375 | Nie używaj sygnatury dostępu współdzielonego konta
CA5376 | Użyj SharedAccessProtocol HttpsOnly
CA5377 | Użyj zasad dostępu na poziomie kontenera
CA5378 | Nie można wyłączyć ServicePointManagerSecurityProtocols
CA5379 | Nie należy używać algorytm funkcji słabe wyprowadzania klucza
CA9999 | Niezgodność wersji analizatora

> [!NOTE]
> CA1052 reguł i CA1053 z oryginalnego wdrożenia programu FxCop są łączone w jednej reguły, CA1052, w analizatory FxCop analizujące kod.

## <a name="unported-rules"></a>Reguły unported

Zestaw reguł, które nie zostały przeniesione do [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) składa się z reguł, które nie zostały jeszcze, ale nadal [mogą być przenoszone](#rules-that-may-be-ported)oraz te, które są przestarzałe i [nie będzie można przenieść](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Reguły, które mogą być przenoszone.

Następujące reguły analizy kodu statycznego FxCop nie została jeszcze zaimplementowana jako analizatorów, ale nadal może być. Może to być z powodów techniczne blokujące lub po prostu to reguły o niższym priorytecie. Aby uzyskać więcej informacji o stanie przenoszenia każdą regułę, kliknij link w **śledzenia problemu** kolumny.

Identyfikator reguły | Śledzenia problemu
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
[CA1804](ca1804-remove-unused-locals.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811-avoid-uncalled-private-code.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900-value-type-fields-should-be-portable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001-avoid-calling-problematic-methods.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004-remove-calls-to-gc-keepalive.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006-use-safehandle-to-encapsulate-native-resources.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109-review-visible-event-handlers.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204-literals-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205-use-managed-equivalents-of-win32-api.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212-do-not-mark-serviced-components-with-webmethod.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215-dispose-methods-should-call-base-class-dispose.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232-mark-windows-forms-entry-points-with-stathread.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236-call-base-class-methods-on-iserializable-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238-implement-serialization-methods-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239-provide-deserialization-methods-for-optional-fields.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240-implement-iserializable-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Przestarzałe reguły

Następujące reguły analizy kodu statycznego FxCop są przestarzałe i nie będzie można zaimplementować jako analizatorów. Aby uzyskać więcej informacji, możesz wyszukiwać według Identyfikatora reguły (na przykład **CA1009**) na [stronie problemów serwisu GitHub analizatorów roslyn](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

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
- [CA1703](ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1800](ca1800-do-not-cast-unnecessarily.md)
- [CA1809](ca1809-avoid-excessive-locals.md)
- [CA1901](ca1901-p-invoke-declarations-should-be-portable.md)
- [CA1903](ca1903-use-only-api-from-targeted-framework.md)
- [CA2003](ca2003-do-not-treat-fibers-as-threads.md)
- [CA2102](ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)
- [CA2103](ca2103-review-imperative-security.md)
- [CA2104](ca2104-do-not-declare-read-only-mutable-reference-types.md)
- [CA2105](ca2105-array-fields-should-not-be-read-only.md)
- [CA2106](ca2106-secure-asserts.md)
- [CA2107](ca2107-review-deny-and-permit-only-usage.md)
- [CA2108](ca2108-review-declarative-security-on-value-types.md)
- [CA2111](ca2111-pointers-should-not-be-visible.md)
- [CA2112](ca2112-secured-types-should-not-expose-fields.md)
- [CA2114](ca2114-method-security-should-be-a-superset-of-type.md)
- [CA2115](ca2115-call-gc-keepalive-when-using-native-resources.md)
- [CA2116](ca2116-aptca-methods-should-only-call-aptca-methods.md)
- [CA2117](ca2117-aptca-types-should-only-extend-aptca-base-types.md)
- [CA2118](ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)
- [CA2120](ca2120-secure-serialization-constructors.md)
- [CA2121](ca2121-static-constructors-should-be-private.md)
- [CA2122](ca2122-do-not-indirectly-expose-methods-with-link-demands.md)
- [CA2123](ca2123-override-link-demands-should-be-identical-to-base.md)
- [CA2124](ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)
- [CA2126](ca2126-type-link-demands-require-inheritance-demands.md)
- [CA2130](ca2130-security-critical-constants-should-be-transparent.md)
- [CA2131](ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)
- [CA2132](ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)
- [CA2133](ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)
- [CA2134](ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)
- [CA2135](ca2135-level-2-assemblies-should-not-contain-linkdemands.md)
- [CA2136](ca2136-members-should-not-have-conflicting-transparency-annotations.md)
- [CA2137](ca2137-transparent-methods-must-contain-only-verifiable-il.md)
- [CA2138](ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)
- [CA2139](ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)
- [CA2140](ca2140-transparent-code-must-not-reference-security-critical-items.md)
- [CA2141](ca2141-transparent-methods-must-not-satisfy-linkdemands.md)
- [CA2142](ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
- [CA2143](ca2143-transparent-methods-should-not-use-security-demands.md)
- [CA2144](ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)
- [CA2145](ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)
- [CA2146](ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)
- [CA2147](ca2147-transparent-methods-may-not-use-security-asserts.md)
- [CA2149](ca2149-transparent-methods-must-not-call-into-native-code.md)
- [CA2151](ca2151-fields-with-critical-types-should-be-security-critical.md)
- [CA2202](ca2202-do-not-dispose-objects-multiple-times.md)
- [CA2210](ca2210-assemblies-should-have-valid-strong-names.md)
- [CA2220](ca2220-finalizers-should-call-base-class-finalizer.md)
- [CA2221](ca2221-finalizers-should-be-protected.md)
- [CA2222](ca2222-do-not-decrease-inherited-member-visibility.md) ([uzasadnienie](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223-members-should-differ-by-more-than-return-type.md)
- [CA2228](ca2228-do-not-ship-unreleased-resource-formats.md)
- [CA2230](ca2230-use-params-for-variable-arguments.md)
- [CA2233](ca2233-operations-should-not-overflow.md)
- [CA5122](ca5122-p-invoke-declarations-should-not-be-safe-critical.md)

## <a name="see-also"></a>Zobacz także

- [Reguły Microsoft.CodeAnalysis.FxCopAnalyzers](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)