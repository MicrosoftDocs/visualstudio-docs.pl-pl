---
title: 'CA1307: Określ argument StringComparison'
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
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922292"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ argument StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Operacja porównywania ciągów używa przeciążenia metody, które nie ustawia <xref:System.StringComparison> parametru.

## <a name="rule-description"></a>Opis reguły
Wiele operacji na <xref:System.String.Compare%2A> ciągach, najważniejszych metod <xref:System.String.Equals%2A> i, zapewniają Przeciążenie, które akceptuje <xref:System.StringComparison> wartość wyliczenia jako parametr.

Za każdym razem, gdy istnieje Przeciążenie <xref:System.StringComparison> , które przyjmuje parametr, powinien zostać użyty zamiast przeciążenia, które nie przyjmuje tego parametru. Jawnie ustawiając ten parametr, kod jest często wyraźniejszy i łatwiejszy w obsłudze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zmienić metody porównywania ciągów na przeciążenia, które akceptują <xref:System.StringComparison> Wyliczenie jako parametr. Na przykład: Zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych i dlatego nie zostanie zlokalizowana.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)
- [CA1309: Użyj porządkowej StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)