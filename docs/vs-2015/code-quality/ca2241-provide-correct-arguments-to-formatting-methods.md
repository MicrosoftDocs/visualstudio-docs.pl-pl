---
title: 'CA2241: Podaj poprawne argumenty metod formatowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543653"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Podaj poprawne argumenty metod formatowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 `format`Argument ciągu przesłany do metody, takiej jak <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> lub nie <xref:System.String.Format%2A?displayProperty=fullName> zawiera elementu formatu odpowiadającego każdemu argumentowi obiektu lub na odwrót.

## <a name="rule-description"></a>Opis reguły
 Argumenty metod, takich jak <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> i <xref:System.String.Format%2A> składają się z ciągu formatu, po którym następuje kilka <xref:System.Object?displayProperty=fullName> wystąpień. Ciąg formatu składa się z tekstu i osadzonych elementów formatu w formularzu {index [, Alignment] [: formatString]}. "index" to liczba całkowita oparta na zero, która wskazuje, które obiekty mają być sformatowane. Jeśli obiekt nie ma odpowiedniego indeksu w ciągu formatu, obiekt jest ignorowany. Jeśli obiekt określony przez element "index" nie istnieje, <xref:System.FormatException?displayProperty=fullName> jest generowany w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, podaj element formatu dla każdego argumentu obiektu i podaj argument obiektu dla każdego elementu formatu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa naruszenia reguły.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
