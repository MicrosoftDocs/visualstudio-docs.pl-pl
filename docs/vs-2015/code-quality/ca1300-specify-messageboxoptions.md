---
title: 'CA1300: Określ argument MessageBoxOptions | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0f325695cab1a5fd9db4206f16414ea462dfe49c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792677"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Określ argument MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda wywołuje przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodę, która nie przyjmuje <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły
 Aby wyświetlić okno komunikatu poprawnie dla kultur stosujących pismo kolejność czytania od prawej do lewej, <xref:System.Windows.Forms.MessageBoxOptions> i <xref:System.Windows.Forms.MessageBoxOptions> członkowie <xref:System.Windows.Forms.MessageBoxOptions> wyliczenia muszą zostać przekazane do <xref:System.Windows.Forms.MessageBox.Show%2A> metody. Sprawdź <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> właściwości zawierającego formantu, aby określić, czy używać kolejność czytania od prawej do lewej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A> metody, która przyjmuje <xref:System.Windows.Forms.MessageBoxOptions> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie jest lokalizowany biblioteki kodu dla kultury, która używa kolejność czytania od prawej do lewej.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która wyświetla okno komunikatu, który zawiera opcje, które są właściwe dla kultury kolejność odczytu. W pliku zasobów, który nie jest wyświetlany, jest wymagany do kompilowania w przykładzie. Postępuj zgodnie z uwagi na przykład, aby zbudować przykład bez pliku zasobów i do testowania funkcji od prawej do lewej.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Zasoby w aplikacjach klasycznych](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
