---
title: 'CA2241: Podaj poprawne argumenty metod formatowania | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a139db3fb1ece41c1d3f18471a286c72a7a576c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783118"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Podaj poprawne argumenty metod formatowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
