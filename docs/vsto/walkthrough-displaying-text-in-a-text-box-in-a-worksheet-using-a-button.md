---
title: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku
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
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328707"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Przewodnik: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku
  W tym instruktażu przedstawiono podstawowe informacje dotyczące używania przycisków i pól tekstowych w Microsoft Office arkuszach programu Excel oraz sposobu tworzenia projektów programu Excel przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio. Aby zobaczyć wynik jako ukończony przykład, zobacz przykład kontrolki programu Excel w programie [Office przykłady i przewodniki dotyczące projektowania](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W tym instruktażu dowiesz się, jak:

- Dodawanie formantów do arkusza.

- Wypełnij pole tekstowe po kliknięciu przycisku.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel za pomocą programu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel z **przyciskiem nazwa mój program Excel**. Upewnij się, że wybrano **Utwórz nowy dokument** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **przycisku my Excel** do **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 W tym instruktażu będziesz potrzebować przycisku i pola tekstowego w pierwszym arkuszu.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Upewnij się, że skoroszyt **mój program Excel Button.xlsx** jest otwarty w projektancie programu Visual Studio z `Sheet1` wyświetlonym poleceniem.

2. Na karcie **Formanty standardowe** przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> do `Sheet1` .

3. Z menu **Widok** wybierz polecenie **okno właściwości**.

4. Upewnij się, że **TextBox1** jest widoczny w polu listy rozwijanej okna **Właściwości** i zmień właściwość **Nazwa** pola tekstowego na **DisplayText**.

5. Przeciągnij kontrolkę **Button na przycisk** `Sheet1` i Zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Tekst**|**Wstaw tekst**|

   Teraz napisz kod do uruchomienia, gdy przycisk zostanie kliknięty.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pole tekstowe po kliknięciu przycisku
 Za każdym razem, gdy użytkownik kliknie przycisk, **Hello World!** jest dołączany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać w polu tekstowym po kliknięciu przycisku

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Arkusz1**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. W języku C# należy dodać procedurę obsługi zdarzeń do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia, jak pokazano poniżej. Aby uzyskać informacje dotyczące tworzenia programów obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Możesz teraz przetestować skoroszyt, aby upewnić się, że wiadomość **Hello World!** pojawia się w polu tekstowym po kliknięciu przycisku.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Kliknij przycisk.

3. Potwierdź, że **Hello World!** pojawia się w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące używania przycisków i pól tekstowych w arkuszach programu Excel. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

- Przy użyciu pól wyboru, aby zmienić formatowanie. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmiana formatowania arkusza za pomocą kontrolek CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
