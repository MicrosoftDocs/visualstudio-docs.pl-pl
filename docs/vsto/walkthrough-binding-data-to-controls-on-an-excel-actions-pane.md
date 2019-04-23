---
title: 'Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Excel'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3dc891c47042fe93ac6be8fa28c2967484c9d6c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050156"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Excel
  W tym instruktażu przedstawiono powiązanie danych z kontrolkami w okienku akcji programu Microsoft Office Excel. Formanty pokazują wzorzec/szczegół relacji między tabelami w bazie danych programu SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie formantów do arkusza.

- Tworzenie kontrolki okienka akcji.

- Dodawanie formantów formularzy Windows powiązane z danymi do kontrolki okienka akcji.

- Wyświetlane w okienku Akcje, gdy aplikacja zostanie otwarta.

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera z przykładową bazą danych Northwind programu SQL Server.

- Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.

## <a name="create-the-project"></a>Utwórz projekt
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje okienku akcji programu Excel**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje okienku akcji programu Excel** projekt **Eksploratora rozwiązań**.

## <a name="add-a-new-data-source-to-the-project"></a>Dodaj nowe źródło danych do projektu

### <a name="to-add-a-new-data-source-to-the-project"></a>Aby dodać nowe źródło danych do projektu

1. Jeśli **źródeł danych** okno nie jest widoczny, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.

2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz **bazy danych** a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.

5. Kliknij przycisk **Dalej**.

6. Usuń zaznaczenie opcji, aby zapisać połączenie, jeśli jest ono zaznaczone, a następnie kliknij **dalej**.

7. Rozwiń **tabel** w węźle **obiektów bazy danych** okna.

8. Zaznacz pole wyboru obok pozycji **dostawców** tabeli.

9. Rozwiń **produktów** tabeli, a następnie wybierz pozycję **ProductName**, **IDDostawcy**, **QuantityPerUnit**, i **UnitPrice**.

10. Kliknij przycisk **Zakończ**.

    Kreator dodaje **dostawców** tabeli i **produktów** do tabeli **źródeł danych** okna. Dodaje także typizowany zestaw danych do projektu, który jest widoczny w **Eksploratora rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Następnie dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i <xref:Microsoft.Office.Tools.Excel.ListObject> formant do pierwszego arkusza.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Aby dodać kontrolkę NamedRange i kontrolki ListObject

1. Upewnij się, że **Moje Pane.xlsx akcji programu Excel** skoroszyt jest otwarty w Projektancie Visual Studio za pomocą `Sheet1` wyświetlane.

2. W **źródeł danych** okna, rozwiń węzeł **dostawców** tabeli.

3. Kliknij strzałkę listy rozwijanej **nazwa firmy** węzłem, a następnie kliknij przycisk **NamedRange**.

4. Przeciągnij **nazwa firmy** z **źródeł danych** okna do komórki **A2** w `Sheet1`.

     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `CompanyNameNamedRange` zostanie utworzony, a tekst \<CompanyName > jest wyświetlana w komórce **A2**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `suppliersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.

5. W **źródeł danych** okna, przewiń w dół ostatnie kolumn, które podlegają **dostawców** tabeli. W dolnej części listy jest **produktów** tabeli; jest w tym miejscu, ponieważ jest elementem podrzędnym **dostawców** tabeli. Wybierz tę opcję, **produktów** tabeli nie ten, który znajduje się w tym samym poziomie co **dostawców** tabeli, a następnie kliknij strzałkę listy rozwijanej, która pojawia się.

6. Kliknij przycisk **ListObject** w listy rozwijanej, a następnie przeciągnij **produktów** tabeli do komórki **A6** w `Sheet1`.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `ProductNameListObject` jest tworzony w komórce **A6**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `productsBindingSource` i karty tabeli są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.

7. Dla C# tylko wybrać **suppliersBindingSource** w zasobniku składnika, a następnie zmień **Modyfikatory** właściwości **wewnętrzne** w **właściwości**  okna.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka akcji
 Następnie należy kontrolka okienka akcji, który ma pola kombi.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolki okienka akcji

1. Wybierz **Moje okienku akcji programu Excel** projektu w **Eksploratora rozwiązań**.

2. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **kontrolki okienka akcji**, nadaj jej nazwę **ActionsControl**i kliknij przycisk **Dodaj**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki formularzy Windows powiązane z danymi kontrolki okienka akcji

1. Z **wspólnych formantów** kart **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> kontrolki do kontrolki okienka akcji.

2. Zmiana **rozmiar** właściwości **171, 21**.

3. Zmień rozmiar kontrolki użytkownika do rozmiaru pola kombi.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Powiąż formant w okienku akcji z danymi
 W tej sekcji będziesz Ustaw źródło danych <xref:System.Windows.Forms.ComboBox> do tego samego źródła danych jako <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w arkuszu.

### <a name="to-set-data-binding-properties-of-the-control"></a>Aby ustawić właściwości powiązanie danych kontrolki

1. Kliknij prawym przyciskiem myszy kontrolki okienka akcji, a następnie kliknij przycisk **Wyświetl kod**.

2. Dodaj następujący kod do <xref:System.Windows.Forms.UserControl.Load> zdarzeń kontrolki okienka akcji.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. W C#, należy utworzyć program obsługi zdarzeń dla `ActionsControl`. Możesz umieścić ten kod w `ActionsControl` konstruktora. Aby uzyskać więcej informacji na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Pokaż okienko akcji
 W okienku Akcje nie są widoczne, do momentu dodania formantu w czasie wykonywania.

#### <a name="to-show-the-actions-pane"></a>Aby pokazać okienko akcji

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *ThisWorkbook.vb* lub *ThisWorkbook.cs*, a następnie kliknij przycisk **Wyświetl kod**.

2. Utwórz nowe wystąpienie kontrolki użytkownika w `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. W <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> program obsługi zdarzeń `ThisWorkbook`, Dodaj formant do okienka działań.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można przetestować dokumencie, aby sprawdzić, czy po otwarciu dokumentu zostanie otwarte okienko akcji i czy formanty mają relacji wzorzec/szczegół.

### <a name="to-test-your-document"></a>Aby przetestować dokumentu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Upewnij się, że widoczne jest okienko akcji.

3. Wybierz firmę, w polu listy. Sprawdź, czy nazwa firmy jest wyświetlana w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i że są wyświetlane szczegóły produktu <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli.

4. Wybierz różnych firm, aby sprawdzić nazwę firmy, a następnie odpowiednio zmienić szczegóły produktu.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Powiązanie danych z kontrolkami w programie Word. Aby uzyskać więcej informacji, zobacz [instruktażu: Wiązanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Zobacz także
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Instrukcje: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
