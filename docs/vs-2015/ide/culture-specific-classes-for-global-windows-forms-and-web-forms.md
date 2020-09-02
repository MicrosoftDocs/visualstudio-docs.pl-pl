---
title: Klasy specyficzne dla kultury dla globalnych Windows Forms i formularzy sieci Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c2d048387e4e81763a63b5bf010c36c87beeacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665905"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każda kultura ma różne konwencje do wyświetlania dat, godzin, cyfr, waluty i innych informacji. <xref:System.Globalization>Przestrzeń nazw zawiera klasy, których można użyć do modyfikacji sposobu wyświetlania wartości specyficznych dla kultury, takich jak <xref:System.Globalization.DateTimeFormatInfo> **Kalendarz**i <xref:System.Globalization.NumberFormatInfo> .

## <a name="using-the-culture-setting"></a>Korzystanie z ustawienia kultury
 Jednak większość czasu Użyj ustawienia kultury, przechowywanego w aplikacji lub w panelu sterowania **Opcje regionalne** , aby automatycznie określić konwencje w czasie wykonywania i odpowiednio sformatować odpowiednie informacje. Aby uzyskać więcej informacji na temat ustawiania kultury, zobacz [How to: Set the Culture and UI Culture for Windows Forms globalizacja](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) lub [How to: Set the Culture and ui Culture for ASP.NET globalizacji Web Page](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klasy, które automatycznie formatują informacje zgodnie z ustawieniem kultury, są nazywane specyficznymi dla kultury. Niektóre metody specyficzne dla kultury to <xref:System.IFormattable.ToString%2A?displayProperty=fullName> , <xref:System.Console.WriteLine%2A?displayProperty=fullName> , i <xref:System.String.Format%2A?displayProperty=fullName> . Niektóre funkcje specyficzne dla kultury (w języku Visual Basic) są `MonthName` i `WeekDayName` .

 Na przykład poniższy kod pokazuje, jak można użyć <xref:System.IFormattable.ToString%2A> metody do formatowania waluty dla bieżącej kultury:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))

```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

 Jeśli kultura jest ustawiona na "fr-FR", zostanie ona wyświetlona w oknie danych wyjściowych:

 `100,00`

 Jeśli kultura jest ustawiona na wartość "en-US", zostanie ona wyświetlona w oknie danych wyjściowych:

 `$100.00`

## <a name="see-also"></a>Zobacz też
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName> <xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)
