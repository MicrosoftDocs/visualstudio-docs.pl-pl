---
title: 'CA1300: Określ argument MessageBoxOptions'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 746475e60bbe72c4ebfc51f13d0b2d4d0552ff62
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235198"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Określ argument MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda wywołuje Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metody, która nie <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> przyjmuje argumentu.

## <a name="rule-description"></a>Opis reguły

Aby wyświetlić okno komunikatu poprawnie dla kultur korzystających z kolejności czytania od prawej do lewej, Przekaż do <xref:System.Windows.Forms.MessageBox.Show%2A> metody pola [MessageBoxOptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) i [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) . <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Sprawdź Właściwość zawierającej kontrolki, aby określić, czy ma być używana kolejność odczytywania od prawej do lewej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, wywołaj Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A> metody, która <xref:System.Windows.Forms.MessageBoxOptions> przyjmuje argument.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli biblioteka kodu nie zostanie zlokalizowana dla kultury korzystającej z kolejności odczytywania od prawej do lewej, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, która wyświetla okno komunikatu z opcjami, które są odpowiednie dla kolejności odczytywania kultury. Plik zasobu, który nie jest wyświetlany, jest wymagany do skompilowania przykładu. Postępuj zgodnie z komentarzami w przykładzie, aby skompilować przykład bez pliku zasobów i przetestować funkcję od prawej do lewej.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index)