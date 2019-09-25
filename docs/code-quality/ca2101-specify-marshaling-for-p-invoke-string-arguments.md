---
title: 'CA2101: Określ kierowanie dla argumentów ciągu P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49c9dfdac1d8d8aec8ec32df7374b5ae0a28e92
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233024"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Określ kierowanie dla argumentów ciągu P/Invoke

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

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

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]