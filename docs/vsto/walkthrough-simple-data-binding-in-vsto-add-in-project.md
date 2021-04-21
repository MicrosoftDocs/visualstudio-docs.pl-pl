---
title: 'Przewodnik: proste powiązanie danych w projekcie dodatku VSTO'
description: Dowiedz się, jak dodawać kontrolki do dokumentu programu Microsoft Word i powiązać je z danymi w czasie uruchamiania.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e1891173f10acfff74e0f7ef7ab17e29b258b80e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826840"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Przewodnik: proste powiązanie danych w projekcie dodatku VSTO

Dane można powiązać z kontrolkami hosta i kontrolkami Windows Forms w projektach dodatków VSTO. W tym przewodniku pokazano, jak dodać kontrolki do Microsoft Office programu Word i powiązać kontrolki z danymi w czasie uruchamiania.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie do <xref:Microsoft.Office.Tools.Word.ContentControl> dokumentu w czasie uruchamiania.

- Tworzenie obiektu <xref:System.Windows.Forms.BindingSource> , który łączy kontrolkę z wystąpieniem zestawu danych.

- Umożliwianie użytkownikowi przewijania rekordów i wyświetlania ich w kontrolce.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, do których dołączono przykładową `AdventureWorksLT` bazę danych. Bazę danych można `AdventureWorksLT` pobrać z [repozytorium GitHub przykładów SQL Server przykładów.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [Jak: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [How to: Attach a database file to SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Pierwszym krokiem jest utworzenie projektu dodatku Word VSTO.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku Word VSTO o nazwie **Wypełnianie** dokumentów z bazy danych przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio plik *ThisAddIn.vb* lub *ThisAddIn.cs* i dodaje dokument **Wypełnianie dokumentów** z projektu bazy danych do Eksplorator rozwiązań **.**

2. Jeśli projekt jest przeznaczony dla pliku lub , dodaj odwołanie do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* zestawu. To odwołanie jest wymagane do programowego dodawania Windows Forms do dokumentu w dalszej części tego przewodnika.

## <a name="create-a-data-source"></a>Tworzenie źródła danych

Użyj okna **Źródła danych,** aby dodać typowany zestaw danych do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typowany zestaw danych do projektu

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

2. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Kliknij **pozycję Baza** danych , a następnie kliknij przycisk **Dalej.**

4. Jeśli masz istniejące połączenie z bazą `AdventureWorksLT` danych, wybierz to połączenie i kliknij przycisk **Dalej.**

    W przeciwnym razie **kliknij pozycję Nowe połączenie** i użyj okna **dialogowego** Dodawanie połączenia, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń.](../data-tools/add-new-connections.md)

5. Na stronie **Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji** kliknij przycisk **Dalej.**

6. Na stronie **Wybieranie obiektów bazy danych** rozwiń pozycję **Tabele** i wybierz pozycję **Klient (SalesLT).**

7. Kliknij przycisk **Finish** (Zakończ).

    Plik *AdventureWorksLTDataSet.xsd* jest dodawany **do** Eksplorator rozwiązań . Ten plik definiuje następujące elementy:

   - Typowany zestaw danych o nazwie `AdventureWorksLTDataSet` . Ten zestaw danych reprezentuje zawartość **tabeli Customer (SalesLT)** w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `CustomerTableAdapter` . Ten tableadapter może służyć do odczytu i zapisu danych w `AdventureWorksLTDataSet` . Aby uzyskać więcej informacji, zobacz [Omówienie tableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obu tych obiektów użyjemy w dalszej części tego przewodnika.

## <a name="create-controls-and-binding-controls-to-data"></a>Tworzenie kontrolek i powiązanie kontrolek z danymi

Interfejs do wyświetlania rekordów bazy danych w tym przewodniku jest podstawowy i jest tworzony bezpośrednio w dokumencie. Jedna wyświetla pojedynczy rekord bazy danych na raz, a dwie kontrolki umożliwiają przewijanie rekordów w obie <xref:Microsoft.Office.Tools.Word.ContentControl> <xref:Microsoft.Office.Tools.Word.Controls.Button> strony. Kontrolka zawartości używa kontrolki <xref:System.Windows.Forms.BindingSource> do nawiązywania połączenia z bazą danych.

Aby uzyskać więcej informacji na temat wiązania kontrolek z danymi, zobacz [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-create-the-interface-in-the-document"></a>Aby utworzyć interfejs w dokumencie

1. W klasie `ThisAddIn` zadeklaruj następujące kontrolki, aby wyświetlić i `Customer` przewijać tabelę bazy `AdventureWorksLTDataSet` danych.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet1":::

2. W metodzie dodaj następujący kod, aby zainicjować zestaw danych, a następnie wypełnij zestaw danych informacjami `ThisAddIn_Startup` z bazy `AdventureWorksLTDataSet` danych.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet2":::

3. Dodaj następujący kod do metody `ThisAddIn_Startup`: Powoduje to wygenerowanie elementu hosta, który rozszerza dokument. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet3":::

4. Zdefiniuj kilka zakresów na początku dokumentu. Te zakresy identyfikują miejsce wstawiania tekstu i umieszczać kontrolki.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet4":::

5. Dodaj kontrolki interfejsu do wcześniej zdefiniowanych zakresów.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet5":::

6. Powiąż kontrolkę zawartości `AdventureWorksLTDataSet` z usługą przy użyciu . <xref:System.Windows.Forms.BindingSource> Dla deweloperów języka C# dodaj dwie procedury obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolek.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet6":::

7. Dodaj następujący kod, aby nawigować po rekordach bazy danych.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet7":::

## <a name="test-the-add-in"></a>Testowanie dodatku

Po otwarciu programu Word kontrolka zawartości wyświetla dane z zestawu `AdventureWorksLTDataSet` danych. Przewiń rekordy bazy danych, klikając przyciski **Dalej** **i** Poprzedni.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij klawisz **F5**.

     Kontrolka zawartości o `customerContentControl` nazwie zostanie utworzona i wypełniona danymi. W tym samym czasie obiekt zestawu danych o `adventureWorksLTDataSet` nazwie i nazwie są dodawane do <xref:System.Windows.Forms.BindingSource> `customerBindingSource` projektu. Obiekt jest powiązany z obiektem , który z <xref:Microsoft.Office.Tools.Word.ContentControl> kolei jest powiązany z <xref:System.Windows.Forms.BindingSource> obiektem zestawu danych.

2. Kliknij przyciski **Dalej** **i Poprzedni,** aby przewijać rekordy bazy danych.

## <a name="see-also"></a>Zobacz też

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Jak wypełnić arkusze danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [How to: Populate documents with data from a database (Jak wypełnić dokumenty danymi z bazy danych)](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [How to: Populate documents with data from services (Jak wypełnić dokumenty danymi z usług)](../vsto/how-to-populate-documents-with-data-from-services.md)
- [How to: Populate documents with data from objects (Jak wypełnić dokumenty danymi z obiektów)](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Jak przewijać rekordy bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Jak zaktualizować źródło danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Omówienie używania plików lokalnej bazy danych w rozwiązaniach pakietu Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [How to: Populate documents with data from objects (Jak wypełnić dokumenty danymi z obiektów)](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Jak zaktualizować źródło danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Omówienie używania plików lokalnej bazy danych w rozwiązaniach pakietu Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)
