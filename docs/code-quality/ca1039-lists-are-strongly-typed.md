---
title: 'CA1039: Listy są silnie typizowane'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b1e8134eb89e4ae78ec0ad6f07fd7406215185
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922841"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listy są silnie typizowane

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ publiczny lub chroniony implementuje <xref:System.Collections.IList?displayProperty=fullName> , ale nie zapewnia metody silnie wpisanej dla co najmniej jednego z następujących elementów:

- Element IList. Item

- IList. Add

- IList. Contains

- IList.IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Opis reguły

Ta reguła wymaga <xref:System.Collections.IList> implementacji, aby zapewnić składowe o jednoznacznie określonym <xref:System.Object?displayProperty=fullName> typie, tak aby użytkownicy nie musieli rzutować argumentów na typ, gdy korzystają z funkcji dostarczonych przez interfejs. <xref:System.Collections.IList> Interfejs jest implementowany przez kolekcje obiektów, do których można uzyskać dostęp za pomocą indeksu. Ta reguła zakłada, że typ, który <xref:System.Collections.IList> implementuje zarządza kolekcją wystąpień typu, który jest silniejszy niż. <xref:System.Object>

<xref:System.Collections.IList>implementuje interfejsy <xref:System.Collections.IEnumerable?displayProperty=fullName>i. <xref:System.Collections.ICollection?displayProperty=fullName> W przypadku zaimplementowania <xref:System.Collections.IList>programu należy dostarczyć wymagane elementy członkowskie o jednoznacznie <xref:System.Collections.ICollection>określonym typie dla. Jeśli obiekty w kolekcji <xref:System.ValueType?displayProperty=fullName>są rozbudowane, należy zapewnić jednoznacznie wpisany <xref:System.Collections.IEnumerable.GetEnumerator%2A> element członkowski, aby uniknąć spadku wydajności, który jest spowodowany opakowaniem; nie jest to wymagane, gdy obiekty kolekcji są typu referencyjnego.

Aby zachować zgodność z tą regułą, należy zaimplementować elementy członkowskie interfejsu jawnie przy użyciu nazw w postaci InterfaceName. InterfaceMemberName, takich <xref:System.Collections.IList.Add%2A>jak. Jawne elementy członkowskie interfejsu używają typów danych zadeklarowanych przez interfejs. Zaimplementuj silnie wpisane elementy członkowskie przy użyciu nazwy składowej interfejsu, `Add`takiej jak. Zadeklaruj elementy członkowskie z jednoznacznie określonymi typami jako publiczne i zadeklaruj parametry i zwróć wartości jako typ silny, który jest zarządzany przez kolekcję. Silne typy zastępują słabsze typy, takie jak <xref:System.Object> i <xref:System.Array> , które są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, jawnie Zaimplementuj <xref:System.Collections.IList> członków i podaj silnie wpisane alternatywy dla elementów członkowskich, które zostały zanotowane wcześniej. W przypadku kodu, który poprawnie <xref:System.Collections.IList> implementuje interfejs i udostępnia wymagane elementy o jednoznacznie określonym typie, zapoznaj się z poniższym przykładem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomijaj ostrzeżenie z tej reguły podczas implementowania nowej kolekcji opartej na obiektach, takiej jak lista połączona, gdzie typy, które poszerzają nową kolekcję, określają typ silny. Te typy powinny być zgodne z tą regułą i uwidaczniają silnie wpisaną składowe.

## <a name="example"></a>Przykład
W poniższym przykładzie typ rozciąga `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName>się, ponieważ wszystkie kolekcje o jednoznacznie określonym typie powinny. <xref:System.Collections.CollectionBase>zapewnia jawną implementację <xref:System.Collections.IList> interfejsu. W związku z tym należy dostarczyć tylko elementy o jednoznacznie określonym <xref:System.Collections.IList> typie <xref:System.Collections.ICollection>dla i.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1035: Implementacje ICollection mają jednoznacznie wpisane elementy członkowskie](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038 Moduły wyliczające powinny być silnie wpisane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>