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
ms.openlocfilehash: d11afe8a3ea8fcae971461b8e33fc4771b74eb75
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947474"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listy są silnie typizowane

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Publiczny lub chroniony typ implementuje <xref:System.Collections.IList?displayProperty=fullName> , ale udostępnia silnie typizowane metody dla co najmniej jednej z następujących czynności:

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>Opis reguły

Ta reguła wymaga <xref:System.Collections.IList> implementacji w celu dostarczenia silnie typizowane składowe, dzięki czemu użytkownicy nie musieli rzutować argumentów na <xref:System.Object?displayProperty=fullName> wpisz podczas korzystania z funkcji dostępnych przez interfejs. <xref:System.Collections.IList> Interfejs jest implementowany przez kolekcje obiektów, które mogą być udostępniane przez indeks. Reguła ta zakłada, że typ, który zawiera <xref:System.Collections.IList> umożliwia zarządzanie kolekcją wystąpień typów mocniejszych niż <xref:System.Object>.

<xref:System.Collections.IList> implementuje <xref:System.Collections.ICollection?displayProperty=fullName> i <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsów. W przypadku zaimplementowania <xref:System.Collections.IList>, musisz podać wymagane silnie typizowanych elementów członkowskich dla <xref:System.Collections.ICollection>. Jeśli obiekty z kolekcji rozszerzony <xref:System.ValueType?displayProperty=fullName>, należy podać element silnie typizowaną dla <xref:System.Collections.IEnumerable.GetEnumerator%2A> w celu uniknięcia spadek wydajności, jest spowodowany przez pakowania; nie jest to wymagane w przypadku obiektów kolekcji typu odwołania.

Aby jest zgodne z tą regułą, należy zaimplementować składowych interfejsu jawnie przy użyciu nazwy w postaci InterfaceName.InterfaceMemberName, takich jak <xref:System.Collections.IList.Add%2A>. Elementy członkowskie interfejsu jawnego używania typów danych, które są zadeklarowane przez interfejs. Implementowanie silnie typizowanych elementów członkowskich przy użyciu nazwy elementu członkowskiego interfejsu, takiego jak `Add`. Zadeklaruj silnie typizowanych elementów członkowskich jako publiczne i można deklarować parametrów i zwracają wartości na typ silny, który jest zarządzany przez kolekcję. Silne typy Zastąp słabszych typów, takich jak <xref:System.Object> i <xref:System.Array> , są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, jawne Implementowanie <xref:System.Collections.IList> elementów członkowskich i dostarczają alternatywy silnie typizowanych elementów członkowskich, które zostały podane wcześniej. Dla kodu, który implementuje prawidłowo <xref:System.Collections.IList> interfejs i zapewnia wymagane silnie typizowanych elementów członkowskich, zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły w przypadku implementowania nowej kolekcji opartej na obiektach takich jak liście połączonej, których typy rozszerzające możliwości Nowa kolekcja określić silnego typu. Te typy powinny są zgodne z tą regułą i udostępnić silnie typizowanych elementów członkowskich.

## <a name="example"></a>Przykład
 W poniższym przykładzie typ `YourType` rozszerza <xref:System.Collections.CollectionBase?displayProperty=fullName>, podobnie jak wszystkie kolekcje silnie typizowane. <xref:System.Collections.CollectionBase> zapewnia jawną implementację <xref:System.Collections.IList> interfejsu. W związku z tym, należy tylko podać silnie typizowanych elementów członkowskich dla <xref:System.Collections.IList> i <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>