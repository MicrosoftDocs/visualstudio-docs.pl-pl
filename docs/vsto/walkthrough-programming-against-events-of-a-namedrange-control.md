---
title: 'Przewodnik: Program w odniesieniu do zdarzeń formantu NamedRange'
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
ms.openlocfilehash: dee6c5dadb1634f384fd04d67cb0701b2e972799
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049935"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Przewodnik: Program w odniesieniu do zdarzeń formantu NamedRange
  W tym instruktażu przedstawiono sposób dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolę do arkusza programu Microsoft Office Excel i programowanie ze zdarzeniami przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Z tego instruktażu dowiesz się jak:

- Dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza.

- Programować przy użyciu <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować zdarzenia.

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

1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje zdarzenia zakresu o nazwie**. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje zdarzenia zakresu o nazwie** projekt **Eksploratora rozwiązań**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Dodawanie tekstu i nazwanych zakresów do arkusza
 Ponieważ formanty hosta są rozszerzonych obiektów pakietu Office, możesz je dodać do dokumentu w taki sam sposób możesz dodać obiekt natywny. Na przykład można dodać programu Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza, otwierając **Wstaw** menu, wskazać polecenie **nazwa**i wybierając pozycję **Definiuj**. Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, przeciągając go z **przybornika** do arkusza.

 W tym kroku dodasz dwóch kontrolek nazwanych zakresów do arkusza za pomocą **przybornika**, a następnie dodaj tekst do arkusza.

### <a name="to-add-a-range-to-your-worksheet"></a>Aby dodać zakres do arkusza

1. Upewnij się, że *Events.xlsx zakresu o nazwie My* skoroszyt jest otwarty w Projektancie Visual Studio za pomocą `Sheet1` wyświetlane.

2. Z **kontrolki programu Excel** kartę przybornika przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę komórki **A1** w `Sheet1`.

     **Dodaj kontrolkę NamedRange** pojawi się okno dialogowe.

3. Upewnij się, że **$A$ 1** pojawia się w polu tekst do edycji, a tej komórki **A1** jest zaznaczone. Jeśli nie, kliknij pozycję komórki **A1** aby go zaznaczyć.

4. Kliknij przycisk **OK**.

     Komórka **A1** staje się zakres o nazwie `namedRange1`. Nie ma żadnego wskazania widoczne w arkuszu, ale `namedRange1` pojawia się w **nazwa** pole (znajdujące się tuż nad arkusz po lewej stronie) gdy komórka **A1** wybrano.

5. Dodaj kolejną <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę komórki **B3**.

6. Upewnij się, że **$B$ 3** pojawia się w polu tekst do edycji, a tej komórki **B3** jest zaznaczone. Jeśli nie, kliknij pozycję komórki **B3** aby go zaznaczyć.

7. Kliknij przycisk **OK**.

     Komórka **B3** staje się zakres o nazwie `namedRange2`.

### <a name="to-add-text-to-your-worksheet"></a>Aby dodać tekst do arkusza

1. W komórce **A1**, wpisz następujący tekst:

    **Jest to przykład kontrolki NamedRange.**

2. W komórce **A3** (po lewej stronie `namedRange2`), wpisz następujący tekst:

    **Zdarzenia:**

   W poniższych sekcjach, trzeba napisać kod, który wstawia tekst do `namedRange2` i modyfikuje właściwości `namedRange2` formant w odpowiedzi na <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, i <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenia `namedRange1`.

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Dodaj kod w celu zareagowania na zdarzenie BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Aby wstawić tekst na NamedRange2 na podstawie zdarzeń BeforeDoubleClick

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs** i wybierz **Wyświetl kod**.

2. Dodaj kod, więc `namedRange1_BeforeDoubleClick` program obsługi zdarzeń wygląda podobnie do następującej:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. W języku C#, należy dodać procedury obsługi zdarzeń dla zakresu o nazwie, jak pokazano na <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> poniższe zdarzenie. Aby uzyskać informacje na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Dodaj kod, aby reagować na zdarzenia zmiany

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Aby wstawić tekst na namedRange2 na podstawie zdarzeń zmiany

1. Dodaj kod, więc `NamedRange1_Change` program obsługi zdarzeń wygląda podobnie do następującej:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    >  Ponieważ dwukrotnie komórkę w zakresie programu Excel przejdzie do trybu edycji, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie występuje, gdy wybór zostanie przeniesiony poza zakresem, nawet wtedy, gdy wystąpił brak zmian do tekstu.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Dodaj kod, aby odpowiedzieć na SelectionChange, zdarzenie

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Aby wstawić tekst na namedRange2 w oparciu o SelectionChange, zdarzenie

1. Dodaj kod, więc **NamedRange1_SelectionChange** programu obsługi zdarzeń wygląda podobnie do następującej:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    >  Dwukrotne kliknięcie komórki w zakresie programu Excel powoduje, że zaznaczenie, aby przenieść do zakresu, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> zdarzenie występuje przed <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> wystąpi zdarzenie.

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszytu, aby zweryfikować ten tekst opisem zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki są wstawiane do innego nazwany zakres, gdy zdarzenia są wywoływane.

### <a name="to-test-your-document"></a>Aby przetestować dokumentu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Umieść kursor w `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> dodaje zdarzenie, a komentarz zostaną wstawione do arkusza.

3. Kliknij dwukrotnie wewnątrz `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> zdarzeń dodaje się czerwony tekst kursywą w `namedRange2`.

4. Kliknij poza `namedRange1` i zwróć uwagę, że zdarzenia zmiany występuje podczas zamykania trybu edycji, nawet jeśli nie zmiany w tekście.

5. Zmienianie tekstu w `namedRange1`.

6. Kliknij poza `namedRange1`i sprawdź, czy tekst dotyczące <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzeń dodaje się z niebieski tekst pod `namedRange2`.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawowe informacje dotyczące programowania w odniesieniu do zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli. W tym polu jest zadaniem, które mogą pochodzić dalej:

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
