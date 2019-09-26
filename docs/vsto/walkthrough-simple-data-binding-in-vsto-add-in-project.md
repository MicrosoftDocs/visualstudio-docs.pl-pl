---
title: 'Przewodnik: Proste powiązanie danych w projekcie dodatku VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e174782c46d24b7743d50faa9fac69d38c3d6c6
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255183"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Przewodnik: Proste powiązanie danych w projekcie dodatku VSTO

Można powiązać dane z kontrolkami hosta i formantami Windows Forms w projektach dodatku VSTO. W tym instruktażu pokazano, jak dodać kontrolki do dokumentu programu Microsoft Office Word i powiązać kontrolki z danymi w czasie wykonywania.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

W instruktażu przedstawiono następujące zagadnienia:

- <xref:Microsoft.Office.Tools.Word.ContentControl> Dodawanie do dokumentu w czasie wykonywania.

- <xref:System.Windows.Forms.BindingSource> Tworzenie, które łączy formant z wystąpieniem zestawu danych.

- Umożliwienie użytkownikowi przewijania rekordów i wyświetlania ich w kontrolce.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, do którego `AdventureWorksLT` jest dołączona Przykładowa baza danych. `AdventureWorksLT` Bazę danych można pobrać z [witryny sieci Web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych za pomocą SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [How to: Dołącz bazę danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych za pomocą wiersza polecenia, zobacz [How to: Dołącz plik bazy danych do SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Word z nazwą **zapełniania dokumentów z bazy danych**przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     Program Visual Studio otwiera plik *ThisAddIn. vb* lub *ThisAddIn.cs* i dodaje do **Eksplorator rozwiązań** **dokumenty wypełniania z projektu bazy danych** .

2. Jeśli projekt jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]lub, Dodaj odwołanie do zestawu *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* . Ta dokumentacja jest wymagana do programowego dodawania formantów Windows Forms do dokumentu w dalszej części tego przewodnika.

## <a name="create-a-data-source"></a>Utwórz źródło danych

Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typ DataSet do projektu

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl** > inne**źródła danych** **systemu Windows** > .

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Kliknij pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Jeśli masz istniejące połączenie z `AdventureWorksLT` bazą danych, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij pozycję **nowe połączenie**, a następnie użyj okna dialogowego **Dodawanie połączenia** , aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

5. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

6. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** i wybierz pozycję **klient (tabeli SalesLT)** .

7. Kliknij przycisk **Zakończ**.

    Plik *AdventureWorksLTDataSet. xsd* zostanie dodany do **Eksplorator rozwiązań**. Ten plik definiuje następujące elementy:

   - Określony zestaw danych o `AdventureWorksLTDataSet`nazwie. Ten zestaw danych reprezentuje zawartość tabeli **Customer (tabeli SalesLT)** w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `CustomerTableAdapter`. Ten TableAdapter może służyć do odczytywania i zapisywania danych w `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

     Oba te obiekty będą używane w dalszej części tego przewodnika.

## <a name="create-controls-and-binding-controls-to-data"></a>Tworzenie kontrolek i kontrolowanie powiązań z danymi

Interfejs do wyświetlania rekordów bazy danych w tym instruktażu jest podstawowy i jest tworzony bezpośrednio wewnątrz dokumentu. Jeden <xref:Microsoft.Office.Tools.Word.ContentControl> wyświetla rekord pojedynczej bazy danych w danym momencie, a <xref:Microsoft.Office.Tools.Word.Controls.Button> dwa kontrolki umożliwiają przewijanie rekordów. Kontrolka zawartości używa <xref:System.Windows.Forms.BindingSource> do nawiązywania połączenia z bazą danych.

Aby uzyskać więcej informacji o kontrolkach powiązań z danymi, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Aby utworzyć interfejs w dokumencie

1. W klasie należy zadeklarować następujące kontrolki do wyświetlania i przewijania `Customer` tabeli `AdventureWorksLTDataSet` bazy danych. `ThisAddIn`

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. W metodzie Dodaj następujący kod, aby zainicjować zestaw danych, Wypełnij zestaw danych informacjami `AdventureWorksLTDataSet` z bazy danych. `ThisAddIn_Startup`

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Dodaj następujący kod do `ThisAddIn_Startup` metody. Spowoduje to wygenerowanie elementu hosta, który rozszerza dokument. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Zdefiniuj kilka zakresów na początku dokumentu. Te zakresy identyfikują, gdzie wstawić kontrolki tekstu i umieszczania.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Dodaj formanty interfejsu do wcześniej zdefiniowanych zakresów.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Powiąż kontrolkę zawartości `AdventureWorksLTDataSet` z przy <xref:System.Windows.Forms.BindingSource>użyciu. Dla C# deweloperów Dodaj dwa programy obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolek.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Dodaj następujący kod, aby nawigować przez rekordy bazy danych.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Testowanie dodatku

Po otwarciu programu Word kontrolka zawartości wyświetla dane z `AdventureWorksLTDataSet` zestawu danych. Przewiń rekordy bazy danych, klikając przyciski **dalej** i **Wstecz** .

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5**.

     Formant zawartości o nazwie `customerContentControl` jest tworzony i wypełniany danymi. W tym samym czasie obiekt zestawu danych o nazwie `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> i nazwie `customerBindingSource` zostanie dodany do projektu. <xref:Microsoft.Office.Tools.Word.ContentControl> Jest powiązany<xref:System.Windows.Forms.BindingSource>z, który z kolei jest powiązany z obiektem DataSet.

2. Kliknij przyciski **dalej** i **Wstecz** , aby przewijać rekordy bazy danych.

## <a name="see-also"></a>Zobacz także

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: Wypełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: Wypełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Wypełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: Wypełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Instrukcje: Aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: Wypełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)
