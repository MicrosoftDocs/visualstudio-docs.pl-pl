---
title: 'Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 473b88dca8813d1db3c465105dc7eca95e49dfbe
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868930"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy
  Może to być sytuacje, w których nie ma programu Microsoft Office Outlook do wyświetlania regionu formularza dla określonego elementu. Na przykład skontaktuj się z pomocą element zawiera adres służbowy, może uniemożliwić pokazujący lokalizacji firmy na mapie wyświetlaniu regionu formularza.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Aby zapobiec wyświetlaniu regionu formularza programu Outlook  
  
1. Otwórz plik kodu dla regionu formularza, który chcesz zmodyfikować.  
  
2. Rozwiń **fabryka regionów formularza** kodu regionu.  
  
3. Dodaj kod, aby `FormRegionInitializing` programu obsługi zdarzeń, która ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy **true**.  
  
   W tym przykładzie, jeśli element kontaktu nie zawierają adresu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość jest ustawiona na **true**, i regionu formularza nie jest wyświetlana.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
