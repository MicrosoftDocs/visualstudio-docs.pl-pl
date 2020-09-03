---
title: 'CA1300: Określ MessageBoxOptions | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539194"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Określ argument MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda wywołuje Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metody, która nie przyjmuje <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły
 Aby wyświetlić okno komunikatu prawidłowo dla kultur korzystających z kolejności czytania od prawej do lewej, <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> elementy członkowskie <xref:System.Windows.Forms.MessageBoxOptions> wyliczenia muszą być przekazywać do <xref:System.Windows.Forms.MessageBox.Show%2A> metody. Sprawdź <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Właściwość zawierającej kontrolki, aby określić, czy ma być używana kolejność odczytywania od prawej do lewej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A> metody, która przyjmuje <xref:System.Windows.Forms.MessageBoxOptions> argument.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli biblioteka kodu nie zostanie zlokalizowana dla kultury korzystającej z kolejności odczytywania od prawej do lewej, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która wyświetla okno komunikatu z opcjami, które są odpowiednie dla kolejności odczytywania kultury. Plik zasobu, który nie jest wyświetlany, jest wymagany do skompilowania przykładu. Postępuj zgodnie z komentarzami w przykładzie, aby skompilować przykład bez pliku zasobów i przetestować funkcję od prawej do lewej.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[Zasoby w aplikacjach klasycznych](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
