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
ms.openlocfilehash: 3bdb8ef315c9702cc10352368aba7202a8f29f7f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920000"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Podaj poprawne argumenty metod formatowania

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Argument ciągu przesłany do metody, takiej jak <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>lub <xref:System.String.Format%2A?displayProperty=fullName> nie zawiera elementu formatu odpowiadającego każdemu argumentowi obiektu lub na odwrót. `format`

## <a name="rule-description"></a>Opis reguły
Argumenty metod <xref:System.Console.WriteLine%2A>, takich jak, i <xref:System.Console.Write%2A> <xref:System.String.Format%2A> składają się z ciągu formatu, po którym następuje kilka <xref:System.Object?displayProperty=fullName> wystąpień. Ciąg formatu składa się z tekstu i osadzonych elementów formatu w formularzu {index [, Alignment] [: formatString]}. "index" to liczba całkowita oparta na zero, która wskazuje, które obiekty mają być sformatowane. Jeśli obiekt nie ma odpowiedniego indeksu w ciągu formatu, obiekt jest ignorowany. Jeśli obiekt określony przez element "index" nie istnieje, <xref:System.FormatException?displayProperty=fullName> jest generowany w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, podaj element formatu dla każdego argumentu obiektu i podaj argument obiektu dla każdego elementu formatu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono dwa naruszenia reguły.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]