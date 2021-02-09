---
title: 'Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Excel'
description: Powiąż dane z kontrolkami w okienku Akcje w programie Microsoft Excel. Kontrolki ilustrują relację wzorzec/szczegóły między tabelami w bazie danych SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75df7a3a9ddfa6009b0002bfe83b57f2d91e6e0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906558"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Excel
  W tym instruktażu przedstawiono powiązanie danych z kontrolkami w okienku Akcje w programie Microsoft Office Excel. Kontrolki ilustrują relację wzorzec/szczegóły między tabelami w bazie danych SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie formantów do arkusza.

- Tworzenie kontrolki okienka akcji.

- Dodawanie formantów Windows Forms powiązanych z danymi do kontrolki okienka akcji.

- Wyświetlanie okienka Akcje po otwarciu aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera za pomocą przykładowej bazy danych Northwind SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych SQL Server.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel za pomocą **okienka nazwa moje działania w programie Excel**. W kreatorze wybierz pozycję **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **okienka Akcje programu Excel** do **Eksplorator rozwiązań**.

## <a name="add-a-new-data-source-to-the-project"></a>Dodaj nowe źródło danych do projektu

### <a name="to-add-a-new-data-source-to-the-project"></a>Aby dodać nowe źródło danych do projektu

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Kliknij przycisk **Dalej**.

6. Usuń zaznaczenie opcji Zapisz połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **tabele** w oknie **obiekty bazy danych** .

8. Zaznacz pole wyboru obok tabeli **dostawcy** .

9. Rozwiń tabelę **Products (produkty** ) i wybierz pozycję **ProductName**, **IDDostawcy**, **QuantityPerUnit** i **CenaJednostkowa**.

10. Kliknij przycisk **Finish** (Zakończ).

    Kreator dodaje tabelę tabele i **produkty** **dostawcy** do okna **źródła danych** . Dodaje również typ DataSet do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Następnie Dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę i <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę do pierwszego arkusza.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Aby dodać formant NamedRange i formant ListObject

1. Sprawdź, czy w projektancie programu Visual Studio jest otwarty skoroszyt **Pane.xlsxakcje w programie Excel** `Sheet1` .

2. W oknie **źródła danych** Rozwiń tabelę **dostawcy** .

3. Kliknij strzałkę listy rozwijanej w węźle **Nazwa firmy** , a następnie kliknij pozycję **NamedRange**.

4. Przeciągnij **nazwę firmy** z okna **źródła danych** do komórki **a2** w `Sheet1` .

     Zostanie <xref:Microsoft.Office.Tools.Excel.NamedRange> utworzona kontrolka o nazwie `CompanyNameNamedRange` , a tekst \<CompanyName> pojawia się w komórce **a2**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `suppliersBindingSource` , karta tabeli i a <xref:System.Data.DataSet> są dodawane do projektu. Formant jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z <xref:System.Data.DataSet> wystąpieniem.

5. W oknie **źródła danych** przewiń w dół do kolumn znajdujących się w tabeli **dostawcy** . W dolnej części listy znajduje się tabela **Products (produkty** ). jest to możliwe, ponieważ jest elementem podrzędnym tabeli **dostawcy** . Wybierz tabelę **produkty** , a nie tę, która znajduje się na tym samym poziomie co tabela **dostawcy** , a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Na liście rozwijanej kliknij pozycję **Lista** , a następnie przeciągnij tabelę **Products** do komórki **a6** w `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject> `ProductNameListObject` W komórce **a6** zostanie utworzony formant o nazwie. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `productsBindingSource` i adapter tabeli są dodawane do projektu. Formant jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z <xref:System.Data.DataSet> wystąpieniem.

7. W przypadku języka C# wybierz pozycję **suppliersBindingSource** na pasku składnika i zmień właściwość **Modyfikatory** na **Internal** w oknie **Właściwości** .

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka Akcje
 Następnie potrzebujesz formantu okienka akcji, który ma pole kombi.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **okienka Akcje programu Excel** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **kontrolka okienka akcji**, nadaj jej nazwę **ActionsControl**, a następnie kliknij przycisk **Dodaj**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki Windows Forms powiązane z danymi do kontrolki okienka akcji

1. Na kartach **Formanty standardowe** **przybornika** przeciągnij <xref:System.Windows.Forms.ComboBox> kontrolkę do okienka Akcje.

2. Zmień właściwość **size** na **171, 21**.

3. Zmień rozmiar kontrolki użytkownika, aby dopasować ją do pola kombi.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Powiązywanie kontrolki w okienku Akcje z danymi
 W tej sekcji ustawisz źródło danych dla tego <xref:System.Windows.Forms.ComboBox> samego źródła danych co <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w arkuszu.

### <a name="to-set-data-binding-properties-of-the-control"></a>Aby ustawić właściwości powiązania danych formantu

1. Kliknij prawym przyciskiem myszy kontrolkę okienko akcji, a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujący kod do <xref:System.Windows.Forms.UserControl.Load> zdarzenia kontrolki okienko akcji.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. W języku C# należy utworzyć procedurę obsługi zdarzeń dla `ActionsControl` . Ten kod można umieścić w `ActionsControl` konstruktorze. Aby uzyskać więcej informacji na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Pokaż okienko akcje
 Okienko akcje nie jest widoczne, dopóki nie dodasz kontrolki w czasie wykonywania.

#### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcje

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy *ThisWorkbook. vb* lub *ThisWorkbook.cs*, a następnie kliknij polecenie **Wyświetl kod**.

2. Utwórz nowe wystąpienie kontrolki użytkownika w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. W programie <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> obsługi zdarzeń programu `ThisWorkbook` Dodaj kontrolkę do okienka Akcje.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można przetestować dokument, aby sprawdzić, czy okienko akcje otwiera się po otwarciu dokumentu oraz czy kontrolki mają relację główną/szczegółową.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że okienko akcje jest widoczne.

3. Wybierz firmę w polu listy. Sprawdź, czy nazwa firmy jest wymieniona w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolce i czy szczegóły produktu są wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolce.

4. Wybierz różne firmy, aby sprawdzić, czy nazwa firmy i szczegóły produktu są odpowiednie.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Powiązywanie danych z kontrolkami w programie Word. Aby uzyskać więcej informacji, zobacz [Przewodnik: powiązywanie danych z kontrolkami w okienku Akcje programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Zobacz też
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Instrukcje: zarządzanie układem sterowania w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
