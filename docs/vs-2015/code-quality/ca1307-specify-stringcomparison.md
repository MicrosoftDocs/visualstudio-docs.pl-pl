---
title: 'CA1307: Określ StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538921"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Określ argument StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Operacja porównywania ciągów używa przeciążenia metody, które nie ustawia <xref:System.StringComparison> parametru.

## <a name="rule-description"></a>Opis reguły
 Wiele operacji na ciągach, najważniejszych <xref:System.String.Compare%2A> <xref:System.String.Equals%2A> metod i, zapewniają Przeciążenie, które akceptuje <xref:System.StringComparison> wartość wyliczenia jako parametr.

 Za każdym razem, gdy istnieje Przeciążenie, które przyjmuje <xref:System.StringComparison> parametr, powinien zostać użyty zamiast przeciążenia, które nie przyjmuje tego parametru. Jawnie ustawiając ten parametr, kod jest często wyraźniejszy i łatwiejszy w obsłudze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić metody porównywania ciągów na przeciążenia, które akceptują <xref:System.StringComparison> Wyliczenie jako parametr. Na przykład: Zmień `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy biblioteka lub aplikacja jest przeznaczona dla ograniczonej liczby odbiorców lokalnych i dlatego nie zostanie zlokalizowana.

## <a name="see-also"></a>Zobacz też
 CA1309 [ostrzeżeń globalizacji](../code-quality/globalization-warnings.md) [: Użyj porządkowej StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
