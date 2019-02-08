---
title: 'CA1051: Nie deklaruj widocznych pól w wystąpieniach'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd4783f6327061da0ce522cc02082289cdee3d39
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938098"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nie deklaruj widocznych pól w wystąpieniach

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz ma pola wystąpienia widoczne na zewnątrz.

## <a name="rule-description"></a>Opis reguły
 Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być `private` lub `internal` i powinien być udostępniany przy użyciu właściwości. Jest to łatwe do dostępu do właściwości jest dostępu do pola i kod w metody dostępu właściwości można zmieniać funkcje typu rozwiń bez wprowadzania przełomowych zmian. Właściwości, które po prostu zwracają wartość pola prywatne lub wewnętrzne są zoptymalizowanych pod kątem podłączonego do uzyskiwania dostępu do pola; bardzo mało wydajne jest skojarzony z użyciem pól widocznego na zewnątrz za pośrednictwem właściwości.

 Widoczne na zewnątrz odwołuje się do `public`, `protected`, i `protected internal` (`Public`, `Protected`, i `Protected Friend` w języku Visual Basic) poziomów ułatwień dostępu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Przekształć pole `private` lub `internal` i udostępnić ją za pomocą właściwości widocznego na zewnątrz.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Widoczne na zewnątrz pola nie oferuje żadnych korzyści, które są niedostępne dla właściwości. Ponadto pola publiczne nie mogą być chronione przez [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands). Zobacz [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu (`BadPublicInstanceFields`) który narusza tę regułę. `GoodPublicInstanceFields` Wyświetla poprawiony kod.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Zobacz także
 [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)