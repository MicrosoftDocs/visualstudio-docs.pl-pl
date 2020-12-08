---
title: 'Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook'
description: Dowiedz się, jak zapobiegać wyświetlaniu przez Microsoft Office programu Outlook regionu formularza dla określonego elementu.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f247bf82d51fda6d321b45c16f91b857300cc1e4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847679"
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

## <a name="see-also"></a>Zobacz także
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
