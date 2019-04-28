---
title: 'Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f74eaa8618ce497a760754d084f390a4d1b8c1d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436090"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku
  W tym instruktażu przedstawiono podstawy używania przycisków i pola tekstowe w arkuszach programu Microsoft Office Excel i jak tworzyć projekty programu Excel przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio. Aby wyświetlić wynik, jako przykład ukończone, zobacz przykład formanty programu Excel w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Z tego instruktażu dowiesz się jak:

- Dodawanie formantów do arkusza.

- Po kliknięciu przycisku, należy wypełnić pole tekstowe.

- Testowanie projektu.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt
 W tym kroku utworzysz projekt skoroszyt programu Excel przy użyciu programu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projektu skoroszytu programu Excel o nazwie **przycisk Moje Excel**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **przycisk Moje Excel** projekt **Eksploratora rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 W ramach tego przewodnika należy przycisk i pole tekstowe z pierwszego arkusza.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Upewnij się, że **Moje Button.xlsx Excel** skoroszyt jest otwarty w Projektancie Visual Studio za pomocą `Sheet1` wyświetlane.

2. Z **wspólnych formantów** kartę przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> do `Sheet1`.

3. Z **widoku** menu, wybierz opcję **okno właściwości**.

4. Upewnij się, że **TextBox1** jest widoczna w **właściwości** pole listy rozwijanej w oknie i zmień **nazwa** właściwości pola tekstowego **Wyświetlany_tekst**.

5. Przeciągnij **przycisk** kontrolować na `Sheet1` i Zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Text**|**Wstaw tekst**|

   Teraz można napisać kod do uruchomienia po kliknięciu przycisku.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pola tekstowego, po kliknięciu przycisku
 Każdorazowo, użytkownik kliknie przycisk, **Witaj, świecie!** jest dołączany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać do pola tekstowego, po kliknięciu przycisku

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Arkusz1**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń przycisku:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. W C#, należy dodać program obsługi zdarzeń do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszytu, aby upewnić się, że komunikat **Witaj, świecie!** Po kliknięciu przycisku, zostanie wyświetlony w polu tekstowym.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Kliknij przycisk.

3. Upewnij się, że **Hello World!** zostanie wyświetlony w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawy używania przycisków i pola tekstowe w arkuszach programu Excel. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

- Za pomocą pola wyboru, aby zmienić formatowanie. Aby uzyskać więcej informacji, zobacz [instruktażu: Arkusz Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
