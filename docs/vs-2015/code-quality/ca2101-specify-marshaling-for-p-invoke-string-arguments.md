---
title: 'CA2101: Określ kierowanie dla argumentów ciągu P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57b7214058baf63ffa5e3ee2c9a982bf411b60e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652184"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Należy określić marshaling dla argumentów typu string P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Element członkowski wywołania platformy zezwala na częściowo zaufane obiekty wywołujące, ma parametr String i nie jest jawnie zorganizowany przez ciąg.

## <a name="rule-description"></a>Opis reguły
 W przypadku konwersji z formatu Unicode na ANSI, istnieje możliwość, że nie wszystkie znaki Unicode mogą być reprezentowane na określonej stronie kodowej ANSI. *Najbardziej pasujące mapowanie* próbuje rozwiązać ten problem przez podstawianie znaku dla znaku, którego nie można reprezentować. Korzystanie z tej funkcji może spowodować potencjalną lukę w zabezpieczeniach, ponieważ nie można kontrolować wybranego znaku. Na przykład złośliwy kod może celowo utworzyć ciąg Unicode, który zawiera znaki, które nie znajdują się na określonej stronie kodowej, które są konwertowane na znaki specjalne systemu plików, takie jak ".." lub "/". Należy zauważyć, że sprawdzanie zabezpieczeń w przypadku znaków specjalnych często występuje przed konwersją ciągu na ANSI.

 Mapowanie najlepiej dopasowane jest wartością domyślną dla konwersji niezarządzanej, WChar do MB. O ile nie wyłączysz jawnie mapowania najlepszego dopasowania, kod może zawierać lukę w zabezpieczeniach, z powodu tego problemu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy jawnie zorganizować typy danych ciągu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która narusza tę regułę, a następnie pokazuje, jak naprawić naruszenie.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
