---
title: 'CA2241: Podaj poprawne argumenty metod formatowania'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f9f48f9cba146251aee1a58ffc7a3403ed899c4a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921500"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Podaj poprawne argumenty metod formatowania

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 `format` Ciąg argumentu przekazanego do metody takie jak <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, lub <xref:System.String.Format%2A?displayProperty=fullName> nie zawiera elementu format, który odpowiada każdemu obiektowi argumentu lub odwrotnie.

## <a name="rule-description"></a>Opis reguły
 Argumenty do metod, takich jak <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, i <xref:System.String.Format%2A> składają się z kilku następuje ciąg formatu <xref:System.Object?displayProperty=fullName> wystąpień. Ciąg formatu, który składa się z tekstu i elementów formatu osadzonego w postaci {indeksu [, wyrównanie] [: formatString]}. "index", jest liczony od zera liczba całkowita, która wskazuje, które obiektów do sformatowania. Jeśli obiekt nie ma odpowiedni indeks w ciągu formatu, obiekt zostanie zignorowany. Jeśli w obiekcie określonym przez "index" nie istnieje, <xref:System.FormatException?displayProperty=fullName> jest generowany w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, podaje elementu formatu dla każdemu obiektowi argumentu i podać argument obiektu dla każdego elementu formatu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwa naruszenia reguły.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]