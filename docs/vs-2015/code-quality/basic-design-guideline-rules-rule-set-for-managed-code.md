---
title: Podstawowych reguł wytycznych projektowych, ustaw dla kodu zarządzanego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 62b6a6e5415f79886246075363a4663efecc246e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535843"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Podstawowe reguły zasad projektowania dla zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć reguły podstawowe reguły wskazówek dotyczących projektowania firmy Microsoft, równa się koncentrować na łatwiejsze do zrozumienia i użycia kodu. Powinien być dołączany do tej reguły, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymuszać najlepsze rozwiązania dla kodu, który jest łatwa w obsłudze.  
  
 Podstawowe reguły wskazówek dotyczących projektowania obejmują wszystkie reguły w zestawie reguł reguły Recommeded Minimum firmy Microsoft. Aby uzyskać listę minimalne reguły, zobacz [zarządzany zalecany zestaw reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 W poniższej tabeli opisano wszystkie reguły w zestawie reguł podstawowe reguły wskazówek dotyczących projektowania firmy Microsoft.  
  
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Nie deklaruj statycznych składowych na typach ogólnych|  
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Nie uwidaczniaj list ogólnych|  
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Użyj ogólnych wystąpień procedury obsługi zdarzeń|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Metody ogólne powinny podawać parametr typu|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Unikaj nadmiernego użycia parametrów w typach ogólnych|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Nie zagnieżdżaj typów ogólnych w podpisach składowych|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Używaj typów ogólnych tam, gdzie to odpowiednie|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Typy wyliczeniowe powinny mieć wartość zero|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Kolekcje powinny implementować interfejs ogólny|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Rozważ przekazywanie typów podstawowych jako parametrów|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Typy abstrakcyjne nie powinny mieć konstruktorów|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Oznacz zestawy atrybutem CLSCompliant|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Oznacz zestawy atrybutem ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Oznacz atrybuty atrybutem AttributeUsage|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Zdefiniuj metody dostępu dla argumentów atrybutów|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indeksatory nie powinny być wielowymiarowe|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Używaj właściwości, o ile to możliwe|  
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Zastąp powtarzalne argumenty tablicą params|  
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Nie należy używać parametrów domyślnych|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Oznacz typy wyliczeniowe atrybutem Flags|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Magazyn typu wyliczeniowego powinien być typu Int32|  
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Używaj zdarzeń, o ile to możliwe|  
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Nie przechwytuj typów wyjątków ogólnych|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Zaimplementuj standardowe konstruktory wyjątków|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Typy zagnieżdżone nie powinny być widoczne|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Implementacje interfejsu ICollection mają silnie typizowane składowe|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Przesłaniaj metody porównywalnych typów|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Moduły wyliczające powinny być silnie typizowane|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listy są silnie typizowane|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Udostępnij komunikat ObsoleteAttribute|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Właściwości nie powinny być tylko do zapisu|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Nie przeciążaj operatora równości w typach referencyjnych|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Nie deklaruj chronionych składowych w typach zapieczętowanych|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Nie deklaruj wirtualnych składowych w typach zapieczętowanych|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Deklaruj typy w przestrzeniach nazw|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Nie deklaruj widocznych pól w wystąpieniach|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statyczne typy przechowujące powinny być zapieczętowane|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statyczne typy przechowujące nie powinny mieć konstruktorów|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identyfikatora URI nie powinny być ciągami|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Wartości zwracane identyfikatora URI nie powinny być ciągami|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Właściwości identyfikatora URI nie powinny być ciągami|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Identyfikator URI typu string przeciąża wywołanie przeciążane przez typ System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typy nie powinny rozszerzać niektórych typów podstawowych|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Składowe nie powinny ujawniać niektórych typów konkretnych|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Wyjątki powinny być publiczne|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Nazwy zmiennych nie powinny być zgodne z nazwami pól|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Unikaj nadmiernej złożoności|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identyfikatory powinny różnić się nie tylko wielkością liter|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Identyfikatory nie powinny być zgodne ze słowami kluczowymi|  
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Dokonaj przeglądu nieużywanych parametrów|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Usuwaj nieużywane zmienne lokalne|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Unikaj zbyt wielu zmiennych lokalnych|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicjuj pola statyczne typu referencyjnego śródwierszowo|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Unikaj niewywołanego kodu prywatnego|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Unikaj klas wewnętrznych bez wystąpień|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Unikaj niezapieczętowanych atrybutów|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Wybieraj tablice nieregularne zamiast wielowymiarowych|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Przesłaniaj metodę equals i operator równości w typach wartości|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Właściwości nie powinny zwracać tablic|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Oznaczaj składowe jako statyczne|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Unikaj nieużywanych pól prywatnych|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Nie zgłaszaj wyjątków o zastrzeżonych typach|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Użyj zarządzanych odpowiedników funkcji API Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Poprawnie twórz wystąpienia wyjątków argumentów|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola niebędące stałymi nie powinny być widoczne|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nie oznaczaj typów wyliczeniowych atrybutem Flags|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Nie zgłaszaj wyjątków w klauzulach wyjątków|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory powinny być chronione|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie obniżaj dziedziczonej widoczności składowych|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Składowe powinny różnić się nie tylko zwracanym typem|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Przeciążenia operatorów mają nazwane elementy alternatywne|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatory powinny mieć symetryczne przeciążenia|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwości kolekcji powinny być tylko do odczytu|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Użyj elementu params dla argumentów zmiennych|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Przekazuj obiekty System.Uri zamiast ciągów|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
