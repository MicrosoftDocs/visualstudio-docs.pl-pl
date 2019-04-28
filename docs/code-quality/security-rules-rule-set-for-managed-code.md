---
title: Zestaw reguł zabezpieczeń dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 45c51a6c5496686ef84b17341c97f00680a80bdd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825295"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Zestaw reguł zabezpieczeń dla zarządzanego kodu
Powinien zawierać regułę reguły zabezpieczeń firmy Microsoft, aby zmaksymalizować liczbę potencjalnych problemów z zabezpieczeniami, które są zgłaszane.

|Reguła|Opis|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Przejrzyj zabezpieczenia imperatywne|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Pola tablicy nie powinny być tylko do odczytu|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Zabezpiecz asercje|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Przejrzyj przypadki użycia metod Deny i PermitOnly|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Przejrzyj widoczne procedury obsługi zdarzeń|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Zabezpiecz konstruktory serializacji|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Konstruktory statyczne powinny być prywatne|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Adnotacje przezroczystości składowych nie powinny powodować konfliktu|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Metody przezroczyste nie powinny używać żądań zabezpieczeń|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Zestawy powinny mieć prawidłowe silne nazwy|
|[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)|Nie używaj niezabezpieczonego deserializatora BinaryFormatter|
|[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)|Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder|
|[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)|Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize|
|[CA3001](../code-quality/ca3001-review-code-for-sql-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL|
|[CA3002](../code-quality/ca3002-review-code-for-xss-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami|
|[CA3003](../code-quality/ca3003-review-code-for-file-path-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku|
|[CA3004](../code-quality/ca3004-review-code-for-information-disclosure-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji|
|[CA3005](../code-quality/ca3005-review-code-for-ldap-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP|
|[CA3006](../code-quality/ca3006-review-code-for-process-command-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu|
|[CA3007](../code-quality/ca3007-review-code-for-open-redirect-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania|
|[CA3008](../code-quality/ca3008-review-code-for-xpath-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath|
|[CA3009](../code-quality/ca3009-review-code-for-xml-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML|
|[CA3010](../code-quality/ca3010-review-code-for-xaml-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML|
|[CA3011](../code-quality/ca3011-review-code-for-dll-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL|
|[CA3012](../code-quality/ca3012-review-code-for-regex-injection-vulnerabilities.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego|
