---
title: Wyświetlanie tekstu w polu tekstowym w arkuszu przy użyciu przycisku
description: Poznaj podstawy używania przycisków i pól tekstowych w arkuszach programu Microsoft Excel. Można również tworzyć projekty programu Excel przy użyciu narzędzi deweloperacyjnych pakietu Office Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827789"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Przewodnik: wyświetlanie tekstu w polu tekstowym w arkuszu przy użyciu przycisku
  W tym przewodniku przedstawiono podstawy używania przycisków i pól tekstowych w arkuszach programu Excel Microsoft Office oraz sposób tworzenia projektów programu Excel przy użyciu narzędzi deweloperacyjnych pakietu Office w programie Visual Studio. Aby zobaczyć wynik jako ukończony przykład, zobacz Excel Controls Sample (Przykład formantów programu Excel) w temacie [Office development samples and walkthroughs (Przykłady](../vsto/office-development-samples-and-walkthroughs.md)dla programistów pakietu Office i wskazówki).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W tym przewodniku dowiesz się, jak:

- Dodawanie kontrolek do arkusza.

- Wypełnij pole tekstowe po kliknięciu przycisku.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel przy użyciu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Mój przycisk programu Excel.** Upewnij się, **że wybrano opcję Utwórz** nowy dokument. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Przycisk programu Excel** do Eksplorator rozwiązań . 

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 W tym przewodniku potrzebny będzie przycisk i pole tekstowe w pierwszym arkuszu.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Sprawdź, czy **skoroszyt mój Button.xlsxExcel** jest otwarty w projektancie Visual Studio, z `Sheet1` wyświetlonym komunikatem.

2. Na karcie **Typowe kontrolki** przybornika przeciągnij element do <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> pola `Sheet1` .

3. W menu **Widok** wybierz pozycję **Okno właściwości.**

4. Upewnij się, **że pole TextBox1** jest widoczne w polu listy rozwijanej Okno właściwości i zmień właściwość  **Name** pola tekstowego na **displayText**.

5. Przeciągnij **kontrolkę Przycisk** na i `Sheet1` zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Tekst**|**Wstaw tekst**|

   Teraz napisz kod do uruchomienia po kliknięciu przycisku.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pole tekstowe po kliknięciu przycisku
 Za każdym razem, gdy użytkownik kliknie przycisk, **Hello world!** jest dołączany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać w polu tekstowym po kliknięciu przycisku

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję Arkusz1**, a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. W języku C# należy dodać do zdarzenia program obsługi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń, jak pokazano poniżej. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że komunikat **Hello world!** w polu tekstowym po kliknięciu przycisku.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Kliknij przycisk .

3. Potwierdź, **że Hello world!** w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy używania przycisków i pól tekstowych w arkuszach programu Excel. Oto kilka zadań, które mogą pojawić się w następnej części:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

- Używanie pól wyboru do zmiany formatowania. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania arkusza przy użyciu kontrolek CheckBox.](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Zobacz też
- [Jak dodać kontrolki Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
- [Ograniczenia kontrolek Windows Forms dokumentów pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
