---
title: Klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdb46f79d6b300280c6743a368953bac5c5b02d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933902"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Klasy specyficzne dla kultury dla globalnych formularzy Windows i formularzy sieci web

Każda kultura ma różnych Konwencji do wyświetlania daty, godziny, liczby, waluty i inne informacje. <xref:System.Globalization> Przestrzeń nazw zawiera klasy, które mogą służyć do modyfikowania wartości jak specyficzne dla kultury są wyświetlane, takich jak:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Kalendarz**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Za pomocą ustawienia kulturowe

Użyj ustawienia kultury, przechowywane w aplikacji lub w **Opcje regionalne** Panelu sterowania, aby określić Konwencji kultury w czasie wykonywania i odpowiednio sformatować informacji. Aby uzyskać więcej informacji na temat ustawiania kultury, zobacz [jak: Ustawianie kultury i kultury UI dla globalizacji strony sieci web platformy ASP.NET](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klasy, które automatycznie Formatuj informacje zgodnie z ustawieniem kultury są nazywane *specyficzne dla kultury*. Niektóre metody specyficzne dla kultury
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Niektóre funkcje specyficzne dla kultury (w języku Visual Basic) są `MonthName` i `WeekDayName`.

Na przykład, poniższy kod przedstawia, jak można użyć <xref:System.IFormattable.ToString%2A> metodę format waluty bieżącej kultury:

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

Kultura jest ustawiona na "fr-FR", zobaczysz następujące opcje w oknie danych wyjściowych:

`100,00`

Kultura ma wartość "en US", zobaczysz następujące opcje w oknie danych wyjściowych:

`$100.00`

## <a name="see-also"></a>Zobacz także

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)