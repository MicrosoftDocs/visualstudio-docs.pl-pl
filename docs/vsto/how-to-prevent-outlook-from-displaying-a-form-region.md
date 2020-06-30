---
title: 'Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90da255beb0a85a302158feb1f9d5cc4981437eb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520137"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook
  Mogą wystąpić sytuacje, w których nie chcesz, aby program Microsoft Office Outlook wyświetlał region formularza dla określonego elementu. Na przykład jeśli element Contact nie zawiera adresu służbowego, można zapobiec wyświetlaniu regionu formularza, który pokazuje lokalizację firmy na mapie.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Aby uniemożliwić programowi Outlook wyświetlanie regionu formularza

1. Otwórz plik kodu dla regionu formularza, który chcesz zmodyfikować.

2. Rozwiń węzeł region kod **fabryczny regionu formularza** .

3. Dodaj kod do `FormRegionInitializing` programu obsługi zdarzeń, który ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy na **true**.

   Jeśli w tym przykładzie element Contact nie zawiera adresu, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość ma **wartość true**, a region formularza nie jest wyświetlany.

## <a name="example"></a>Przykład
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Zobacz też
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
