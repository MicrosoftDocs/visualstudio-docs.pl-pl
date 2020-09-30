---
title: 'Przewodnik: program dla zdarzeń kontrolki NamedRange'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e5ce12e2de8274afd2c27d4ece36529563a6386
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584940"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Przewodnik: program dla zdarzeń kontrolki NamedRange
  W tym instruktażu pokazano, jak dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do Microsoft Office arkusza i programu Excel z jego zdarzeń przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W tym instruktażu dowiesz się, jak:

- Dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do arkusza.

- Program przed <xref:Microsoft.Office.Tools.Excel.NamedRange> zdarzeniami kontroli.

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

1. Utwórz projekt skoroszytu programu Excel z nazwą **Moje nazwane zdarzenia zakresu**. Upewnij się, że wybrano **Utwórz nowy dokument** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje do **Eksplorator rozwiązań**projekt **Moje nazwane zdarzenia zakresu** .

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Dodaj tekst i nazwane zakresy do arkusza
 Ponieważ formanty hosta są rozszerzonymi obiektami pakietu Office, można je dodać do dokumentu w taki sam sposób, jak dodać obiekt macierzysty. Na przykład można dodać kontrolkę programu Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> do arkusza, otwierając menu **Wstaw** , wskazując **nazwę**i wybierając **Definiuj**. Możesz również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formant, przeciągając go z **przybornika** do arkusza.

 W tym kroku dodasz dwie kontrolki z nazwanymi zakresami do arkusza za pomocą **przybornika**, a następnie dodasz tekst do arkusza.

### <a name="to-add-a-range-to-your-worksheet"></a>Aby dodać zakres do arkusza

1. Upewnij się, że skoroszyt *mój nazwany zakres Events.xlsx* jest otwarty w projektancie programu Visual Studio z `Sheet1` wyświetlonym poleceniem.

2. Na karcie **formanty programu Excel** przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do komórki **a1** w `Sheet1` .

     Pojawi się okno dialogowe **Dodaj kontrolkę NamedRange** .

3. Sprawdź, czy **$A $1** pojawia się w edytowalnym polu tekstowym, a komórka **a1** jest zaznaczona. Jeśli tak nie jest, kliknij komórkę **a1** , aby ją zaznaczyć.

4. Kliknij przycisk **OK**.

     Komórka **a1** otrzymuje zakres o nazwie `namedRange1` . W arkuszu nie ma widocznych wskazań, ale `namedRange1` pojawia się w polu **Nazwa** (znajdującym się tuż nad arkuszem po lewej stronie), gdy jest zaznaczona komórka **a1** .

5. Dodaj kolejną <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do komórki **B3**.

6. Sprawdź, czy **$B $3** pojawia się w edytowalnym polu tekstowym, a następnie wybierz komórkę **B3** . Jeśli tak nie jest, kliknij komórkę **B3** , aby ją zaznaczyć.

7. Kliknij przycisk **OK**.

     Komórka **B3** jest zakresem o nazwie `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Aby dodać tekst do arkusza

1. W komórce **a1**wpisz następujący tekst:

    **Jest to przykład kontrolki NamedRange.**

2. W komórce **a3** (po lewej stronie `namedRange2` ) wpisz następujący tekst:

    **Wydarzeniach**

   W poniższych sekcjach napiszesz kod, który wstawia tekst do `namedRange2` i modyfikuje właściwości `namedRange2` kontrolki w odpowiedzi na <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenia, i <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Dodaj kod odpowiadający zdarzeniu BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Aby wstawić tekst do NamedRange2 na podstawie zdarzenia BeforeDoubleClick

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Arkusz1. vb** lub **Sheet1.cs** i wybierz polecenie **Wyświetl kod**.

2. Dodaj kod, aby `namedRange1_BeforeDoubleClick` program obsługi zdarzeń wyglądał następująco:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. W języku C# należy dodać procedury obsługi zdarzeń dla nazwanego zakresu, jak pokazano w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> poniższym zdarzeniu. Aby uzyskać informacje dotyczące tworzenia programów obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Dodaj kod, aby odpowiedzieć na zdarzenie zmiany

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Aby wstawić tekst do namedRange2 na podstawie zdarzenia zmiany

1. Dodaj kod, aby `NamedRange1_Change` program obsługi zdarzeń wyglądał następująco:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Ponieważ dwukrotne kliknięcie komórki w zakresie programu Excel spowoduje przejście do trybu edycji, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie występuje, gdy zaznaczenie jest przenoszone poza zakres nawet wtedy, gdy nie wystąpiły żadne zmiany w tekście.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Dodaj kod odpowiadający zdarzeniu SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Aby wstawić tekst do namedRange2 na podstawie zdarzenia SelectionChange

1. Dodaj kod, aby program obsługi zdarzeń **NamedRange1_SelectionChange** wyglądał następująco:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Ponieważ dwukrotne kliknięcie komórki w zakresie programu Excel powoduje przeniesienie zaznaczenia do zakresu, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenie występuje przed <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> wystąpieniem zdarzenia.

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować skoroszyt, aby sprawdzić, czy tekst opisujący zdarzenia <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki został wstawiony do innego nazwanego zakresu, gdy zdarzenia są zgłaszane.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Umieść kursor w obszarze `namedRange1` i sprawdź, czy tekst dotyczący <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenia jest wstawiany i czy komentarz jest wstawiany do arkusza.

3. Kliknij dwukrotnie wewnątrz `namedRange1` i sprawdź, czy tekst dotyczący <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> zdarzeń jest wstawiany z czerwonym kursywą w tekście `namedRange2` .

4. Kliknij poza `namedRange1` i pamiętaj, że zdarzenie zmiany występuje podczas kończenia trybu edycji, nawet jeśli nie wprowadzono zmiany w tekście.

5. Zmień tekst w `namedRange1` .

6. Kliknij poza `namedRange1` i sprawdź, czy w polu tekst dotyczący <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenia jest wstawiany niebieski tekst `namedRange2` .

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące programowania względem zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki. Oto zadanie, które może się pojawić w następnej kolejności:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
