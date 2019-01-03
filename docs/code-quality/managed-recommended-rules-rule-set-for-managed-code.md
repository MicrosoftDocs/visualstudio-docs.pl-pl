---
title: Zarządzane zalecane Reguły dla zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 257cd658d798f620a5dd3faf47edea7b1454e7bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987141"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Zarządzane zalecane Reguły dla zarządzanego kodu
Można użyć programu Microsoft zarządzany zalecany zestaw reguł skoncentrować się na najważniejszych problemów w kodzie zarządzanym, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne istotne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, które posiadają pola usuwalne powinny być usuwalne|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Poprawnie Zadeklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Oznacz zestawy atrybutem Assemblyversion|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody interfejsu powinny być wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, które posiadają natywne zasoby powinny być usuwalne|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Przenieś P/Invokes do klasy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Nie ukrywaj metod klasy bazowej|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Powinny istnieć punkty wejścia P/Invoke|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes nie powinny być widoczne|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy automatycznego układu nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wywołaj metodę GetLastError natychmiast po P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody rejestracji modelu COM powinny być dopasowane|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Poprawnie Zadeklaruj P/Invokes|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklaracje P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Należy określić marshaling dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Typy zabezpieczone nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy bazowe APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami linkdemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Zastąpienie konsolidacji powinny być identyczne z bazowym|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Linkdemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne dla zabezpieczeń nie mogą brać udziału w równoważeniu typu|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegatów należy powiązać z metodami ze spójną jawnością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Metody przezroczyste muszą zawierać tylko weryfikowalne IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Przezroczysty kod nie może odwoływać się elementów krytycznych dla zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak krytyczne jak ich typy podstawowe i interfejsy|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Metody przezroczyste nie mogą używać zabezpieczeń asercji|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Ponownie, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nie Likwiduj obiektów wiele razy|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Typu wartości Inicjuj pola statyczne bezpośrednio|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nie oznaczaj usługowych składników atrybutem WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola możliwe do rozporządzania należy rozporządzać|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nie wywoływać nadpisywalnych metod w konstruktorach|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typy możliwe do rozporządzania powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizatory powinny wywoływać finalizatory klasy bazowej|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Zaimplementuj konstruktory serializacji|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Punkty wejścia znacznik Windows Forms za pomocą atrybutu STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Oznacz wszystkie pola nieprzeznaczone do|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Wywołuj metody klasy bazowej typu ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Poprawnie Implementuj metody serializacji|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Poprawnie Testuj NaN|