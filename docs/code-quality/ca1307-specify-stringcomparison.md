---
title: 'CA1307: Określ StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3b3d979910883f6be9f542ec581ecbda0f91deb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444370"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Operacja porównywania ciągów używa przeciążenia metody, które nie ustawia parametru <xref:System.StringComparison>.

## <a name="rule-description"></a>Opis reguły
Wiele operacji na ciągach, co jest najważniejszymi metodami <xref:System.String.Compare%2A> i <xref:System.String.Equals%2A>, zapewniają Przeciążenie, które akceptuje wartość wyliczenia <xref:System.StringComparison> jako parametr.

Za każdym razem, gdy istnieje Przeciążenie, które pobiera <xref:System.StringComparison> parametru, należy użyć zamiast przeciążenia, które nie przyjmuje tego parametru. Jawnie ustawiając ten parametr, kod jest często wyraźniejszy i łatwiejszy w obsłudze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić metody porównywania ciągów na przeciążenia, które akceptują Wyliczenie <xref:System.StringComparison> jako parametr. Na przykład: Zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych i dlatego nie zostanie zlokalizowana.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
- [CA1309: Używaj wyliczenia StringComparison stosującego reguły sortowania oparte na wartości](../code-quality/ca1309-use-ordinal-stringcomparison.md)
