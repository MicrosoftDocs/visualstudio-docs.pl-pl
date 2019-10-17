---
title: 'CA1309: Użyj porządkowego StringComparison'
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
ms.openlocfilehash: e5274352a867c4c25c5fc68fd674c1e4c4855c2d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440619"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego StringComparison

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Operacja porównywania ciągów, która nie jest językiem, nie ustawia parametru <xref:System.StringComparison> na wartość **porządkową** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
Wiele operacji na ciągach, co jest najważniejszymi metodami <xref:System.String.Compare%2A?displayProperty=fullName> i <xref:System.String.Equals%2A?displayProperty=fullName>, udostępnia teraz Przeciążenie, które akceptuje wartość wyliczenia <xref:System.StringComparison?displayProperty=fullName> jako parametr.

Po określeniu wartości **StringComparison. porządkowych** lub **StringComparison. OrdinalIgnoreCase**, Porównywanie ciągów nie jest językiem. Oznacza to, że funkcje, które są specyficzne dla języka naturalnego są ignorowane w przypadku podejmowania decyzji dotyczących porównania. Ignorowanie funkcji języka naturalnego oznacza, że decyzje są oparte na prostych porównaniach bajtów, a nie na wielkości liter lub tabel równoważności, które są sparametryzowane przez kulturę. W związku z tym poprzez jawne ustawienie parametru na **StringComparison. numer porządkowy** lub **StringComparison. OrdinalIgnoreCase**, kod często uzyskuje szybkość, zwiększa poprawność i jest bardziej niezawodny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić metodę porównywania ciągów na Przeciążenie, które akceptuje Wyliczenie <xref:System.StringComparison?displayProperty=fullName> jako parametr, i określić wartość **porządkową** lub **OrdinalIgnoreCase**. Na przykład zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych lub gdy należy używać semantyki bieżącej kultury.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
- [CA1307: Określ wyliczenie StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
