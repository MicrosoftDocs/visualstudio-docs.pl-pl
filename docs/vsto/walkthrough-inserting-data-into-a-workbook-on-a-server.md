---
title: 'Przewodnik: Wstawianie danych do skoroszytu na serwerze'
description: Dowiedz się, jak wstawić dane do zestawu danych buforowanych w skoroszycie programu Microsoft Excel bez uruchamiania programu Excel przy użyciu klasy ServerDocument.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bf5d3bcb09ce1db013b89e60b22308f1904c4796
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827724"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>Przewodnik: Wstawianie danych do skoroszytu na serwerze
  W tym przewodniku pokazano, jak wstawić dane do zestawu danych, który jest buforowany w skoroszycie programu Excel Microsoft Office excel bez uruchamiania programu Excel przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Definiowanie zestawu danych zawierającego dane z bazy danych AdventureWorksLT.

- Tworzenie wystąpień zestawu danych w projekcie skoroszytu programu Excel i projekcie aplikacji konsolowej.

- Tworzenie obiektów <xref:Microsoft.Office.Tools.Excel.ListObject> powiązanych z zestawem danych w skoroszycie.

- Dodanie zestawu danych w skoroszycie do pamięci podręcznej danych.

- Wstawianie danych do buforowanych zestawów danych przez uruchomienie kodu w aplikacji konsolowej bez uruchamiania programu Excel.

  Mimo że w tym przewodniku założono, że kod jest uruchomiony na komputerze dewelopera, kod zademonstrowany w tym przewodniku może być używany na serwerze, na którym nie zainstalowano programu Excel.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia Microsoft SQL Server lub Microsoft SQL Server Express, do których jest dołączona przykładowa baza danych AdventureWorksLT. Bazę danych AdventureWorksLT można pobrać z witryny [internetowej CodePlex.](https://archive.codeplex.com/?p=SqlServerSamples) Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [Jak: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [How to: Attach a database file to SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Tworzenie projektu biblioteki klas definiującego zestaw danych
 Aby użyć tego samego zestawu danych w projekcie skoroszytu programu Excel i aplikacji konsolowej, musisz zdefiniować zestaw danych w oddzielnym zestawie, do który odwołuje się oba te projekty. W tym przewodniku zdefiniuj zestaw danych w projekcie biblioteki klas.

### <a name="to-create-the-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie kliknij pozycję **Windows**.

4. Na liście szablonów projektów wybierz pozycję **Biblioteka klas**.

5. W polu **Nazwa** wpisz **AdventureWorksDataSet**.

6. Kliknij **przycisk** Przeglądaj , przejdź do folderu *%UserProfile%\Moje dokumenty* (dla systemu Windows XP i starszych) lub *folderu %UserProfile%\Documents* (dla systemu Windows Vista), a następnie kliknij pozycję Wybierz **folder**.

7. W **oknie dialogowym Nowy** projekt upewnij się, że pole wyboru Utwórz **katalog** dla rozwiązania nie jest zaznaczone.

8. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje projekt **AdventureWorksDataSet** do **Eksplorator rozwiązań** i otwiera plik kodu **Class1.cs** lub **Class1.vb.**

9. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **plik Class1.cs** lub **Class1.vb,** a następnie kliknij polecenie **Usuń**. Ten plik nie jest potrzebny w tym przewodniku.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definiowanie zestawu danych w projekcie biblioteki klas
 Zdefiniuj typowany zestaw danych zawierający dane z bazy danych AdventureWorksLT dla SQL Server 2005. W dalszej części tego przewodnika będziesz odwoływać się do tego zestawu danych z projektu skoroszytu programu Excel i projektu aplikacji konsolowej.

 Zestaw danych to *typowany zestaw danych,* który reprezentuje dane w tabeli Product bazy danych AdventureWorksLT. Aby uzyskać więcej informacji na temat typów zestawów danych, zobacz [Narzędzia zestawu](../data-tools/dataset-tools-in-visual-studio.md)danych w Visual Studio .

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Aby zdefiniować typowany zestaw danych w projekcie biblioteki klas

1. W **Eksplorator rozwiązań** kliknij projekt **AdventureWorksDataSet.**

2. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

3. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

4. Kliknij **pozycję Baza** danych , a następnie kliknij przycisk **Dalej.**

5. Jeśli masz istniejące połączenie z bazą danych AdventureWorksLT, wybierz to połączenie i kliknij przycisk **Dalej.**

    W przeciwnym razie **kliknij pozycję Nowe** połączenie i użyj okna **dialogowego** Dodawanie połączenia, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz How to: Connect to data in a database (Jak [nawiązać połączenie z danymi w bazie danych).](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)

6. Na stronie **Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji** kliknij przycisk **Dalej.**

7. Na stronie **Wybieranie obiektów bazy danych** rozwiń pozycję **Tabele** i wybierz pozycję **Produkt (SalesLT).**

8. Kliknij przycisk **Finish** (Zakończ).

    Plik *AdventureWorksLTDataSet.xsd* zostanie dodany do **projektu AdventureWorksDataSet.** Ten plik definiuje następujące elementy:

   - Typowany zestaw danych o nazwie `AdventureWorksLTDataSet` . Ten zestaw danych reprezentuje zawartość tabeli Product w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `ProductTableAdapter` . Ten tableAdapter może służyć do odczytu i zapisu danych w `AdventureWorksLTDataSet` . Aby uzyskać więcej informacji, zobacz [Omówienie tableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obu tych obiektów użyjemy w dalszej części tego przewodnika.

9. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **AdventureWorksDataSet** i kliknij polecenie **Build (Kompilacja).**

     Sprawdź, czy projekt jest kompilowany bez błędów.

## <a name="create-an-excel-workbook-project"></a>Tworzenie projektu skoroszytu programu Excel
 Utwórz projekt skoroszytu programu Excel dla interfejsu danych. W dalszej części tego przewodnika utworzysz element , który wyświetla dane, a następnie dodasz wystąpienie zestawu danych do pamięci podręcznej danych <xref:Microsoft.Office.Tools.Excel.ListObject> w skoroszycie.

### <a name="to-create-the-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie **AdventureWorksDataSet,** wskaż polecenie **Dodaj,** a następnie kliknij pozycję **Nowy projekt.**

2. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

3. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł **Dodatki pakietu Office.**

4. Na liście szablonów projektów wybierz projekt Skoroszyt programu **Excel 2010** lub Skoroszyt programu **Excel 2013.**

5. W polu **Nazwa** wpisz **AdventureWorksReport**. Nie należy modyfikować lokalizacji.

6. Kliknij przycisk **OK**.

     Zostanie **Visual Studio Tools kreator projektu pakietu Office.**

7. Upewnij **się, że jest zaznaczona opcja Utwórz** nowy dokument, a następnie kliknij przycisk **OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera skoroszyt **AdventureWorksReport** w projektancie i dodaje projekt **AdventureWorksReport** do **Eksplorator rozwiązań**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Dodawanie zestawu danych do źródeł danych w projekcie skoroszytu programu Excel
 Aby można było wyświetlić zestaw danych w skoroszycie programu Excel, należy najpierw dodać zestaw danych do źródeł danych w projekcie skoroszytu programu Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Aby dodać zestaw danych do źródeł danych w projekcie skoroszytu programu Excel

1. W **Eksplorator rozwiązań** kliknij dwukrotnie **pozycję Sheet1.cs** lub **Sheet1.vb** w **projekcie AdventureWorksReport.**

     Skoroszyt zostanie otwarty w projektancie.

2. W menu **Dane** kliknij pozycję **Dodaj nowe źródło danych.**

     Zostanie **otwarty Kreator konfiguracji źródła** danych.

3. Kliknij **pozycję Obiekt**, a następnie kliknij przycisk **Dalej.**

4. Na stronie **Wybierz obiekt, z którą chcesz powiązać** powiązanie, kliknij pozycję **Dodaj odwołanie**.

5. Na karcie **Projekty** kliknij pozycję **AdventureWorksDataSet,** a następnie kliknij przycisk **OK.**

6. W przestrzeni **nazw AdventureWorksDataSet** **zestawu AdventureWorksDataSet** kliknij pozycję **AdventureWorksLTDataSet,** a następnie kliknij przycisk **Zakończ.**

     Zostanie **otwarte okno Źródła** danych, a zestaw **AdventureWorksLTDataSet** zostanie dodany do listy źródeł danych.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Tworzenie obiektu ListObject powiązanego z wystąpieniem zestawu danych
 Aby wyświetlić zestaw danych w skoroszycie, utwórz element <xref:Microsoft.Office.Tools.Excel.ListObject> powiązany z wystąpieniem zestawu danych. Aby uzyskać więcej informacji na temat wiązania kontrolek z danymi, zobacz [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Aby utworzyć element ListObject powiązany z wystąpieniem zestawu danych

1. W **oknie Źródła** danych rozwiń węzeł **AdventureWorksLTDataSet** w obszarze **AdventureWorksDataSet**.

2. Wybierz węzeł **Produkt,** kliknij strzałkę listy rozwijanej, która zostanie wyświetlona, a następnie wybierz pozycję **ListObject** na liście rozwijanej.

     Jeśli strzałka listy rozwijanej nie jest wyświetlana, upewnij się, że skoroszyt jest otwarty w projektancie.

3. Przeciągnij **tabelę Product** do komórki A1.

     W <xref:Microsoft.Office.Tools.Excel.ListObject> arkuszu zostanie utworzona `productListObject` kontrolka o nazwie rozpoczynająca się w komórce A1. W tym samym czasie obiekt zestawu danych o `adventureWorksLTDataSet` nazwie i nazwie są dodawane do <xref:System.Windows.Forms.BindingSource> `productBindingSource` projektu. Element <xref:Microsoft.Office.Tools.Excel.ListObject> jest powiązany z <xref:System.Windows.Forms.BindingSource> obiektem , który z kolei jest powiązany z obiektem zestawu danych.

## <a name="add-the-dataset-to-the-data-cache"></a>Dodawanie zestawu danych do pamięci podręcznej danych
 Aby umożliwić dostęp do zestawu danych w skoroszycie kodu spoza projektu skoroszytu programu Excel, należy dodać zestaw danych do pamięci podręcznej danych. Aby uzyskać więcej informacji na temat pamięci podręcznej danych, zobacz [Cached data in document-level customizations (Buforowane](../vsto/cached-data-in-document-level-customizations.md) dane w dostosowaniach na poziomie dokumentu) i [Cache data (Dane pamięci podręcznej).](../vsto/caching-data.md)

### <a name="to-add-the-dataset-to-the-data-cache"></a>Aby dodać zestaw danych do pamięci podręcznej danych

1. W projektancie kliknij pozycję **adventureWorksLTDataSet.**

2. W **oknie** Właściwości ustaw właściwość **Modyfikatory na** **public**.

3. Ustaw właściwość **CacheInDocument na** **wartość True.**

## <a name="checkpoint"></a>Punkt kontrolny
 Skompiluj i uruchom projekt skoroszytu programu Excel, aby upewnić się, że jest on kompilowany i uruchamiany bez błędów.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **AdventureWorksReport,** wybierz polecenie **Debuguj**, a następnie kliknij polecenie Uruchom **nowe wystąpienie**.

     Projekt został sbudowaną i skoroszyt zostanie otwarty w programie Excel. Obiekt <xref:Microsoft.Office.Tools.Excel.ListObject> w **arkuszu Sheet1** jest pusty, ponieważ `adventureWorksLTDataSet` obiekt w pamięci podręcznej danych nie ma jeszcze żadnych danych. W następnej sekcji użyjemy aplikacji konsolowej, aby wypełnić `adventureWorksLTDataSet` obiekt danymi.

2. Zamknij program Excel. Nie zapisuj zmian.

## <a name="create-a-console-application-project"></a>Tworzenie projektu aplikacji konsolowej
 Utwórz projekt aplikacji konsolowej do wstawiania danych w buforowanych zestawach danych w skoroszycie.

### <a name="to-create-the-console-application-project"></a>Aby utworzyć projekt aplikacji konsolowej

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie **AdventureWorksDataSet,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt.**

2. W **okienku Typy projektów** rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie kliknij pozycję **Windows**.

3. W **okienku Szablony** wybierz pozycję **Aplikacja konsolowa.**

4. W polu **Nazwa** wpisz **DataWriter**. Nie należy modyfikować lokalizacji.

5. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Dodaje projekt **DataWriter** **do** Eksplorator rozwiązań i otwiera plik kodu **Program.cs** lub **Module1.vb.**

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>Dodawanie danych do buforowanych zestawów danych przy użyciu aplikacji konsolowej
 Użyj klasy <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> w aplikacji konsolowej, aby wypełnić buforowany zestaw danych w skoroszycie danymi.

### <a name="to-add-data-to-the-cached-dataset"></a>Aby dodać dane do buforowanych zestawów danych

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DataWriter** i kliknij polecenie **Dodaj odwołanie**.

2. Na karcie **.NET** wybierz pozycję **Microsoft.VisualStudio.Tools.Applications.ServerDocument.**

3. Kliknij przycisk **OK**.

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DataWriter** i kliknij polecenie **Dodaj odwołanie**.

5. Na karcie **Projekty** wybierz pozycję **AdventureWorksDataSet** i kliknij przycisk **OK.**

6. Otwórz *plik Program.cs* lub *Module1.vb* w Edytorze kodu.

7. Dodaj następującą **instrukcje using** (dla języka C#) lub **Imports** (Visual Basic) na początku pliku kodu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. Dodaj następujący kod do metody `Main`: Ten kod deklaruje następujące obiekty:

   - Wystąpienia typów `AdventureWorksLTDataSet` i `ProductTableAdapter` zdefiniowanych w projekcie **AdventureWorksDataSet.**

   - Ścieżka do skoroszytu AdventureWorksReport w folderze kompilacji projektu **AdventureWorksReport.**

   - Obiekt <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> do użycia w celu uzyskania dostępu do pamięci podręcznej danych w skoroszycie.

     > [!NOTE]
     > W poniższym kodzie przyjęto założenie, że używasz skoroszytu z rozszerzeniem *pliku xlsx.* Jeśli skoroszyt w projekcie ma inne rozszerzenie pliku, zmodyfikuj ścieżkę zgodnie z potrzebami.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet3":::

9. Dodaj następujący kod do `Main` metody po kodzie dodanym w poprzednim kroku. Ten kod wykonuje następujące zadania:

   - Wypełnia typowany obiekt zestawu danych za pomocą adaptera tabeli.

   - Używa właściwości klasy , aby uzyskać dostęp do <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> buforowanych zestawów danych w skoroszycie.

   - Używa metody , aby wypełnić buforowany zestaw danych <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> danymi z lokalnego typiowego zestawu danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet4":::

10. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DataWriter,** wskaż polecenie **Debuguj,** a następnie kliknij polecenie Uruchom nowe **wystąpienie**.

     Projekt jest budowany, a aplikacja konsolowa wyświetla kilka komunikatów o stanie po wypełnieniu lokalnego zestawu danych i zapisaniu danych w buforowym zestawie danych w skoroszycie. Naciśnij **klawisz Enter,** aby zamknąć aplikację.

## <a name="test-the-workbook"></a>Testowanie skoroszytu
 Po otwarciu skoroszytu zostaną wyświetlone dane dodane do buforowanych zestawów danych <xref:Microsoft.Office.Tools.Excel.ListObject> za pomocą aplikacji konsolowej.

### <a name="to-test-the-workbook"></a>Aby przetestować skoroszyt

1. Zamknij skoroszyt AdventureWorksReport w projektancie Visual Studio, jeśli jest nadal otwarty.

2. W Eksplorator plików otwórz skoroszyt AdventureWorksReport, który znajduje się w folderze kompilacji **projektu AdventureWorksReport.** Domyślnie folder kompilacji znajduje się w jednej z następujących lokalizacji:

    - *%UserProfile%\Moje dokumenty\AdventureWorksReport\bin\Debug* (dla systemu Windows XP i starszych)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (dla systemu Windows Vista)

3. Po otwarciu skoroszytu sprawdź, czy dane <xref:Microsoft.Office.Tools.Excel.ListObject> zostały wypełnione.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat pracy z danymi w pamięci podręcznej można znaleźć w tych tematach:

- Zmiana danych w buforowanych zestawach danych bez uruchamiania programu Excel. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie danych buforowanych w skoroszycie na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik: zmienianie buforowanych danych w skoroszycie na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
