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
ms.openlocfilehash: eff846cfacb30d97c28cadd14b86f7724b1d2ce4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234938"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego ustawienia właściwości StringComparison

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Operacja porównywania ciągów, która nie jest językiem, nie <xref:System.StringComparison> ustawia parametru na wartość **porządkową** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
Wiele operacji na <xref:System.String.Compare%2A?displayProperty=fullName> ciągach, co jest najważniejszymi metodami i <xref:System.String.Equals%2A?displayProperty=fullName> , zapewnia teraz Przeciążenie, <xref:System.StringComparison?displayProperty=fullName> które akceptuje wartość wyliczenia jako parametr.

Po określeniu wartości **StringComparison. porządkowych** lub **StringComparison. OrdinalIgnoreCase**, Porównywanie ciągów nie jest językiem. Oznacza to, że funkcje, które są specyficzne dla języka naturalnego są ignorowane w przypadku podejmowania decyzji dotyczących porównania. Ignorowanie funkcji języka naturalnego oznacza, że decyzje są oparte na prostych porównaniach bajtów, a nie na wielkości liter lub tabel równoważności, które są sparametryzowane przez kulturę. W związku z tym poprzez jawne ustawienie parametru na **StringComparison. numer porządkowy** lub **StringComparison. OrdinalIgnoreCase**, kod często uzyskuje szybkość, zwiększa poprawność i jest bardziej niezawodny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić metodę porównywania ciągów na Przeciążenie, które akceptuje <xref:System.StringComparison?displayProperty=fullName> Wyliczenie jako parametr, i określić wartość **porządkową** lub **OrdinalIgnoreCase**. Na przykład zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych lub gdy należy używać semantyki bieżącej kultury.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
- [CA1307 Określ StringComparison](../code-quality/ca1307-specify-stringcomparison.md)