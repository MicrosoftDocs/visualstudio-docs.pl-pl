---
title: 'Instrukcje: Dodaj przycisk Uruchom okno dialogowe do grupy wstążki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac39cd45c566d837d34cf8e7be0cf94ded8de419
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862541"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Instrukcje: Dodaj przycisk Uruchom okno dialogowe do grupy wstążki
  Możesz dodać przycisk Uruchom okno dialogowe z żadną grupą na Wstążce. Przycisk Uruchom okno dialogowe jest mała ikona, która pojawia się w grupie. Użytkownicy, kliknij tę ikonę, aby otworzyć określone okno dialogowe lub okienka zadań, które zapewniają więcej opcji, które odnoszą się do tej grupy.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Aby dodać przycisk Uruchom okno dialogowe do grupy wstążki  
  
1.  Wybierz plik kodu wstążki (*.vb* lub *.cs* pliku) w **Eksploratora rozwiązań**.  
  
2.  Na **widoku** menu, kliknij przycisk **projektanta**.  
  
3.  W Projektancie wstążki, kliknij prawym przyciskiem myszy dowolną grupę, a następnie kliknij przycisk **Dodaj element DialogBoxLauncher**.  
  
     Dodaj kod, aby <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> zdarzeń grupę, aby otworzyć okno dialogowe niestandardowych i wbudowanych.  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [XML — Wstążka](../vsto/ribbon-xml.md)   
 [Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Instrukcje: Zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Instrukcje: Dodawanie formantów do widoku zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Przewodnik: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
