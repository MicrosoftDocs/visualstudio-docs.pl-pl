---
title: 'Przewodnik: Zmiana formatowania arkusza za pomocą formantów CheckBox'
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
ms.openlocfilehash: aba73d5fc6c1609a3347178765ba516840b5176e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061692"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Przewodnik: Zmiana formatowania arkusza za pomocą formantów CheckBox
  W tym instruktażu przedstawiono podstawy używania pola wyboru w arkuszu kalkulacyjnym programu Microsoft Office Excel, aby zmienić formatowanie. Użyjesz narzędzi programistycznych pakietu Office w programie Visual Studio do tworzenia i dodać kod do projektu. Aby wyświetlić wynik, jako przykład ukończone, zobacz przykład formanty programu Excel w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Z tego instruktażu dowiesz się jak:

- Dodawanie tekstu i formantów do arkusza.

- Sformatuj tekst, gdy opcja jest zaznaczona.

- Testowanie projektu.

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt
 W tym kroku utworzysz projektu skoroszytu programu Excel przy użyciu programu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje formatowania programu Excel**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje formatowania programu Excel** projekt **Eksploratora rozwiązań**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Dodawanie tekstu i kontrolek do arkusza
 Dla tego przewodnika, potrzebujesz trzech <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> kontrolek i tekst w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli.

### <a name="to-add-three-check-boxes"></a>Aby dodać trzy pola wyboru

1. Sprawdź, czy skoroszyt jest otwarty w projektancie programu Visual Studio, które `Sheet1` jest otwarty.

2. Z **wspólnych formantów** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> formantu do lub w pobliżu komórki **B2** w **Arkusz1**.

3. Z **widoku** menu, wybierz opcję **właściwości** okna.

4. Upewnij się, że **Checkbox1** jest widoczna w polu listy nazwy obiektu z **właściwości** okna i Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Text**|**Bold**|

5. Przeciągnij drugie pole wyboru na lub w pobliżu komórki **B4** i Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Text**|**Kursywa**|

6. Przeciągnij trzecie pole wyboru na lub w pobliżu komórki **B6** i Zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Text**|**Underline**|

7. Wybierz wszystkie formanty trzy pola wyboru podczas przechowywania **Ctrl** klucza.

8. W grupie rozmieszczanie w karcie Format w programie Excel kliknij **Wyrównaj**, a następnie kliknij przycisk **Wyrównaj do lewej**.

     Formanty trzy pola wyboru są wyrównane po lewej stronie, na pozycji pierwszego wybraną kontrolką.

     Następnie możesz przeciągnąć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza.

    > [!NOTE]
    >  Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, wpisując **textFont** do **nazwa** pole.

#### <a name="to-add-text-to-a-namedrange-control"></a>Aby dodać tekst do kontrolki NamedRange

1. Z **kontrolki programu Excel** kartę przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę komórki **B9**.

2. Upewnij się, że **$B$ 9** pojawia się w polu tekst do edycji, a tej komórki **B9** jest zaznaczone. Jeśli nie, kliknij pozycję komórki **B9** aby go zaznaczyć.

3. Kliknij przycisk **OK**.

4. Komórka **B9** staje się zakres o nazwie `NamedRange1`.

    Nie ma żadnego wskazania widoczne w arkuszu, ale `NamedRange1` pojawia się w **pola Nazwa podmiotu** (tuż nad arkusz po lewej stronie) gdy komórka **B9** jest zaznaczone.

5. Upewnij się, że **NamedRange1** jest widoczna w polu listy nazwy obiektu z **właściwości** okna i Zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**textFont**|
   |**Value2**|**Kliknij pole wyboru, aby zmienić formatowanie tekstu.**|

   Następnie należy napisać kod do formatowania tekstu, gdy opcja jest zaznaczona.

## <a name="format-the-text-when-an-option-is-selected"></a>Sformatuj tekst po wybraniu opcji
 W tej sekcji trzeba napisać kod, tak aby po użytkownik wybierze opcję formatowania, zmieni się na format tekstu w arkuszu.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Aby zmienić formatowanie, gdy pole wyboru jest zaznaczone

1. Kliknij prawym przyciskiem myszy **Arkusz1**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyBoldFont` pole wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyItalicFont` pole wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyUnderlineFont` pole wyboru:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. W języku C#, należy dodać obsługę zdarzeń dla pola wyboru, aby <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszytu, aby upewnić się, że tekst jest prawidłowo sformatowany, zaznacz lub usuń zaznaczenie pola wyboru.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Zaznacz lub wyczyść pole wyboru.

3. Upewnij się, że tekst jest prawidłowo sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawy korzystania z pola wyboru oraz formatowania tekstu w arkuszach programu Excel. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Zobacz także
- [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
