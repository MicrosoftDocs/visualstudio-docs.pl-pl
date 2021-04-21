---
title: Zmienianie formatowania arkusza przy użyciu kontrolek CheckBox
description: Dowiedz się, jak tworzyć i dodawać kod do projektu za pomocą Visual Studio pakietu Office w programie .
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6f649fad99b8d94cc650ecda57e10b423b14194e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826437"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Przewodnik: zmienianie formatowania arkusza przy użyciu kontrolek CheckBox
  W tym przewodniku przedstawiono podstawowe informacje dotyczące używania pól wyboru w Microsoft Office programu Excel w celu zmiany formatowania. Do tworzenia i dodawania kodu do projektu użyj Visual Studio pakietu Office w programie . Aby zobaczyć wynik jako ukończony przykład, zobacz Przykład formantów programu Excel w przykładach i przewodnikach dla programistów [pakietu Office.](../vsto/office-development-samples-and-walkthroughs.md)

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W ramach tego przewodnika dowiesz się, jak:

- Dodawanie tekstu i kontrolek do arkusza.

- Sformatuj tekst po wybraniu opcji.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel przy użyciu Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **Moje formatowanie programu Excel.** Upewnij się, **że wybrano opcję Utwórz** nowy dokument. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Moje formatowanie programu Excel** do **Eksplorator rozwiązań**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Dodawanie tekstu i kontrolek do arkusza
 Na potrzeby tego przewodnika będziesz potrzebować trzech <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> kontrolek i tekstu w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolce.

### <a name="to-add-three-check-boxes"></a>Aby dodać trzy pola wyboru

1. Sprawdź, czy skoroszyt jest otwarty w projektancie Visual Studio i `Sheet1` czy jest otwarty.

2. Na karcie **Typowe kontrolki** **przybornika przeciągnij** kontrolkę do komórki B2 lub w pobliżu jej w <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> arkuszu **Arkusz1**. 

3. W menu **Widok** wybierz **okno** Właściwości.

4. Upewnij się, **że pole wyboru Checkbox1** jest widoczne w polu listy nazw obiektów w oknie **Właściwości** i zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Tekst**|**Pogrubiona**|

5. Przeciągnij drugie pole wyboru do komórki B4 lub w pobliżu komórki **B4** i zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Tekst**|**Kursywa**|

6. Przeciągnij trzecie pole wyboru do komórki **B6** lub w pobliżu tej komórki i zmień następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Tekst**|**Podkreślenie**|

7. Zaznacz wszystkie trzy kontrolki pola wyboru, przytrzymując **naciśnięty klawisz Ctrl.**

8. Na karcie Format na karcie Rozmieść grupę w programie Excel kliknij pozycję **Wyrównaj**, a następnie kliknij pozycję **Wyrównaj do lewej.**

     Trzy kontrolki pola wyboru są wyrównane po lewej stronie na pozycji pierwszej wybranej kontrolki.

     Następnie przeciągniesz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do arkusza.

    > [!NOTE]
    > Możesz również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, wpisując **tekstFont** w **polu** Nazwa.

#### <a name="to-add-text-to-a-namedrange-control"></a>Aby dodać tekst do kontrolki NamedRange

1. Na karcie **Kontrolki programu Excel** przybornika przeciągnij kontrolkę <xref:Microsoft.Office.Tools.Excel.NamedRange> do komórki **B9.**

2. Sprawdź, **$B 9 USD** pojawia się w edytowalnym polu tekstowym i czy komórka **B9** jest zaznaczona. Jeśli tak nie jest, kliknij komórkę **B9,** aby ją zaznaczyć.

3. Kliknij przycisk **OK**.

4. Komórka **B9 staje** się zakresem o nazwie `NamedRange1` .

    Nie ma widocznego wskazania w arkuszu, ale pojawia się w polu Nazwa (tuż nad arkuszem po lewej stronie), gdy komórka `NamedRange1` **B9** jest  zaznaczona.

5. Upewnij się, **że namedRange1** jest widoczny w polu listy nazw obiektów w **oknie Właściwości** i zmień następujące właściwości:

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**textFont**|
   |**Wartość 2**|**Kliknij pole wyboru, aby zmienić formatowanie tego tekstu.**|

   Następnie napisz kod, aby sformatować tekst po wybraniu opcji.

## <a name="format-the-text-when-an-option-is-selected"></a>Formatowanie tekstu po wybraniu opcji
 W tej sekcji napiszesz kod, dzięki czemu gdy użytkownik wybierze opcję formatowania, format tekstu w arkuszu zostanie zmieniony.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Aby zmienić formatowanie, gdy pole wyboru jest zaznaczone

1. Kliknij prawym przyciskiem **myszy pozycję Arkusz1,** a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyBoldFont` pola wyboru:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet7":::

3. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyItalicFont` pola wyboru:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet8":::

4. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyUnderlineFont` pola wyboru:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet9":::

5. W języku C# należy dodać procedury obsługi zdarzeń dla pól wyboru do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzenia, jak pokazano poniżej. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create event handlers in Office projects (Jak utworzyć procedury obsługi zdarzeń w projektach pakietu Office).](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że tekst jest poprawnie sformatowany po zaznaczeniu lub wyczyszczeniu pola wyboru.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Zaznacz lub wyczyść pole wyboru.

3. Upewnij się, że tekst jest poprawnie sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy używania pól wyboru i formatowania tekstu w arkuszach programu Excel. Oto kilka zadań, które mogą się pojawić w następnej części:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz Deploy an Office solution by using ClickOnce (Wdrażanie [rozwiązania pakietu Office przy użyciu technologii ClickOnce).](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- Wypełnianie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie tekstu w polu tekstowym w [arkuszu przy użyciu przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
