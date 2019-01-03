---
title: Rozszerzone wytyczne dotyczące reguł projektowania dla zarządzanego kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d30acba85a2980aef51e5f1eab93ef6d53a4199c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988027"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Rozszerzone wytyczne dotyczące reguł projektowania dla zarządzanego kodu
Reguły wskazówek dotyczących projektowania firmy Microsoft rozszerzony zestaw reguł rozszerza reguły wskazówek dotyczących podstawowy projekt, aby zmaksymalizować użytecznością i utrzymaniem problemy, które są zgłaszane. Dodatkowy nacisk jest kładziony na wskazówki dotyczące nazewnictwa. Należy rozważyć dołączenie tego zestawu, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najwyższych standardów tworzenia kodu, która jest łatwa w obsłudze reguł.

 Rozszerzone reguły wskazówek dotyczących projektowania obejmuje wszystkie podstawowe reguły wskazówek dotyczących projektowania firmy Microsoft. Podstawowe reguły wskazówek dotyczących projektowania obejmuje wszystkie reguły Zalecana minimalna firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zestaw reguł podstawowych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) i [zarządzany zalecany zestaw reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 W poniższej tabeli opisano wszystkie reguły w zestawie reguł rozszerzone reguły wskazówek dotyczących projektowania się do firmy Microsoft.

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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Nie deklaruj składowych statycznych w typach ogólnych|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Nie ujawniaj list ogólnych|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Użyj wystąpień obsługi zdarzeń generycznych|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Metody ogólne powinny podawać parametr typu|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Unikaj nadużywania parametrów na typach generycznych|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Nie zagnieżdżaj typów ogólnych w sygnaturach składowych|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Typy wyliczeniowe powinny mieć wartości zerowej|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Kolekcje powinny implementować interfejs ogólny|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Należy rozważyć przekazywanie typów bazowych jako parametrów|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Typy abstrakcyjne nie powinny mieć konstruktorów|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Oznacz zestawy atrybutem CLSCompliant|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Oznacz zestawy atrybutem ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Oznacz atrybuty atrybutem Attributeusage|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Zdefiniuj metody dostępu dla argumentów atrybutu|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Indeksatory nie powinny być wielowymiarowe|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Korzystanie z właściwości, gdzie jest to odpowiednie|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Zastąp powtarzające się argumenty tablicą params|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Nie można używać parametrów domyślnych|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Oznacz Typy wyliczeniowe atrybutem Flags|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Magazyn typu wyliczeniowego powinien być typu Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Używać zdarzeń, gdzie jest to odpowiednie|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Nie przechwytuj wyjątków typów ogólnych|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Zaimplementuj standardowe konstruktory wyjątku|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Typy zagnieżdżone nie powinny być widoczne|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Implementacje interfejsu ICollection mają silnie typizowane składowe|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Przesłaniaj metody porównywalnych typów|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Moduły wyliczające powinny być silnie typizowane|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listy są silnie typizowane|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Określ komunikat ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Użyj argumentu integral lub string dla indeksatorów|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Właściwości nie powinny być tylko do zapisu|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Nie przeciążaj operatora równości w typach referencyjnych|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Nie deklaruj chronionych elementów członkowskich w typach zapieczętowanych|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Nie deklaruj wirtualnych składowych w typach zapieczętowanych|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Deklaruj typy w przestrzeniach nazw|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Nie deklaruj widocznych pól wystąpienia|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Statyczne typy przechowujące powinny być zapieczętowane|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Statyczne typy przechowujące nie powinny mieć konstruktorów|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Parametry identyfikatora URI nie powinny być ciągami|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Identyfikator URI zwracanych wartości nie powinny być ciągami|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Właściwości identyfikatora URI nie powinny być ciągami|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Typy nie powinny rozszerzać niektórych typów podstawowych|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Składowe nie powinny ujawniać niektórych typów konkretnych|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Wyjątki powinny być publiczne|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Nazwy zmiennych nie powinny odpowiadać nazwom pól|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Unikaj nadmiernej złożoności|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identyfikatory powinny różnić się przez więcej niż wielkością liter|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Identyfikatory nie powinny odpowiadać słowom|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Przejrzyj nieużywane parametry|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Usuń nieużywane zmienne lokalne|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Unikaj zbyt wielu zmiennych lokalnych|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inicjowanie pola statyczne typu referencyjnego śródwierszowo|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Unikaj niewywołanego kodu prywatnego|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Unikaj klas wewnętrznych bez wystąpień|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Unikaj niezapieczętowanych atrybutów|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Preferuj Tablice nieregularne wielowymiarowych|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Przesłoń metodę equals i operator równości dla typów wartości|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Właściwości nie powinny zwracać tablic|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Oznaczaj składowe jako statyczne|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Unikaj nieużywanych pól prywatnych|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Nie wywołuj zastrzeżonych typów wyjątku|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Użyj zarządzanych odpowiedników funkcji Win32 API|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Poprawne wystąpienia wyjątków argumentów|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Pola niebędące stałymi nie powinny być widoczne|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Nie oznaczaj wyliczeń za pomocą FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Nie zgłaszaj wyjątków w klauzulach wyjątków|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Elementy Członkowskie powinny różnić się od tylko zwracanym typem|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Przesłoń metodę equals, przeciążając operator equals|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operator overloads ma nazwanych zastępców|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Użyj parametrów dla argumentów zmiennych|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Przekazuj obiekty System.Uri zamiast ciągów|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Unikaj przestrzeni nazw z kilkoma typami|
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Unikaj parametrów out|
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Unikaj pustych interfejsów|
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Nie przekazuj typów przez odwołanie|
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Waliduj argumenty metod publicznych|
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Unikaj nadmiernego dziedziczenia|
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Przegląd mylących nazw pól|
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Unikaj kodu trudnego w utrzymaniu|
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Unikaj nadmiernego sprzężenia klas|
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Nie nadawaj wartościom wyliczenia nazwy "Reserved"|
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter|
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Wyrazy złożone powinny mieć prawidłową wielkość liter|
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Ciągi zasobów, które powinny być zapisane poprawnie|
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Identyfikatory powinny być zapisane poprawnie|
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Identyfikatory nie powinny zawierać podkreśleń|
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Identyfikatory powinny mieć prawidłową wielkość liter|
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Identyfikatory powinny mieć poprawny sufiks|
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Identyfikatory nie powinny mieć niepoprawnego sufiksu|
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Nie poprzedzaj wartości wyliczenia nazwą typu|
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Zdarzenia nie powinny mieć prefiksu before ani after|
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Typy wyliczeniowe flag powinny mieć nazwy w liczbie mnogiej|
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Identyfikatory powinny mieć poprawny prefiks|
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Tylko wyliczenia FlagsAttribute powinny mieć nazwy w liczbie mnogiej|
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Nazwy parametrów nie powinny odpowiadać nazwom elementu członkowskiego|
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Identyfikatory nie powinny zawierać nazw typów|
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Nazwy właściwości nie powinny odpowiadać metody get|
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Identyfikatory nie powinny mieć niepoprawnego prefiksu|
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Nazwy typów nie powinny odpowiadać nazwom|
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Nazwy parametrów powinny pasować do deklaracji podstawowej|
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Używaj preferowanych terminów|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Literały powinny być zapisane poprawnie|