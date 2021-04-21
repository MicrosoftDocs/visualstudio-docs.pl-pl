---
title: 'Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki'
description: Dowiedz się, jak utworzyć kartę niestandardową, a następnie dodać do niego kontrolki i ustawić ich położenie przy użyciu Projektanta wstążki.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3886e20d45834f98f36b8d7e48f3b11c9ef7d5dd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824825"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki
  Za pomocą Projektanta wstążki można utworzyć kartę niestandardową, a następnie dodać i umieścić na nim kontrolki.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- [Utwórz okienka akcji.](#BKMK_CreateActionsPanes)

- [Utwórz kartę niestandardową](#BKMK_CreateCustomTab).

- [Ukrywanie i pokazywanie okienek akcji przy użyciu przycisków na karcie niestandardowej](#BKMK_HideShowActionsPane).

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Tworzenie projektu skoroszytu programu Excel
 Kroki korzystania z Projektanta wstążki są prawie identyczne dla wszystkich aplikacji pakietu Office. W tym przykładzie użyto skoroszytu programu Excel.

### <a name="to-create-an-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel

- Utwórz projekt skoroszytu programu Excel o **nazwie MyExcelRibbon.** Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt w projektancie i dodaje projekt **MyExcelRibbon** do **Eksplorator rozwiązań**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Tworzenie okienek akcji
 Dodaj dwa okienka akcji niestandardowych do projektu. Później dodasz przyciski, które pokazują i ukrywają te okienka akcji na karcie niestandardowej.

### <a name="to-create-actions-panes"></a>Aby utworzyć okienka akcji

1. W menu **Project** (Projekt) wybierz pozycję **Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **ActionsPaneControl,** a następnie wybierz pozycję **Dodaj**.

     **ActionsPaneControl1.cs** lub **ActionsPaneControl1.vb** zostanie otwarty w projektancie.

3. Na karcie **Typowe kontrolki** **przybornika** dodaj etykietę na powierzchni projektanta.

4. W **oknie** Właściwości ustaw właściwość **Text** etykiety label1 na **wartość Actions Pane 1**.

5. Powtórz kroki od 1 do 5, aby utworzyć drugie okienko akcji i etykietę. Ustaw właściwość **Text** drugiej etykiety na **wartość Actions Pane 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Tworzenie karty niestandardowej
 Jedną z wytycznych dotyczących projektowania aplikacji pakietu Office jest to, że użytkownicy powinni zawsze mieć kontrolę nad interfejsem użytkownika aplikacji pakietu Office. Aby dodać tę możliwość do okienek akcji, możesz dodać przyciski, które pokazują i ukrywają każde okienko akcji na karcie niestandardowej na wstążce. Aby utworzyć kartę niestandardową, dodaj element Wstążki **(Projektant wizualny)** do projektu. Projektant ułatwia dodawanie i ustawianie położenia kontrolek, ustawianie właściwości kontrolek i obsługę zdarzeń kontrolek.

### <a name="to-create-a-custom-tab"></a>Aby utworzyć kartę niestandardową

1. W menu **Project (Projekt)** wybierz **pozycję Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję **Wstążka (Projektant wizualny).**

3. Zmień nazwę nowej wstążki na **MyRibbon,** a następnie wybierz pozycję **Dodaj**.

     Plik **MyRibbon.cs** lub **MyRibbon.vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i grupa.

4. W Projektancie wstążki wybierz kartę domyślną.

5. W **oknie Właściwości** rozwiń właściwość **ControlId,** a następnie ustaw właściwość **ControlIdType** na **wartość Custom**.

6. Ustaw właściwość **Etykieta** na wartość **Moja karta niestandardowa**.

7. W Projektancie wstążki wybierz pozycję **grupa1**.

8. W **oknie Właściwości** ustaw **etykietę na** **Menedżer okienek akcji**.

9. Na karcie **Kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij przycisk do **grupy 1.**

10. Wybierz **przycisk1.**

11. W **oknie Właściwości** ustaw **wartość Etykieta** na **Pokaż akcje w okienku 1.**

12. Dodaj drugi przycisk do **grupy group1** i ustaw właściwość **Etykieta** na **Pokaż akcje w okienku 2.**

13. Na karcie **Kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij kontrolkę **ToggleButton** do **grupy 1.**

14. Ustaw właściwość **Etykieta** na **wartość Ukryj okienko akcji.**

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Ukrywanie i pokazywanie okienek akcji przy użyciu przycisków na karcie niestandardowej
 Ostatnim krokiem jest dodanie kodu, który odpowiada użytkownikowi. Dodaj procedury obsługi zdarzeń <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dla zdarzeń dwóch przycisków i zdarzenia <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> przycisku przełączania. Dodaj kod do tych programów obsługi zdarzeń, aby umożliwić ukrywanie i wyświetlanie okienek akcji.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Aby ukryć i pokazać okienka akcji przy użyciu przycisków na karcie niestandardowej

1. W **Eksplorator rozwiązań** otwórz menu skrótów *dla pliku MyRibbon.cs* lub *MyRibbon.vb,* a następnie wybierz **pozycję Wyświetl kod.**

2. Dodaj następujący kod na początku `MyRibbon` klasy . Ten kod tworzy dwa obiekty okienka akcji.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet1":::

3. Zastąp metodę `MyRibbon_Load` następującym kodem. Ten kod dodaje obiekty okienka akcji do kolekcji i <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> ukrywa obiekty w widoku. Kod Visual C# dołącza również delegatów do kilku zdarzeń kontrolek wstążki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet2":::

4. Dodaj następujące trzy metody obsługi zdarzeń do `MyRibbon` klasy . Te metody obsługują <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwóch przycisków i <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenia przycisku przełączania. Procedury obsługi zdarzeń dla przycisków button1 i button2 pokazują okienka akcji alternatywnych. Procedura obsługi zdarzeń dla przełącznika ToggleButton1 pokazuje i ukrywa okienko aktywnych akcji.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet3":::

## <a name="test-the-custom-tab"></a>Testowanie karty niestandardowej
 Po uruchomieniu projektu program Excel zostanie uruchomiony, **a** na wstążce zostanie wyświetlona karta Moje niestandardowe. Wybierz przyciski na karcie **Moje niestandardowe,** aby wyświetlić i ukryć okienka akcji.

### <a name="to-test-the-custom-tab"></a>Aby przetestować kartę niestandardową

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Wybierz **kartę Moje niestandardowe.**

3. W grupie **Menedżer okienek akcji niestandardowych** wybierz pozycję **Pokaż akcje w okienku 1.**

     Zostanie wyświetlone okienko akcje z etykietą **Akcje Okienko 1**.

4. Wybierz **pozycję Pokaż akcje w okienku 2.**

     Zostanie wyświetlone okienko akcje z etykietą **Akcje Okienko 2**.

5. Wybierz **pozycję Ukryj okienko akcji.**

     Okienka akcji nie są już widoczne.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat dostosowywania interfejsu użytkownika pakietu Office można znaleźć w tych tematach:

- Dodaj kontekstowy interfejs użytkownika do dowolnego dostosowania na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Rozszerzanie standardowego lub niestandardowego Microsoft Office formularza programu Outlook. Aby uzyskać więcej informacji, [zobacz Przewodnik: projektowanie regionu formularza programu Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Przewodnik: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Jak zmienić położenie karty na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Jak dostosować wbudowaną kartę](../vsto/how-to-customize-a-built-in-tab.md)
- [Jak dodać kontrolki do widoku backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
