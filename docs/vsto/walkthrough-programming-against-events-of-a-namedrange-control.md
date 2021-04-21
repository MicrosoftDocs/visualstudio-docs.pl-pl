---
title: 'Przewodnik: programowanie względem zdarzeń kontrolki NamedRange'
description: Dowiedz się, jak dodać kontrolkę NamedRange do arkusza programu Microsoft Excel i programu względem jej zdarzeń przy użyciu narzędzi programistyki pakietu Office w programie Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec1c670867fae277a3c3c8290cd34d0d4be7ddf3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824968"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Przewodnik: programowanie względem zdarzeń kontrolki NamedRange
  W tym przewodniku pokazano, jak dodać kontrolkę do arkusza programu Excel i Microsoft Office programu dla jego zdarzeń przy użyciu narzędzi programistyczych pakietu Office w <xref:Microsoft.Office.Tools.Excel.NamedRange> programie Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W ramach tego przewodnika dowiesz się, jak:

- Dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do arkusza.

- Programowanie względem <xref:Microsoft.Office.Tools.Excel.NamedRange> zdarzeń sterujących.

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

1. Utwórz projekt skoroszytu programu Excel o nazwie **My Named Range Events (Moje nazwane zdarzenia zakresu).** Upewnij się, **że wybrano opcję Utwórz** nowy dokument. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt My Named Range Events (Moje **nazwane** zdarzenia **zakresu) do Eksplorator rozwiązań**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Dodawanie tekstu i nazwanych zakresów do arkusza
 Ponieważ kontrolki hosta są rozszerzonymi obiektami pakietu Office, można je dodać do dokumentu w taki sam sposób, jak w przypadku dodawania obiektu macierzystego. Na przykład możesz dodać kontrolkę programu Excel do arkusza, otwierając menu Wstaw, wybierając pozycję Nazwa <xref:Microsoft.Office.Tools.Excel.NamedRange> i wybierając pozycję **Definiuj**.   Możesz również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, przeciągając  ją z przybornika do arkusza.

 W tym kroku dodasz dwie nazwane kontrolki zakresu do arkusza przy użyciu przybornika **,** a następnie dodasz tekst do arkusza.

### <a name="to-add-a-range-to-your-worksheet"></a>Aby dodać zakres do arkusza

1. Sprawdź, czy *skoroszyt mój nazwany Events.xlsx* zakres jest otwarty w Visual Studio aplikacji z `Sheet1` wyświetlonym komunikatem .

2. Na karcie **Kontrolki programu Excel** przybornika przeciągnij kontrolkę do <xref:Microsoft.Office.Tools.Excel.NamedRange> komórki **A1** w obszarze `Sheet1` .

     Zostanie **wyświetlone okno dialogowe Dodawanie kontrolki NamedRange.**

3. Sprawdź, **$A 1** USD pojawia się w edytowalnym polu tekstowym i czy komórka **A1** jest zaznaczona. Jeśli tak nie jest, kliknij **komórkę A1,** aby ją zaznaczyć.

4. Kliknij przycisk **OK**.

     Komórka **A1 staje** się zakresem o nazwie `namedRange1` . Nie ma widocznego wskazania w arkuszu, ale pojawia się w polu Nazwa (tuż nad arkuszem po lewej stronie), gdy komórka `namedRange1` **A1** jest  zaznaczona.

5. Dodaj kolejną <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do komórki **B3**.

6. Sprawdź, **$B 3 USD** pojawia się w edytowalnym polu tekstowym i czy komórka **B3** jest zaznaczona. Jeśli tak nie jest, kliknij komórkę **B3,** aby ją zaznaczyć.

7. Kliknij przycisk **OK**.

     Komórka **B3** staje się zakresem o nazwie `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Aby dodać tekst do arkusza

1. W **komórce A1** wpisz następujący tekst:

    **Jest to przykład kontrolki NamedRange.**

2. W **komórce A3** (z lewej strony tabeli `namedRange2` ) wpisz następujący tekst:

    **Zdarzenia:**

   W poniższych sekcjach napiszesz kod, który wstawia tekst do kontrolki i modyfikuje jej właściwości w odpowiedzi na zdarzenia `namedRange2` `namedRange2` , i <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Dodawanie kodu w celu reagowania na zdarzenie BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Aby wstawić tekst do NamedRange2 na podstawie zdarzenia BeforeDoubleClick

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Sheet1.vb** lub **Sheet1.cs** i wybierz **polecenie Wyświetl kod.**

2. Dodaj kod, aby `namedRange1_BeforeDoubleClick` procedura obsługi zdarzeń wyglądała następująco:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. W języku C# należy dodać procedury obsługi zdarzeń dla nazwanego zakresu, jak pokazano w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> poniższym zdarzeniu. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create event handlers in Office projects (Jak utworzyć procedury obsługi zdarzeń w projektach pakietu Office).](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Dodawanie kodu w celu reagowania na zdarzenie zmiany

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Aby wstawić tekst do namedRange2 na podstawie zmiany zdarzenia

1. Dodaj kod, aby `NamedRange1_Change` procedura obsługi zdarzeń wyglądała następująco:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Ponieważ dwukrotne kliknięcie komórki w zakresie programu Excel przechodzi w tryb edycji, zdarzenie występuje, gdy zaznaczenie zostanie przeniesione poza zakres, nawet jeśli nie <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> nastąpiły żadne zmiany tekstu.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Dodawanie kodu w celu reagowania na zdarzenie SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Aby wstawić tekst do namedRange2 na podstawie zdarzenia SelectionChange

1. Dodaj kod, aby **NamedRange1_SelectionChange** obsługi zdarzeń wygląda następująco:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Ponieważ dwukrotne kliknięcie komórki w zakresie programu Excel powoduje przejście zaznaczenia do zakresu, przed zdarzeniem wystąpi <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> zdarzenie.

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby sprawdzić, czy tekst opisujący zdarzenia kontrolki jest wstawiany do innego nazwanego zakresu po <xref:Microsoft.Office.Tools.Excel.NamedRange> złożeniu zdarzeń.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Umieść kursor w i sprawdź, czy tekst dotyczący zdarzenia został wstawiony i czy komentarz został `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> wstawiony do arkusza.

3. Kliknij dwukrotnie wewnątrz i sprawdź, czy tekst dotyczący zdarzeń jest wstawiany z czerwonym `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> kursywą w . `namedRange2`

4. Kliknij poza polem i zwróć uwagę, że zdarzenie zmiany występuje podczas zamykania trybu edycji, mimo że nie `namedRange1` w tekście wnoszono żadnych zmian.

5. Zmień tekst w ciągu `namedRange1` .

6. Kliknij poza , a następnie sprawdź, czy tekst dotyczący zdarzenia został wstawiony `namedRange1` z niebieskim tekstem do <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> . `namedRange2`

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy programowania dla zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki. Oto zadanie, które może zostać następne:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [How to: Resize NamedRange controls (2017: Zmienianie rozmiaru kontrolek NamedRange)](../vsto/how-to-resize-namedrange-controls.md)
- [2017: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [How to: Create event handlers in Office projects (Tworzyć procedury obsługi zdarzeń w projektach pakietu Office)](../vsto/how-to-create-event-handlers-in-office-projects.md)
