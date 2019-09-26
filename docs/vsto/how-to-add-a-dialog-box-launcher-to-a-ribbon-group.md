---
title: 'Porady: Dodawanie uruchamiania okna dialogowego do grupy wstążki'
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
ms.openlocfilehash: b930348845e04dca089cf153a11cc2a9fd29c880
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255902"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Instrukcje: Dodawanie uruchamiania okna dialogowego do grupy wstążki
  Możesz dodać przycisk uruchamiania okna dialogowego do dowolnej grupy na Wstążce. Uruchamia okno dialogowe jest małą ikoną wyświetlaną w grupie. Użytkownicy klikają tę ikonę, aby otworzyć powiązane okna dialogowe lub okienka zadań, które zawierają więcej opcji odnoszących się do grupy.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Aby dodać Uruchamianie okna dialogowego do grupy wstążki

1. Wybierz plik kodu wstążki (plik*VB* lub *cs* ) w **Eksplorator rozwiązań**.

2. W menu **Widok** kliknij pozycję **Projektant**.

3. W Projektancie wstążki kliknij prawym przyciskiem myszy dowolną grupę, a następnie kliknij polecenie **Dodaj element DialogBoxLauncher**.

     Dodaj kod do <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> zdarzenia grupy w celu otworzenia niestandardowego lub wbudowanego okna dialogowego.

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do kodu XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: Zmiana pozycji karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
