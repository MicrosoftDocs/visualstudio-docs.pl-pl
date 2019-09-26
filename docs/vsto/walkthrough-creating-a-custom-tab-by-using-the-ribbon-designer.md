---
title: 'Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki'
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
ms.openlocfilehash: 5a32cfc84aa9bc93761dc8b57c13651eb04031a2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255522"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki
  Za pomocą projektanta wstążki można utworzyć niestandardową kartę, a następnie dodać do niej kontrolki i położenia.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- [Utwórz okienka akcji](#BKMK_CreateActionsPanes).

- [Utwórz kartę niestandardową](#BKMK_CreateCustomTab).

- [Ukrywanie i wyświetlanie okienek akcji przy użyciu przycisków na karcie niestandardowe](#BKMK_HideShowActionsPane).

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Program Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Utwórz projekt skoroszytu programu Excel
 Kroki związane z korzystaniem z projektanta wstążki są prawie identyczne we wszystkich aplikacjach pakietu Office. Ten przykład używa skoroszytu programu Excel.

### <a name="to-create-an-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel

- Utwórz projekt skoroszytu programu Excel o nazwie **MyExcelRibbon**. Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     Program Visual Studio otwiera nowy skoroszyt w Projektancie i dodaje projekt **MyExcelRibbon** do **Eksplorator rozwiązań**.

## <a name="BKMK_CreateActionsPanes"></a>Tworzenie okienek akcji
 Dodaj dwa okienka akcji niestandardowych do projektu. Później dodasz przyciski pokazujące i ukrywając te okienka akcji na karcie niestandardowe.

### <a name="to-create-actions-panes"></a>Aby utworzyć okienka akcji

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **ActionsPaneControl**, a następnie wybierz pozycję **Dodaj**.

     Plik **ActionsPaneControl1.cs** lub **ActionsPaneControl1. vb** zostanie otwarty w projektancie.

3. Na karcie **Formanty standardowe** **przybornika**Dodaj etykietę do powierzchni projektanta.

4. W oknie **Właściwości** ustaw właściwość **Text** elementu Label1 na **Actions Window 1**.

5. Powtórz kroki od 1 do 5 w celu utworzenia drugiego okienka akcji i etykiety. Ustaw właściwość **Text** drugiej etykiety w **okienku Akcje 2**.

## <a name="BKMK_CreateCustomTab"></a>Tworzenie niestandardowej karty
 Jedną z wytycznych dotyczących projektowania aplikacji pakietu Office jest to, że użytkownicy powinni zawsze mieć kontrolę nad interfejsem użytkownika aplikacji pakietu Office. Aby dodać tę możliwość dla okienek akcji, możesz dodać przyciski pokazujące i ukrywające poszczególne akcje na karcie niestandardowej na Wstążce. Aby utworzyć niestandardową kartę, Dodaj do projektu element **wstążki (Projektant wizualizacji)** . Projektant ułatwia dodawanie i określanie położenia kontrolek, Ustawianie właściwości kontrolki i obsługę zdarzeń kontroli.

### <a name="to-create-a-custom-tab"></a>Aby utworzyć kartę niestandardową

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant wizualny)** .

3. Zmień nazwę nowej wstążki **na Wstążkę, a**następnie wybierz pozycję **Dodaj**.

     Plik **MyRibbon.cs** lub **webwstążka. vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

4. W Projektancie wstążki wybierz kartę domyślną.

5. W oknie **Właściwości** rozwiń Właściwość **ControlID** , a następnie ustaw właściwość **ControlIdType** na **Custom**.

6. Ustaw właściwość **etykieta** na **moją kartę niestandardową**.

7. W Projektancie wstążki wybierz **grupa1**.

8. W oknie **Właściwości** ustaw wartość **etykieta** **Menedżer okienka akcji**.

9. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij przycisk na **grupa1**.

10. Wybierz pozycję **Button1**.

11. W oknie **Właściwości** Ustaw **etykietę** , aby **wyświetlić okienko akcje 1**.

12. Dodaj drugi przycisk do **grupa1**i ustaw właściwość **etykieta** na **Pokaż okienko akcji 2**.

13. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij kontrolkę **ToggleButton** na **grupa1**.

14. Ustaw właściwość **etykieta** na **Ukryj okienko akcje**.

## <a name="BKMK_HideShowActionsPane"></a>Ukrywanie i wyświetlanie okienek akcji przy użyciu przycisków na karcie niestandardowe
 Ostatnim krokiem jest dodanie kodu, który odpowiada użytkownikowi. Dodaj programy obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzeń dwóch przycisków <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> i zdarzenia przycisku przełącznika. Dodaj kod do tych programów obsługi zdarzeń, aby włączyć ukrywanie i wyświetlanie okienek akcji.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Aby ukryć i wyświetlić okienka akcji przy użyciu przycisków na karcie niestandardowe

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla *MyRibbon.cs* lub *wstążki. vb*, a następnie wybierz polecenie **Wyświetl kod**.

2. Dodaj następujący kod na górze `MyRibbon` klasy. Ten kod tworzy dwa obiekty okienka akcji.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Zastąp `MyRibbon_Load` metodę poniższym kodem. Ten kod umożliwia dodanie obiektów okienka Akcje do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> kolekcji i ukrycie obiektów z widoku. Kod wizualizacji C# dołącza także delegatów do kilku zdarzeń kontrolki wstążki.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Dodaj następujące trzy metody obsługi zdarzeń do `MyRibbon` klasy. Te metody obsługują <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwóch przycisków <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> i zdarzenia przycisku przełącznika. Procedury obsługi zdarzeń dla Button1 i Button2 pokażą okienka alternatywne akcje. Procedura obsługi zdarzeń dla toggleButton1 pokazuje i ukrywa aktywne akcje okienka.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Przetestuj kartę niestandardową
 Gdy uruchamiasz projekt, program Excel zostanie uruchomiony, a karta **My Custom** Tab pojawia się na Wstążce. Wybierz przyciski na **mojej karcie niestandardowe** , aby pokazać i ukryć okienka akcji.

### <a name="to-test-the-custom-tab"></a>Aby przetestować kartę niestandardową

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Wybierz kartę **moja karta niestandardowa** .

3. W grupie **Menedżer okienka Akcje niestandardowe** wybierz **Pokaż okienko akcje 1**.

     Zostanie wyświetlone okienko akcje i wyświetlenie **okienka Akcje etykiet 1**.

4. Wybierz **Pokaż okienko akcji 2**.

     Zostanie wyświetlone okienko akcje i wyświetlenie **okienka Akcje etykiet 2**.

5. Wybierz **Ukryj okienko akcje**.

     Okienka akcji nie są już widoczne.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office można znaleźć w następujących tematach:

- Dodaj interfejs użytkownika oparty na kontekście do dowolnych dostosowań na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Rozbudowa standardowego lub niestandardowego formularza programu Outlook Microsoft Office. Aby uzyskać więcej informacji, [zobacz Przewodnik: Projektuj region](../vsto/walkthrough-designing-an-outlook-form-region.md)formularza programu Outlook.

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Instrukcje: Zmiana pozycji karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
