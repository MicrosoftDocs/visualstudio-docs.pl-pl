---
title: 'Przewodnik: zbieranie danych przy użyciu formularza systemu Windows'
description: Otwórz formularz systemu Windows na podstawie dostosowania na poziomie dokumentu dla programu Microsoft Excel, Zbierz informacje od użytkownika i Zapisz te informacje w komórce arkusza.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e8c88bbf529da8e07976c012d40ca59e5f1e5626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920372"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Przewodnik: zbieranie danych przy użyciu formularza systemu Windows
  W tym instruktażu pokazano, jak otworzyć formularz systemu Windows na podstawie dostosowania na poziomie dokumentu dla Microsoft Office Excel, zebrać informacje od użytkownika i zapisać te informacje w komórce arkusza.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Chociaż w tym instruktażu jest stosowany projekt na poziomie dokumentu dla programu Excel, koncepcje przedstawione w tym przewodniku dotyczą innych projektów pakietu Office.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **WinFormInput**, a następnie wybierz pozycję **Utwórz nowy dokument** w kreatorze. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **WinFormInput** do **Eksplorator rozwiązań**.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Dodaj kontrolkę NamedRange do arkusza

### <a name="to-add-a-named-range-to-sheet1"></a>Aby dodać nazwany zakres do Arkusz1

1. Zaznacz komórkę **a1** na `Sheet1` .

2. W polu **Nazwa** wpisz **formInput**.

     Pole **Nazwa** znajduje się po lewej stronie paska formuły, po prostu powyżej kolumny **A** arkusza.

3.  Naciśnij klawisz **Enter**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Kontrolka jest dodawana do komórki **a1**. W arkuszu nie ma widocznych wskazań, ale **formInput** pojawia się w polu **Nazwa** (tuż nad arkuszem po lewej stronie) i w oknie **Właściwości** , gdy zaznaczona jest komórka **a1** .

## <a name="add-a-windows-form-to-the-project"></a>Dodawanie formularza systemu Windows do projektu
 Utwórz formularz systemu Windows, aby monitować użytkownika o informacje.

### <a name="to-add-a-windows-form"></a>Aby dodać formularz systemu Windows

1. Wybierz projekt **WinFormInput** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj formularz systemu Windows**.

3. Nadaj nazwę formularzowi **GetInputString. vb** lub **GetInputString.cs**, a następnie kliknij przycisk **Dodaj**.

    Nowy formularz zostanie otwarty w projektancie.

4. Dodaj <xref:System.Windows.Forms.TextBox> a i a <xref:System.Windows.Forms.Button> do formularza.

5. Wybierz przycisk, Znajdź **tekst** właściwości w oknie **Właściwości** , a następnie Zmień tekst na **OK**.

   Następnie Dodaj kod do `ThisWorkbook.vb` lub `ThisWorkbook.cs` , aby zebrać informacje o użytkowniku.

## <a name="display-the-windows-form-and-collecting-information"></a>Wyświetlanie formularza systemu Windows i zbieranie informacji
 Utwórz wystąpienie `GetInputString` formularza systemu Windows i Wyświetl je, a następnie Zapisz informacje o użytkowniku w komórce w arkuszu.

#### <a name="to-display-the-form-and-collect-information"></a>Aby wyświetlić formularz i zebrać informacje

1. Kliknij prawym przyciskiem myszy **ThisWorkbook. vb** lub **ThisWorkbook.cs** w **Eksplorator rozwiązań**, a następnie kliknij przycisk **Wyświetl kod**.

2. W programie <xref:Microsoft.Office.Tools.Excel.Workbook.Open> obsługi zdarzeń programu `ThisWorkbook` Dodaj następujący kod, aby zadeklarować zmienną dla formularza, `GetInputString` a następnie Pokaż formularz.

   > [!NOTE]
   > W języku C# należy dodać procedurę obsługi zdarzeń, jak pokazano w <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> poniższym zdarzeniu. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]

3. Utwórz metodę o nazwie `WriteStringToCell` , która zapisuje tekst w nazwanym zakresie. Ta metoda jest wywoływana z formularza, a dane wejściowe użytkownika są przesyłane do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, `formInput` w komórce **a1**.

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]

   Następnie Dodaj kod do formularza, aby obsłużyć zdarzenie kliknięcia przycisku.

## <a name="send-information-to-the-worksheet"></a>Wyślij informacje do arkusza

### <a name="to-send-information-to-the-worksheet"></a>Aby wysłać informacje do arkusza

1. Kliknij prawym przyciskiem myszy pozycję **GetInputString** w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Projektant widoków**.

2. Kliknij dwukrotnie przycisk, aby otworzyć plik kodu z <xref:System.Windows.Forms.Control.Click> dodaną obsługą zdarzeń przycisku.

3. Dodaj kod do programu obsługi zdarzeń, aby przyjmować dane wejściowe z pola tekstowego, wyślij je do funkcji `WriteStringToCell` , a następnie zamknij formularz.

     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]

## <a name="test"></a>Testowanie
 Teraz można uruchomić projekt. Zostanie wyświetlony formularz systemu Windows, a dane wejściowe pojawią się w arkuszu.

### <a name="to-test-your-workbook"></a>Aby przetestować skoroszyt

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że zostanie wyświetlony formularz systemu Windows.

3. Wpisz **Hello World** w polu tekstowym, a następnie kliknij przycisk **OK**.

4. Upewnij się, że **Hello World** pojawia się w komórce **a1** arkusza.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące wyświetlania formularza systemu Windows i przekazywania danych do arkusza. Inne zadania, które można wykonać, obejmują:

- Użyj formantów Windows Forms w skoroszycie programu Excel lub dokumencie programu Word. Aby uzyskać więcej informacji, zobacz [Windows Forms kontrolki w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Zmodyfikuj interfejs użytkownika aplikacji Microsoft Office na podstawie dostosowania na poziomie dokumentu lub dodatku VSTO. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
