---
title: 'CA1300: Określ argument MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6b72d40bbb2f83eeb8a402b2d389a941f64bfef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845379"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Określ argument MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda wywołuje przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodę, która nie przyjmuje <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły

Aby wyświetlić okno komunikatu poprawnie dla kultur stosujących pismo kolejność czytania od prawej do lewej, należy przekazać [właściwość MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) i [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) polom <xref:System.Windows.Forms.MessageBox.Show%2A> Metoda. Sprawdź <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> właściwości zawierającego formantu, aby określić, czy używać kolejność czytania od prawej do lewej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A> metody, która przyjmuje <xref:System.Windows.Forms.MessageBoxOptions> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie jest lokalizowany biblioteki kodu dla kultury, która używa kolejność czytania od prawej do lewej.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, która wyświetla okno komunikatu, który zawiera opcje, które są właściwe dla kultury kolejność odczytu. W pliku zasobów, który nie jest wyświetlany, jest wymagany do kompilowania w przykładzie. Postępuj zgodnie z uwagi na przykład, aby zbudować przykład bez pliku zasobów i do testowania funkcji od prawej do lewej.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Zasoby w aplikacjach komputerowych (.NET Framework)](/dotnet/framework/resources/index)