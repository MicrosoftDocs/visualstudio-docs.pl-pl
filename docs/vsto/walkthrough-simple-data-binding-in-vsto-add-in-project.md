---
title: 'Wskazówki: Proste powiązanie danych w projekcie dodatku narzędzi VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0373bcba5cecbbc47451f3ad050ba0ea44a12246
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672668"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Wskazówki: Proste powiązanie danych w projekcie dodatku narzędzi VSTO

Dane można powiązać formanty hosta i kontrolek Windows Forms w projektach dodatku narzędzi VSTO. W tym instruktażu pokazano, jak dodać kontrolki do dokumentu programu Microsoft Office Word i powiązać formanty z danymi w czasie wykonywania.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

W instruktażu przedstawiono następujące zagadnienia:

-   Dodawanie <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentu w czasie wykonywania.

-   Tworzenie <xref:System.Windows.Forms.BindingSource> , formant łączy się z wystąpieniem zestawu danych.

-   Włączanie użytkownika do przewijania rekordów i wyświetlać je w kontrolce.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

-   Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, który ma `AdventureWorksLT` przykładowej bazy danych dołączono do niego. Możesz pobrać `AdventureWorksLT` bazy danych z [witryny sieci Web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:

    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1.  Utwórz projekt dodatku narzędzi VSTO programu Word z nazwą **zapełnianie dokumentów z bazy danych**, za pomocą Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projekty pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Zostanie otwarty program Visual Studio *ThisAddIn.vb* lub *ThisAddIn.cs* plików i dodaje **zapełnianie dokumentów z bazy danych** projekt **Eksploratora rozwiązań** .

2.  Jeśli projekt jest ukierunkowany [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], Dodaj odwołanie do *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* zestawu. To odwołanie jest wymagane, aby programowo dodać kontrolek formularzy Windows Forms do dokumentów w dalszej części tego przewodnika.

## <a name="create-a-data-source"></a>Utwórz źródło danych

Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typizowany zestaw danych do projektu

1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.

2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.

4. Jeśli masz istniejące połączenie z programem `AdventureWorksLT` bazy danych, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodaj połączenie** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

5. W **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

6. W **wybierz obiekty bazy danych** rozwiń **tabel** i wybierz **klienta (SalesLT)**.

7. Kliknij przycisk **Zakończ**.

    *AdventureWorksLTDataSet.xsd* plik zostanie dodany do **Eksploratora rozwiązań**. Ten plik definiuje następujące elementy:

   - Typizowany zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość **klienta (SalesLT)** tabeli w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `CustomerTableAdapter`. Ten obiekt TableAdapter można odczytywać i zapisywać dane `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Użyje obu tych obiektów w dalszej części tego przewodnika.

## <a name="create-controls-and-binding-controls-to-data"></a>Tworzenie kontrolki oraz powiązanie z danymi

Interfejs do wyświetlania rekordów bazy danych w tym instruktażu jest poziom podstawowy i utworzeniu bezpośrednio w dokumencie. Jeden <xref:Microsoft.Office.Tools.Word.ContentControl> wyświetla rekord ze pojedynczej bazy danych w czasie i dwóch <xref:Microsoft.Office.Tools.Word.Controls.Button> formanty pozwalają na i z powrotem przewijania rekordów. Formant zawartości używa <xref:System.Windows.Forms.BindingSource> do łączenia z bazą danych.

Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Aby utworzyć interfejs w dokumencie

1.  W `ThisAddIn` klasy, Zadeklaruj następujące formanty do wyświetlania i przewijać `Customer` tabeli `AdventureWorksLTDataSet` bazy danych.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2.  W `ThisAddIn_Startup` metody, Dodaj następujący kod, aby zainicjować zestaw danych, wypełnić dataset przy użyciu informacji z `AdventureWorksLTDataSet` bazy danych.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3.  Dodaj następujący kod do `ThisAddIn_Startup` metody. Spowoduje to wygenerowanie element hosta, która rozszerza dokument. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4.  Zdefiniuj kilku zakresów na początku dokumentu. Tych zakresach wskazać, gdzie Wstawianie tekstu i umieść formanty.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5.  Dodawanie kontrolek interfejsu do wcześniej zdefiniowanego zakresu.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6.  Powiąż formant zawartości `AdventureWorksLTDataSet` przy użyciu <xref:System.Windows.Forms.BindingSource>. Aby uzyskać C# deweloperów, Dodaj dwie procedury obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolki.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7.  Dodaj następujący kod, aby poruszać się po rekordów bazy danych.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Testowanie dodatku programu

Po otwarciu programu Word, formant zawartości są wyświetlane dane z `AdventureWorksLTDataSet` zestawu danych. Przewijanie rekordów bazy danych, klikając pozycję **dalej** i **Wstecz** przycisków.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

1.  Naciśnij klawisz **F5**.

     Kontrolki zawartości o nazwie `customerContentControl` zostanie utworzony i wypełniony danymi. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `customerBindingSource` są dodawane do projektu. <xref:Microsoft.Office.Tools.Word.ContentControl> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.

2.  Kliknij przycisk **dalej** i **Wstecz** przycisków do przewijania rekordów bazy danych.

## <a name="see-also"></a>Zobacz także

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Porady: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Porady: aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Wskazówki: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Wskazówki: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Porady: aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)