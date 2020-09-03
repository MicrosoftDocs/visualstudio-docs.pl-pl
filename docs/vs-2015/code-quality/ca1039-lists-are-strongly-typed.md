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
ms.openlocfilehash: 4e485375c12564b5416c79bd3a41dedb1da76dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533448"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listy są silnie typizowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje, <xref:System.Collections.IList?displayProperty=fullName> ale nie zapewnia metody silnie wpisanej dla co najmniej jednego z następujących elementów:

- Element IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga <xref:System.Collections.IList> implementacji, aby zapewnić składowe silnie wpisane, tak aby użytkownicy nie musieli rzutować argumentów na <xref:System.Object?displayProperty=fullName> Typ, gdy korzystają z funkcji dostarczonych przez interfejs. <xref:System.Collections.IList>Interfejs jest implementowany przez kolekcje obiektów, do których można uzyskać dostęp za pomocą indeksu. Ta reguła zakłada, że typ, który implementuje, <xref:System.Collections.IList> służy do zarządzania kolekcją wystąpień typu, który jest silniejszy niż <xref:System.Object> .

 <xref:System.Collections.IList> implementuje <xref:System.Collections.ICollection?displayProperty=fullName> interfejsy i <xref:System.Collections.IEnumerable?displayProperty=fullName> . W przypadku zaimplementowania programu <xref:System.Collections.IList> należy dostarczyć wymagane elementy członkowskie o jednoznacznie określonym typie dla <xref:System.Collections.ICollection> . Jeśli obiekty w kolekcji są rozbudowane <xref:System.ValueType?displayProperty=fullName> , należy zapewnić jednoznacznie wpisany element członkowski, <xref:System.Collections.IEnumerable.GetEnumerator%2A> Aby uniknąć spadku wydajności, który jest spowodowany opakowaniem; nie jest to wymagane, gdy obiekty kolekcji są typu referencyjnego.

 Aby zachować zgodność z tą regułą, należy zaimplementować elementy członkowskie interfejsu jawnie przy użyciu nazw w postaci InterfaceName. InterfaceMemberName, takich jak <xref:System.Collections.IList.Add%2A> . Jawne elementy członkowskie interfejsu używają typów danych zadeklarowanych przez interfejs. Zaimplementuj silnie wpisane elementy członkowskie przy użyciu nazwy składowej interfejsu, takiej jak `Add` . Zadeklaruj elementy członkowskie z jednoznacznie określonymi typami jako publiczne i zadeklaruj parametry i zwróć wartości jako typ silny, który jest zarządzany przez kolekcję. Silne typy zastępują słabsze typy, takie jak <xref:System.Object> i <xref:System.Array> , które są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, jawnie Zaimplementuj <xref:System.Collections.IList> członków i podaj silnie wpisane alternatywy dla elementów członkowskich, które zostały zanotowane wcześniej. W przypadku kodu, który poprawnie implementuje <xref:System.Collections.IList> interfejs i udostępnia wymagane elementy o jednoznacznie określonym typie, zapoznaj się z poniższym przykładem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżenie z tej reguły podczas implementowania nowej kolekcji opartej na obiektach, takiej jak lista połączona, gdzie typy, które poszerzają nową kolekcję, określają typ silny. Te typy powinny być zgodne z tą regułą i uwidaczniają silnie wpisaną składowe.

## <a name="example"></a>Przykład
 W poniższym przykładzie typ `YourType` rozciąga się <xref:System.Collections.CollectionBase?displayProperty=fullName> , podobnie jak wszystkie kolekcje o jednoznacznie określonym typie. Należy pamiętać, że <xref:System.Collections.CollectionBase> zapewnia to jawną implementację <xref:System.Collections.IList> interfejsu. W związku z tym należy dostarczyć tylko elementy o jednoznacznie określonym typie dla <xref:System.Collections.IList> i <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
