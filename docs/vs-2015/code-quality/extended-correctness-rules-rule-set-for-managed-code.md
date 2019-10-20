---
title: Rozszerzony zestaw reguł poprawności dla kodu zarządzanego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bef208dbcb4c1017840602d198b5099267b25a99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667638"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Rozszerzony zestaw reguł poprawności dla zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw reguł poprawności rozszerzonej firmy Microsoft maksymalizuje błędy użycia logiki i struktury, które są raportowane przez analizę kodu. Dodatkowy nacisk jest umieszczany w określonych scenariuszach, takich jak współdziałanie COM i aplikacje mobilne. Należy rozważyć uwzględnienie tego zestawu reguł, jeśli jeden z tych scenariuszy ma zastosowanie do Twojego projektu lub aby znaleźć dodatkowe problemy w projekcie.

 Zestaw reguł poprawnego rozszerzenia Microsoft Extended zawiera reguły, które znajdują się w zestawie reguł poprawności programu Microsoft Basic. Podstawowe reguły poprawności obejmują reguły, które znajdują się w minimalnym zalecanym zestawie reguł firmy Microsoft. Aby uzyskać więcej informacji, zobacz [podstawowe reguły poprawności zestaw reguł dla kodu zarządzanego](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) i [zarządzane zalecane reguły zestawu reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 W poniższej tabeli opisano wszystkie reguły w zestawie reguł poprawnych rozszerzonych firmy Microsoft.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Nie ukrywaj metod klasy bazowej|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Zaimplementuj konstruktory serializacji|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Poprawnie implementuj metody serializacji|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Poprawnie testuj nie-liczby (NaN)|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Nie ignoruj wyników metod|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Poprawnie wywołaj metodę GC.SuppressFinalize|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Właściwości nie powinny zwracać tablic|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Używaj tylko interfejsu API platformy docelowej|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Usuń wywołania funkcji GC.KeepAlive|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Pola tablicy nie powinny być tylko do odczytu|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Zabezpiecz asercje|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpiecz konstruktory serializacji|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Konstruktory statyczne powinny być prywatne|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Użyj zarządzanych odpowiedników funkcji API Win32|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Metody Dispose powinny wywoływać metodę Dispose klasy bazowej|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Składowe powinny różnić się nie tylko zwracanym typem|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Zaimplementuj standardowe konstruktory wyjątków|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Wartości zwracane identyfikatora URI nie powinny być ciągami|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Unikaj przeciążeń w interfejsach widocznych dla modelu COM|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Unikaj statycznych składowych w typach widocznych dla modelu COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Nie używaj wartości AutoDual elementu ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Typy widoczne dla modelu COM powinny mieć możliwość utworzenia|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metody rejestracji modelu COM nie powinny być widoczne|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Oznacz interfejsy ComSource atrybutem IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Unikaj niepublicznych pól w typach wartości widocznych w modelu COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Oznacz argumenty typu boolean elementu P/Invoke argumentem MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nie używaj priorytetu procesu o wartości Bezczynny|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Unikaj wywoływania problematycznych metod|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Nie traktuj włókien jak wątków|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Adnotacje przezroczystości składowych nie powinny powodować konfliktu|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Metody przezroczyste nie powinny używać żądań zabezpieczeń|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Pisownia literałów powinna być poprawna|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nie oznaczaj typów wyliczeniowych atrybutem Flags|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Nie zgłaszaj wyjątków w klauzulach wyjątków|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Przeciążenia operatorów mają nazwane elementy alternatywne|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Nie publikuj zasobów w formatach z wersji wstępnych|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Użyj elementu params dla argumentów zmiennych|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Operacje nie powinny powodować przepełnienia|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Analiza literałów ciągów atrybutów powinna przebiegać poprawnie|
