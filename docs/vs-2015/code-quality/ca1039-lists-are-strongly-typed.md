---
title: 'CA1039: listy są silnie wpisane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8845fb8bcd08f076ddc3c509a37948cf008e0623
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661799"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listy są silnie typizowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.IList?displayProperty=fullName>, ale nie zapewnia metody silnie wpisanej dla co najmniej jednego z następujących elementów:

- Element IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga implementacji <xref:System.Collections.IList>, aby zapewnić składowe o jednoznacznie określonym typie, tak aby użytkownicy nie musieli rzutować argumentów na typ <xref:System.Object?displayProperty=fullName>, gdy korzystają z funkcji dostarczonych przez interfejs. Interfejs <xref:System.Collections.IList> jest implementowany przez kolekcje obiektów, do których można uzyskać dostęp za pomocą indeksu. Ta reguła zakłada, że typ, który implementuje <xref:System.Collections.IList>, służy do zarządzania kolekcją wystąpień typu, które są silniejszymi niż <xref:System.Object>.

 <xref:System.Collections.IList> implementuje interfejsy <xref:System.Collections.ICollection?displayProperty=fullName> i <xref:System.Collections.IEnumerable?displayProperty=fullName>. Jeśli zaimplementowano <xref:System.Collections.IList>, należy dostarczyć wymagane elementy członkowskie o jednoznacznie określonym typie dla <xref:System.Collections.ICollection>. Jeśli obiekty w kolekcji są rozbudowywane <xref:System.ValueType?displayProperty=fullName>, musisz dostarczyć składową o jednoznacznie określonym typie dla <xref:System.Collections.IEnumerable.GetEnumerator%2A>, aby uniknąć spadku wydajności, który jest spowodowany opakowaniem; nie jest to wymagane, gdy obiekty kolekcji są typu referencyjnego.

 Aby zachować zgodność z tą regułą, należy zaimplementować elementy członkowskie interfejsu jawnie przy użyciu nazw w formie InterfaceName. InterfaceMemberName, takiej jak <xref:System.Collections.IList.Add%2A>. Jawne elementy członkowskie interfejsu używają typów danych zadeklarowanych przez interfejs. Zaimplementuj silnie wpisaną składowe przy użyciu nazwy elementu członkowskiego interfejsu, takiej jak `Add`. Zadeklaruj elementy członkowskie z jednoznacznie określonymi typami jako publiczne i zadeklaruj parametry i zwróć wartości jako typ silny, który jest zarządzany przez kolekcję. Silne typy zastępują słabsze typy, takie jak <xref:System.Object> i <xref:System.Array>, które są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, jawnie Zaimplementuj członków <xref:System.Collections.IList> i zapewnij silnie wpisane alternatywy dla elementów członkowskich, które zostały zanotowane wcześniej. W przypadku kodu, który poprawnie implementuje interfejs <xref:System.Collections.IList> i udostępnia wymagane elementy o jednoznacznie określonym typie, zapoznaj się z poniższym przykładem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżenie z tej reguły podczas implementowania nowej kolekcji opartej na obiektach, takiej jak lista połączona, gdzie typy, które poszerzają nową kolekcję, określają typ silny. Te typy powinny być zgodne z tą regułą i uwidaczniają silnie wpisaną składowe.

## <a name="example"></a>Przykład
 W poniższym przykładzie typ `YourType` rozszerza <xref:System.Collections.CollectionBase?displayProperty=fullName>, tak jak w przypadku wszystkich kolekcji o jednoznacznie określonym typie. Należy pamiętać, że <xref:System.Collections.CollectionBase> zapewnia jawną implementację interfejsu <xref:System.Collections.IList>. W związku z tym należy dostarczyć tylko elementy o jednoznacznie określonym typie dla <xref:System.Collections.IList> i <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.CollectionBase?displayProperty=fullName><xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
