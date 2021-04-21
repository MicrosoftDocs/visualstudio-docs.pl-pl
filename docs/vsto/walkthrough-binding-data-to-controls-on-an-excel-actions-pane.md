---
title: 'Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Excel'
description: Wiązanie danych z kontrolkami w okienku akcji w programie Microsoft Excel. Kontrolki pokazują relację wzorzec/szczegół między tabelami w SQL Server danych.
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
ms.openlocfilehash: 377c3405211c91712f8754131d8379c3dae7e820
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824552"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Excel
  W tym przewodniku pokazano powiązanie danych z kontrolkami w okienku akcji w Microsoft Office Excel. Kontrolki pokazują relację wzorzec/szczegół między tabelami w SQL Server danych.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie kontrolek do arkusza.

- Tworzenie kontrolki okienka akcji.

- Dodawanie kontrolek Windows Forms powiązanych z danymi do kontrolki okienka akcji.

- Wyświetlanie okienka akcji po otworze aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do serwera przy użyciu bazy danych Northwind SQL Server przykładowej bazy danych.

- Uprawnienia do odczytu i zapisu w SQL Server danych.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **My Excel Actions Pane (Okienko akcji programu Excel).** W kreatorze wybierz **pozycję Utwórz nowy dokument.** Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **Okienko akcji** programu Excel do Eksplorator rozwiązań **.**

## <a name="add-a-new-data-source-to-the-project"></a>Dodawanie nowego źródła danych do projektu

### <a name="to-add-a-new-data-source-to-the-project"></a>Aby dodać nowe źródło danych do projektu

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

2. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Wybierz **pozycję Baza danych,** a następnie kliknij **przycisk Dalej.**

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub dodaj nowe połączenie przy użyciu **przycisku Nowe** połączenie.

5. Kliknij przycisk **Dalej**.

6. Wyczyść opcję zapisania połączenia, jeśli jest zaznaczone, a następnie kliknij przycisk **Dalej.**

7. Rozwiń **węzeł Tabele** w **oknie Obiekty bazy** danych.

8. Zaznacz pole wyboru obok tabeli **Suppliers (Dostawcy).**

9. Rozwiń **tabelę Products** i wybierz **pozycję ProductName**, **SupplierID,** **QuantityPerUnit** i **UnitPrice.**

10. Kliknij przycisk **Finish** (Zakończ).

    Kreator dodaje **tabelę Suppliers (Dostawcy)** **i Products (Produkty)** do **okna Źródła** danych. Dodaje również typowany zestaw danych do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 Następnie dodaj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę i <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę do pierwszego arkusza.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Aby dodać kontrolkę NamedRange i kontrolkę ListObject

1. Sprawdź, czy **skoroszyt Moje akcje programu Excel Pane.xlsx** jest otwarty w projektancie Visual Studio, z `Sheet1` wyświetlonym komunikatem .

2. W **oknie Źródła** danych rozwiń **tabelę Suppliers (Dostawcy).**

3. Kliknij strzałkę listy rozwijanej w **węźle Nazwa firmy,** a następnie kliknij pozycję **NamedRange .**

4. Przeciągnij **ciąg Nazwa firmy** z okna Źródła **danych** do komórki **A2 w** pliku `Sheet1` .

     Zostanie <xref:Microsoft.Office.Tools.Excel.NamedRange> utworzona `CompanyNameNamedRange` kontrolka o nazwie , a tekst pojawi \<CompanyName> się w **komórce A2**. W tym samym czasie do projektu <xref:System.Windows.Forms.BindingSource> są dodawane nazwane `suppliersBindingSource` , adapter tabeli i <xref:System.Data.DataSet> . Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource> , która z kolei jest powiązana z <xref:System.Data.DataSet> wystąpieniem .

5. W **oknie Źródła** danych przewiń w dół za kolumnami, które znajdują się w **tabeli Suppliers.** W dolnej części listy znajduje się tabela **Products.** Jest to tutaj, ponieważ jest to podwłasny **tabeli Suppliers.** Wybierz tę **tabelę** Products (Produkty), a nie tę, która znajduje się na tym samym poziomie co tabela **Suppliers** (Dostawcy), a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Kliknij **pozycję ListObject** na liście rozwijanej, a następnie przeciągnij **tabelę Products** do komórki **A6** w . `Sheet1`

     Kontrolka <xref:Microsoft.Office.Tools.Excel.ListObject> o `ProductNameListObject` nazwie jest tworzona w **komórce A6**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> `productsBindingSource` nazwana karta i karta tabeli są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource> , która z kolei jest powiązana z <xref:System.Data.DataSet> wystąpieniem .

7. Tylko w przypadku języka C# wybierz **pozycję suppliersBindingSource** na pasku składników i zmień właściwość **Modyfikatory** na **Wewnętrzna** w **oknie** Właściwości.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka akcji
 Następnie potrzebna jest kontrolka okienka akcji z polem kombi.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **Okienko akcji programu Excel** w **Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **Kontrolka okienka Akcje,** nadaj jej nazwę **ActionsControl** i kliknij przycisk **Dodaj**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Aby dodać kontrolki powiązane z Windows Forms do kontrolki okienka akcji

1. Na **kartach Typowe kontrolki** **przybornika** przeciągnij <xref:System.Windows.Forms.ComboBox> kontrolkę do kontrolki okienka akcji.

2. Zmień właściwość **Size** na **171, 21**.

3. Zmień rozmiar kontrolki użytkownika, aby dopasować pole kombi.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Wiązanie kontrolki w okienku akcji z danymi
 W tej sekcji ustawisz źródło danych na to samo źródło danych co <xref:System.Windows.Forms.ComboBox> <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolka w arkuszu.

### <a name="to-set-data-binding-properties-of-the-control"></a>Aby ustawić właściwości powiązania danych kontrolki

1. Kliknij prawym przyciskiem myszy kontrolkę okienka akcji, a następnie kliknij polecenie **Wyświetl kod.**

2. Dodaj następujący kod do zdarzenia <xref:System.Windows.Forms.UserControl.Load> kontrolki okienka akcji.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet1":::

3. W języku C# należy utworzyć program obsługi zdarzeń dla `ActionsControl` . Ten kod można umieścić w `ActionsControl` konstruktorze. Aby uzyskać więcej informacji na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet2":::

## <a name="show-the-actions-pane"></a>Wyświetlanie okienka akcji
 Okienko akcji nie jest widoczne, dopóki nie dodasz kontrolki w czasie uruchamiania.

#### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcji

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy *pozycję ThisWorkbook.vb* lub *ThisWorkbook.cs,* a następnie kliknij polecenie **Wyświetl kod.**

2. Utwórz nowe wystąpienie kontrolki użytkownika w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet3":::

3. W <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> programie obsługi zdarzeń `ThisWorkbook` dodaj kontrolkę do okienka akcji.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet4":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby sprawdzić, czy okienko akcji jest otwierane po otwarciu dokumentu i czy kontrolki mają relację wzorzec/szczegół.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że okienko akcji jest widoczne.

3. Wybierz firmę w polu listy. Sprawdź, czy nazwa firmy znajduje się na liście w kontrolce i czy <xref:Microsoft.Office.Tools.Excel.NamedRange> szczegóły produktu są wymienione w <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolce.

4. Wybierz różne firmy, aby sprawdzić, czy nazwa firmy i szczegóły produktu odpowiednio się zmieniają.

## <a name="next-steps"></a>Następne kroki
 Oto kilka zadań, które mogą się pojawić w następnej części:

- Wiązanie danych z kontrolkami w programie Word. Aby uzyskać więcej informacji, [zobacz Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Word.](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)

- Wdrażanie projektu. Aby uzyskać więcej informacji, zobacz Deploy an Office solution by using ClickOnce (Wdrażanie [rozwiązania pakietu Office przy użyciu technologii ClickOnce).](../vsto/deploying-an-office-solution-by-using-clickonce.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie okienka Akcje](../vsto/actions-pane-overview.md)
- [How to: Manage control layout on actions panes (Jak zarządzać układem kontrolek w okienkach akcji)](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
