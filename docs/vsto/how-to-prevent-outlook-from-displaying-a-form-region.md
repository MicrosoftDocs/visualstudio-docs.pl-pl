---
title: 'How to: Prevent Outlook from displaying a form region (Jak zapobiec wyświetlaniu regionu formularza w programie Outlook)'
description: Dowiedz się, jak Microsoft Office wyświetlanie regionu formularza dla określonego elementu w programie Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825852"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>How to: Prevent Outlook from displaying a form region (Jak zapobiec wyświetlaniu regionu formularza w programie Outlook)
  Mogą wystąpić sytuacje, w których nie chcesz, aby Microsoft Office Outlook wyświetlał region formularza dla określonego elementu. Jeśli na przykład element kontaktu nie zawiera adresu firmy, możesz zapobiec pojawianiu się regionu formularza, który pokazuje lokalizację firmy na mapie.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Aby uniemożliwić programowi Outlook wyświetlanie regionu formularza

1. Otwórz plik kodu dla regionu formularza, który chcesz zmodyfikować.

2. Rozwiń **region kodu Fabryki regionów** formularzy.

3. Dodaj kod do `FormRegionInitializing` programu obsługi zdarzeń, który <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ustawia właściwość klasy na <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true**.

   Jeśli w tym przykładzie element kontaktu nie zawiera adresu, właściwość jest ustawiona na <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> **wartość true** i region formularza nie jest wyświetlany.

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Zobacz także
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Jak dodać region formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Przewodnik: projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Przewodnik: importowanie regionu formularza zaprojektowanego w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
