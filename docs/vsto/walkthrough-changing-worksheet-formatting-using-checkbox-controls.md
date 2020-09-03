---
title: Zmiana formatowania arkusza za pomocą kontrolek CheckBox
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42d2c46f6fd61d74476933cfda3dea8c62b00c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328702"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Przewodnik: zmiana formatowania arkusza za pomocą kontrolek CheckBox
  W tym instruktażu przedstawiono podstawowe informacje dotyczące używania pól wyboru w arkuszu programu Excel Microsoft Office, aby zmienić formatowanie. W programie Visual Studio będziesz używać narzędzi programistycznych pakietu Office do tworzenia i dodawania kodu do projektu. Aby zobaczyć wynik jako ukończony przykład, zobacz przykład kontrolki programu Excel w programie [Office przykłady i przewodniki dotyczące projektowania](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W tym instruktażu dowiesz się, jak:

- Dodaj tekst i kontrolki do arkusza.

- Sformatuj tekst w przypadku wybrania opcji.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel przy użyciu programu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Moje formatowanie w programie Excel**. Upewnij się, że wybrano **Utwórz nowy dokument** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **Moje formatowanie programu Excel** do **Eksplorator rozwiązań**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Dodawanie tekstu i kontrolek do arkusza
 W tym instruktażu będziesz potrzebować trzech <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> kontrolek i tekstu w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolce.

### <a name="to-add-three-check-boxes"></a>Aby dodać trzy pola wyboru

1. Upewnij się, że skoroszyt jest otwarty w projektancie programu Visual Studio i `Sheet1` jest otwarty.

2. Na karcie **Formanty standardowe** **przybornika**przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> formant do lub blisko komórki **B2** w **arkuszu Arkusz1**.

3. Z menu **Widok** wybierz polecenie okno **Właściwości** .

4. Upewnij się, że **checkBox1** jest widoczny w polu listy Nazwa obiektu okna **Właściwości** i Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Tekst**|**Pogrubiona**|

5. Przeciągnij drugie pole wyboru do lub blisko komórki **B4** i Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Tekst**|**Kursywa**|

6. Przeciągnij trzecie pole wyboru w komórce **B6** lub blisko niej, a następnie Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Tekst**|**Podkreślenie**|

7. Zaznacz wszystkie trzy kontrolki pola wyboru, przytrzymując klawisz **Ctrl** .

8. W grupie Rozmieść karty format w programie Excel kliknij pozycję **Wyrównaj**, a następnie kliknij pozycję **Wyrównaj do lewej**.

     Trzy kontrolki pola wyboru są wyrównane po lewej stronie, na pozycji pierwszej zaznaczonej kontrolki.

     Następnie przeciągniesz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do arkusza.

    > [!NOTE]
    > Możesz również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, wpisując **TextFont** w polu **Nazwa** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Aby dodać tekst do kontrolki NamedRange

1. Na karcie **formanty programu Excel** przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do komórki **B9**.

2. Sprawdź, czy **$B $9** pojawia się w edytowalnym polu tekstowym i zaznacz komórkę **B9** . Jeśli tak nie jest, kliknij komórkę **B9** , aby ją zaznaczyć.

3. Kliknij przycisk **OK**.

4. Komórka **B9** przybiera zakres o nazwie `NamedRange1` .

    W arkuszu nie ma widocznych wskazań, ale `NamedRange1` pojawia się w **polu Nazwa** (tuż nad arkuszem po lewej stronie), gdy jest zaznaczona komórka **B9** .

5. Upewnij się, że **namedRange1** jest widoczny w polu listy Nazwa obiektu okna **Właściwości** i Zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**TextFont**|
   |**Wartość2**|**Kliknij pole wyboru, aby zmienić formatowanie tego tekstu.**|

   Następnie napisz kod, aby sformatować tekst w przypadku wybrania opcji.

## <a name="format-the-text-when-an-option-is-selected"></a>Sformatuj tekst w przypadku wybrania opcji
 W tej sekcji napiszesz kod w taki sposób, że gdy użytkownik wybierze opcję formatowania, format tekstu w arkuszu zostanie zmieniony.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Aby zmienić formatowanie, gdy pole wyboru jest zaznaczone

1. Kliknij prawym przyciskiem myszy pozycję **Arkusz1**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń `applyBoldFont` pola wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń `applyItalicFont` pola wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń `applyUnderlineFont` pola wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. W języku C# należy dodać obsługę zdarzeń dla pól wyboru do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia, jak pokazano poniżej. Aby uzyskać informacje dotyczące tworzenia programów obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować skoroszyt, aby upewnić się, że tekst jest sformatowany prawidłowo po zaznaczeniu lub usunięciu zaznaczenia pola wyboru.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Zaznacz lub wyczyść pole wyboru.

3. Upewnij się, że tekst jest poprawnie sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące używania pól wyboru i formatowania tekstu w arkuszach programu Excel. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Wypełnienie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
