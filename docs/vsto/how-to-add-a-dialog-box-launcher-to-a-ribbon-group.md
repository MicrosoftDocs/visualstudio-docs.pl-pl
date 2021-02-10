---
title: 'Instrukcje: Dodawanie uruchamiania okna dialogowego do grupy wstążki'
description: Możesz dodać przycisk Uruchom okno dialogowe do dowolnej grupy na Wstążce, która może otwierać powiązane okna dialogowe lub okienka zadań, które udostępniają więcej opcji odnoszących się do grupy.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d8e04b7549d1b6a458f0993804946502f55f0165
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942285"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Instrukcje: Dodawanie uruchamiania okna dialogowego do grupy wstążki
  Możesz dodać przycisk uruchamiania okna dialogowego do dowolnej grupy na Wstążce. Uruchamia okno dialogowe jest małą ikoną wyświetlaną w grupie. Użytkownicy klikają tę ikonę, aby otworzyć powiązane okna dialogowe lub okienka zadań, które zawierają więcej opcji odnoszących się do grupy.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Aby dodać Uruchamianie okna dialogowego do grupy wstążki

1. Wybierz plik kodu wstążki (plik *VB* lub *cs* ) w **Eksplorator rozwiązań**.

2. W menu **Widok** kliknij pozycję **Projektant**.

3. W Projektancie wstążki kliknij prawym przyciskiem myszy dowolną grupę, a następnie kliknij polecenie **Dodaj element DialogBoxLauncher**.

     Dodaj kod do <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> zdarzenia grupy w celu otworzenia niestandardowego lub wbudowanego okna dialogowego.

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Instrukcje: Eksportowanie wstążki z Projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: zmiana położenia karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie kontrolek do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
