---
title: 'CA1309: Użyj porządkowego ustawienia właściwości StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00accdbdb08e4267bbca2b7e5fab8002f539f1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546482"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego ustawienia właściwości StringComparison

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia <xref:System.StringComparison> albo parametr **numer** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
 Wiele ciągów operacje, co najważniejsze <xref:System.String.Compare%2A?displayProperty=fullName> i <xref:System.String.Equals%2A?displayProperty=fullName> metod, teraz dostarczać przeciążenia, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wartość wyliczenia jako parametr.

 Po określeniu jednej **StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, porównywania ciągów jest niejęzykowy. Oznacza to funkcje, które są specyficzne dla języka naturalnego są ignorowane, podczas porównywania decyzji. Ignorowanie funkcje języka naturalnego oznacza, że decyzje są oparte na porównania jednobajtowych a nie wielkością liter lub równoważności tabel, które są parametryzowane przez kulturę. W rezultacie przez jawne ustawienie parametru na wartość **StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, kod często uzyskuje szybkość, zwiększa poprawność i staje się bardziej niezawodna.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień metodę porównywania ciągów na przeciążenie, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wyliczenia jako parametr oraz określ **numer** lub **OrdinalIgnoreCase**. Na przykład zmienić `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy biblioteki lub aplikacja jest przeznaczona dla ograniczonej grupie osób lokalnych lub w przypadku, gdy semantykę bieżącej kultury, które powinny być używane.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
- [CA1307: Specify StringComparison](../code-quality/ca1307-specify-stringcomparison.md)