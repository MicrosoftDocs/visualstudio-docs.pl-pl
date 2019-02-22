---
title: 'Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2d310956753398c55fdc6d367f24a6ba8bec101
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599740"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki
  Za pomocą projektanta wstążki, można utworzyć niestandardową kartę, a następnie dodaj i ustawianie formantów na nim.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

-   [Tworzenie okienek akcji](#BKMK_CreateActionsPanes).

-   [Tworzenie kart niestandardowych](#BKMK_CreateCustomTab).

-   [Ukryć i pokazać okienka akcji za pomocą przycisków na karcie niestandardowe](#BKMK_HideShowActionsPane).

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Program Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Utwórz projektu skoroszytu programu Excel
 Kroki dotyczące korzystania z projektanta wstążek są niemal identyczne dla wszystkich aplikacji pakietu Office. W tym przykładzie użyto skoroszytu programu Excel.

### <a name="to-create-an-excel-workbook-project"></a>Aby utworzyć projekt arkusza Excel

-   Utwórz projektu skoroszytu programu Excel o nazwie **MyExcelRibbon**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt w Projektancie i dodaje **MyExcelRibbon** projekt **Eksploratora rozwiązań**.

##  <a name="BKMK_CreateActionsPanes"></a> Tworzyć okienka akcji
 Dodaj dwa okienka akcji niestandardowych do projektu. Należy później dodać przyciski, który pokazuje i ukrywa te okienka akcji niestandardowej karty.

### <a name="to-create-actions-panes"></a>Aby tworzyć okienka akcji

1.  Na **projektu** menu, wybierz **Dodaj nowy element**.

2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **ActionsPaneControl**, a następnie wybierz **Dodaj**.

     **ActionsPaneControl1.cs** lub **ActionsPaneControl1.vb** plik zostanie otwarty w projektancie.

3.  Z **wspólnych formantów** karcie **przybornika**, Dodaj etykietę do powierzchni projektanta.

4.  W **właściwości** oknie **tekstu** właściwość elementu label1 w **okienko akcji 1**.

5.  Powtórz kroki od 1 do 5, aby utworzyć drugi panel akcji i etykiety. Ustaw **tekstu** właściwość drugiej etykiety na **okienko akcji 2**.

##  <a name="BKMK_CreateCustomTab"></a> Tworzenie kart niestandardowych
 Jedną z wytycznych projektowania aplikacji pakietu Office jest, czy użytkownicy powinni zawsze mieć kontrolki interfejsu użytkownika aplikacji pakietu Office. Aby dodać tę zdolność dla okienek akcji, możesz dodać przyciski, które pokazują i chowają każde okienko akcji z niestandardowej karty na Wstążce. Aby utworzyć niestandardową kartę, należy dodać **Wstążka (Projektant graficzny)** do projektu. Projektant pomaga dodać i ustawianie formantów, ustawianie właściwości formantu i obsługiwać zdarzenia formantu.

### <a name="to-create-a-custom-tab"></a>Aby utworzyć niestandardową kartę

1.  Na **projektu** menu, wybierz **Dodaj nowy element**.

2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)**.

3.  Zmień nazwę nowego wstążki do **MyRibbon**i wybierz polecenie **Dodaj**.

     **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.

4.  W Projektancie wstążki wybierz kartę domyślną.

5.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustaw **ControlIdType** właściwości **niestandardowe**.

6.  Ustaw **etykiety** właściwości **Moje karty niestandardowe**.

7.  W Projektancie wstążki wybierz **grupa1**.

8.  W **właściwości** oknie **etykiety** do **Menedżera okienka akcji**.

9. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij przycisk do **grupa1**.

10. Wybierz **button1**.

11. W **właściwości** oknie **etykiety** do **Pokaż okienko akcji 1**.

12. Dodaj drugi przycisk, który **grupa1**i ustaw **etykiety** właściwości **pokazać okienko akcji 2**.

13. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij **ToggleButton** kontrolować na **grupa1**.

14. Ustaw **etykiety** właściwości **ukryć okienko akcji**.

##  <a name="BKMK_HideShowActionsPane"></a> Ukryć i pokazać okienka akcji za pomocą przycisków na karcie niestandardowe
 Ostatnim krokiem jest, aby dodać kod, który odpowiada użytkownikowi. Dodawanie obsługi zdarzeń <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwa przyciski i <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenia przycisku przełącznika. Dodaj kod do tych programów obsługi zdarzeń, aby umożliwić wyświetlanie i ukrywanie okienka akcji.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Aby ukryć i pokazać okienka akcji przy użyciu przycisków w karcie niestandardowej

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla *MyRibbon.cs* lub *MyRibbon.vb*, a następnie wybierz **Wyświetl kod**.

2.  Dodaj następujący kod na górze `MyRibbon` klasy. Ten kod tworzy dwa obiekty okienka akcji.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3.  Zastąp `MyRibbon_Load` metoda następującym kodem. Ten kod dodaje obiekty akcji okienka do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> zbierania i ukrywa obiekty z widoku. Kod Visual C# dołącza również delegaty do kilku zdarzeń kontrolek wstążki.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4.  Dodaj następujące trzy metody obsługi wydarzeń do `MyRibbon` klasy. Te metody obsługują <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwa przyciski i <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenia przycisku przełącznika. Programy obsługi zdarzeń dla button1 i button2 umożliwiają wyświetlenie okienka akcji alternatywnej. Obsługa zdarzenia toggleButton1 pokazuje i ukrywa okienko aktywnych czynności.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Testowanie karty niestandardowej
 Po uruchomieniu projektu, uruchamia się Excel i **Moje karty niestandardowe** na Wstążce zostanie wyświetlona karta. Wybierz przyciski ma **Moje karty niestandardowe** by pokazać lub ukryć okienka działań.

### <a name="to-test-the-custom-tab"></a>Aby przetestować niestandardową kartę

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.

2.  Wybierz **Moje karty niestandardowe** kartę.

3.  W **Menedżera okienka akcji niestandardowych** grupy, wybierz **Pokaż okienko akcji 1**.

     W okienku Akcje pojawia się i wyświetli etykietę **okienko akcji 1**.

4.  Wybierz **Pokaż okienko akcji 2**.

     W okienku Akcje pojawia się i wyświetli etykietę **okienko akcji 2**.

5.  Wybierz **ukryć okienko akcji**.

     Okienka czynności nie są już widoczne.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu dostosowywania interfejsu użytkownika pakietu Office w tych tematach:

-   Dodaj oparte na kontekście interfejsu użytkownika do jakiegokolwiek dostosowywania poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

-   Rozszerz standardowy lub niestandardowy formularz programu Microsoft Office Outlook. Aby uzyskać więcej informacji, zobacz [instruktażu: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Zobacz także
- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: Zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie formantów do widoku zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)
