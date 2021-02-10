---
title: 'Przewodnik: Wstawianie danych do skoroszytu na serwerze'
description: Dowiedz się, jak wstawiać dane do zestawu danych, który jest buforowany w skoroszycie programu Microsoft Excel bez uruchamiania programu Excel przy użyciu klasy ServerDocument.
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
ms.openlocfilehash: 2456f92e6bd0b6e1a6b8bf6389718ec6a41342dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937441"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>Przewodnik: Wstawianie danych do skoroszytu na serwerze
  W tym instruktażu pokazano, jak wstawić dane do zestawu danych, który jest buforowany w Microsoft Office skoroszycie programu Excel bez uruchamiania programu Excel przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Definiowanie zestawu danych zawierającego dane z bazy danych AdventureWorksLT.

- Tworzenie wystąpień zestawu danych w projekcie skoroszytu programu Excel i projekcie aplikacji konsolowej.

- Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> , które jest powiązane z zestawem danych w skoroszycie.

- Dodawanie zestawu danych w skoroszycie do pamięci podręcznej danych.

- Wstawianie danych do buforowanego zestawu danych przez uruchomienie kodu w aplikacji konsolowej bez uruchamiania programu Excel.

  Chociaż w tym instruktażu przyjęto założenie, że uruchomiono kod na komputerze deweloperskim, kod, który pokazano w tym instruktażu, może być używany na serwerze, na którym nie jest zainstalowany program Excel.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia Microsoft SQL Server lub Microsoft SQL Server Express z dołączoną przykładową bazą danych AdventureWorksLT. Bazę danych AdventureWorksLT można pobrać z [witryny sieci Web CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych za pomocą SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [How to: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych za pomocą wiersza polecenia, zobacz [How to: Dołączanie pliku bazy danych do SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Utwórz projekt biblioteki klas, który definiuje zestaw danych
 Aby użyć tego samego zestawu danych w projekcie skoroszytu programu Excel i aplikacji konsolowej, należy zdefiniować zestaw danych w osobnym zestawie, do którego odwołuje się oba te projekty. W tym instruktażu Zdefiniuj zestaw danych w projekcie biblioteki klas.

### <a name="to-create-the-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie kliknij pozycję **Windows**.

4. Na liście szablonów projektu wybierz pozycję **Biblioteka klas**.

5. W polu **Nazwa** wpisz **AdventureWorksDataSet**.

6. Kliknij przycisk **Przeglądaj**, przejdź do folderu *%USERPROFILE%\My Documents* (dla systemu Windows XP i starszych) lub *%USERPROFILE%\Documents* (dla systemu Windows Vista), a następnie kliknij pozycję **Wybierz folder**.

7. W oknie dialogowym **Nowy projekt** upewnij się, że pole wyboru **Utwórz katalog dla rozwiązania** nie jest zaznaczone.

8. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **AdventureWorksDataSet** do **Eksplorator rozwiązań** i otwiera plik kodu **Class1.cs** lub **Class1. vb** .

9. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Class1.cs** lub **Class1. vb**, a następnie kliknij polecenie **Usuń**. Ten plik nie jest potrzebny do tego przewodnika.

## <a name="define-a-dataset-in-the-class-library-project"></a>Zdefiniuj zestaw danych w projekcie biblioteki klas
 Zdefiniuj zestaw danych, który zawiera dane z bazy danych AdventureWorksLT dla SQL Server 2005. W dalszej części tego przewodnika odwołujesz się do tego zestawu danych z projektu skoroszytu programu Excel i projektu aplikacji konsolowej.

 Zestaw danych jest *typem zestawu* danych, który reprezentuje dane w tabeli produktów bazy danych AdventureWorksLT. Aby uzyskać więcej informacji o typach danych, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Aby zdefiniować określony zestaw danych w projekcie biblioteki klas

1. W **Eksplorator rozwiązań** kliknij projekt **AdventureWorksDataSet** .

2. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

3. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

4. Kliknij pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

5. Jeśli masz istniejące połączenie z bazą danych AdventureWorksLT, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij pozycję **nowe połączenie**, a następnie użyj okna dialogowego **Dodawanie połączenia** , aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [jak: łączenie z danymi w bazie danych](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** i wybierz pozycję **produkt (tabeli SalesLT)**.

8. Kliknij przycisk **Finish** (Zakończ).

    Plik *AdventureWorksLTDataSet. xsd* zostanie dodany do projektu **AdventureWorksDataSet** . Ten plik definiuje następujące elementy:

   - Określony zestaw danych o nazwie `AdventureWorksLTDataSet` . Ten zestaw danych reprezentuje zawartość tabeli Product w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `ProductTableAdapter` . Ten TableAdapter może służyć do odczytywania i zapisywania danych w `AdventureWorksLTDataSet` . Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

     Oba te obiekty będą używane w dalszej części tego przewodnika.

9. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **AdventureWorksDataSet** , a następnie kliknij pozycję **Kompiluj**.

     Upewnij się, że projekt kompiluje się bez błędów.

## <a name="create-an-excel-workbook-project"></a>Utwórz projekt skoroszytu programu Excel
 Utwórz projekt skoroszytu programu Excel dla interfejsu dla danych. W dalszej części tego instruktażu utworzysz, <xref:Microsoft.Office.Tools.Excel.ListObject> że zostaną wyświetlone dane, i dodasz wystąpienie zestawu danych do pamięci podręcznej danych w skoroszycie.

### <a name="to-create-the-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie **AdventureWorksDataSet** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

3. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

4. Na liście szablonów projektu wybierz **skoroszyt programu excel 2010** lub projekt **skoroszytu programu Excel 2013** .

5. W polu **Nazwa** wpisz **AdventureWorksReport**. Nie należy modyfikować lokalizacji.

6. Kliknij przycisk **OK**.

     Zostanie otwarty **kreator Visual Studio Tools dla programu Office Project** .

7. Upewnij się, że jest zaznaczona **wartość Utwórz nowy dokument** , a następnie kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera skoroszyt **AdventureWorksReport** w Projektancie i dodaje projekt **AdventureWorksReport** do **Eksplorator rozwiązań**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Dodawanie zestawu danych do źródeł danych w projekcie skoroszytu programu Excel
 Zanim będzie można wyświetlić zestaw danych w skoroszycie programu Excel, musisz najpierw dodać zestaw danych do źródeł danych w projekcie skoroszytu programu Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Aby dodać zestaw danych do źródeł danych w projekcie skoroszytu programu Excel

1. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję **Sheet1.cs** lub **Arkusz1. vb** w projekcie **AdventureWorksReport** .

     Skoroszyt zostanie otwarty w projektancie.

2. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych**.

     Zostanie otwarty **Kreator konfiguracji źródła danych** .

3. Kliknij pozycję **obiekt**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz obiekt, który chcesz powiązać** ze stroną kliknij pozycję **Dodaj odwołanie**.

5. Na karcie **projekty** kliknij pozycję **AdventureWorksDataSet** , a następnie kliknij przycisk **OK**.

6. W obszarze nazw **AdventureWorksDataSet** zestawu **AdventureWorksDataSet** kliknij pozycję **AdventureWorksLTDataSet** , a następnie kliknij przycisk **Zakończ**.

     Zostanie otwarte okno **źródła danych** , a do listy źródeł danych zostanie dodany **AdventureWorksLTDataSet** .

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Utwórz listę obiektów, która jest powiązana z wystąpieniem zestawu danych
 Aby wyświetlić zestaw danych w skoroszycie, Utwórz obiekt <xref:Microsoft.Office.Tools.Excel.ListObject> , który jest powiązany z wystąpieniem zestawu danych. Aby uzyskać więcej informacji o kontrolkach powiązań z danymi, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Aby utworzyć listę obiektów, która jest powiązana z wystąpieniem zestawu danych

1. W oknie **źródła danych** rozwiń węzeł **AdventureWorksLTDataSet** w obszarze **AdventureWorksDataSet**.

2. Wybierz węzeł **produkt** , kliknij strzałkę listy rozwijanej, która zostanie wyświetlona, a następnie wybierz pozycję **listaobject** na liście rozwijanej.

     Jeśli strzałka listy rozwijanej nie zostanie wyświetlona, upewnij się, że skoroszyt jest otwarty w projektancie.

3. Przeciągnij tabelę **produktów** do komórki a1.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Kontrolka o nazwie `productListObject` jest tworzona w arkuszu, rozpoczynając od komórki a1. W tym samym czasie obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> nazwie `productBindingSource` zostanie dodany do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject>Jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z obiektem DataSet.

## <a name="add-the-dataset-to-the-data-cache"></a>Dodawanie zestawu danych do pamięci podręcznej danych
 Aby włączyć kod poza projektem skoroszytu programu Excel w celu uzyskania dostępu do zestawu danych w skoroszycie, należy dodać zestaw danych do pamięci podręcznej danych. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [buforowane dane w obszarze dostosowania na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md) i [dane pamięci podręcznej](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Aby dodać zestaw danych do pamięci podręcznej danych

1. W projektancie kliknij pozycję **AdventureWorksLTDataSet**.

2. W oknie **Właściwości** ustaw właściwość **Modyfikatory** na **Public**.

3. Ustaw właściwość **CacheInDocument** na **wartość true**.

## <a name="checkpoint"></a>Punkt kontrolny
 Kompiluj i uruchamiaj projekt skoroszytu programu Excel, aby upewnić się, że kompiluje i uruchamia się bez błędów.

### <a name="to-build-and-run-the-project"></a>Aby skompilować i uruchomić projekt

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **AdventureWorksReport** , wybierz polecenie **Debuguj**, a następnie kliknij polecenie **Uruchom nowe wystąpienie**.

     Projekt został skompilowany, a skoroszyt zostanie otwarty w programie Excel. <xref:Microsoft.Office.Tools.Excel.ListObject>W **arkuszu Arkusz1** jest pusty, ponieważ `adventureWorksLTDataSet` obiekt w pamięci podręcznej danych nie ma jeszcze danych. W następnej sekcji zostanie użyta Aplikacja konsolowa do wypełnienia `adventureWorksLTDataSet` obiektu danymi.

2. Zamknij program Excel. Nie zapisuj zmian.

## <a name="create-a-console-application-project"></a>Tworzenie projektu aplikacji konsolowej
 Utwórz projekt aplikacji konsoli, który ma być używany do wstawiania danych z buforowanego zestawu danych w skoroszycie.

### <a name="to-create-the-console-application-project"></a>Aby utworzyć projekt aplikacji konsolowej

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie **AdventureWorksDataSet** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W okienku **typy projektów** rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie kliknij pozycję **Windows**.

3. W okienku **Szablony** wybierz pozycję **Aplikacja konsolowa**.

4. W polu **Nazwa** wpisz **datawriteer**. Nie należy modyfikować lokalizacji.

5. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **datawrite** do **Eksplorator rozwiązań** i otwiera plik kodu **program.cs** lub **Module1. vb** .

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>Dodawanie danych do buforowanego zestawu danych przy użyciu aplikacji konsolowej
 Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w aplikacji konsolowej, aby wypełnić buforowany zestaw danych w skoroszycie danymi.

### <a name="to-add-data-to-the-cached-dataset"></a>Aby dodać dane do buforowanego zestawu danych

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **datawrite** i kliknij polecenie **Dodaj odwołanie**.

2. Na karcie **.NET** wybierz pozycję **Microsoft. VisualStudio. Tools. Applications. ServerDocument**.

3. Kliknij przycisk **OK**.

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **datawrite** i kliknij polecenie **Dodaj odwołanie**.

5. Na karcie **projekty** wybierz pozycję **AdventureWorksDataSet**, a następnie kliknij przycisk **OK**.

6. Otwórz plik *program.cs* lub *Module1. vb* w edytorze kodu.

7. Dodaj następujące instrukcje **using** (for C#) lub **Imports** (for Visual Basic) na początku pliku kodu.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Dodaj następujący kod do metody `Main`: Ten kod deklaruje następujące obiekty:

   - Wystąpienia `AdventureWorksLTDataSet` i typy, `ProductTableAdapter` które są zdefiniowane w projekcie **AdventureWorksDataSet** .

   - Ścieżka do skoroszytu AdventureWorksReport w folderze Build projektu **AdventureWorksReport** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Obiekt, który ma być używany do uzyskiwania dostępu do pamięci podręcznej danych w skoroszycie.

     > [!NOTE]
     > Poniższy kod założono, że używasz skoroszytu o rozszerzeniu *. xlsx* . Jeśli skoroszyt w projekcie ma inne rozszerzenie pliku, w razie potrzeby zmodyfikuj ścieżkę.

     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]

9. Dodaj następujący kod do `Main` metody po kodzie dodanym w poprzednim kroku. Ten kod wykonuje następujące zadania:

   - Wypełnia typ obiektu DataSet za pomocą karty tabeli.

   - Używa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwości <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w celu uzyskania dostępu do buforowanego zestawu danych w skoroszycie.

   - Używa <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metody do wypełniania buforowanego zestawu danych danymi z lokalnego zestawu danych.

     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]

10. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **datawrite** , wskaż polecenie **Debuguj**, a następnie kliknij polecenie **Uruchom nowe wystąpienie**.

     Projekt został skompilowany, a Aplikacja konsolowa wyświetla kilka komunikatów o stanie po wypełnieniu lokalnego zestawu danych i gdy aplikacja zapisuje dane w buforowanym zestawie danych w skoroszycie. Naciśnij klawisz **Enter** , aby zamknąć aplikację.

## <a name="test-the-workbook"></a>Testowanie skoroszytu
 Po otwarciu skoroszytu <xref:Microsoft.Office.Tools.Excel.ListObject> zostaną wyświetlone dane, które zostały dodane do buforowanego zestawu danych za pomocą aplikacji konsolowej.

### <a name="to-test-the-workbook"></a>Aby przetestować skoroszyt

1. Zamknij skoroszyt AdventureWorksReport w projektancie programu Visual Studio, jeśli jest nadal otwarty.

2. W Eksploratorze plików otwórz skoroszyt AdventureWorksReport, który znajduje się w folderze Build projektu **AdventureWorksReport** . Domyślnie folder kompilacji znajduje się w jednej z następujących lokalizacji:

    - *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (dla systemu Windows XP i starszych)

    - *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (dla systemu Windows Vista)

3. Upewnij się, że <xref:Microsoft.Office.Tools.Excel.ListObject> po otwarciu skoroszytu zostanie wypełnione dane.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat pracy z danymi buforowanymi można znaleźć w następujących tematach:

- Zmiana danych w buforowanym zestawie danych bez uruchamiania programu Excel. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie danych w pamięci podręcznej w skoroszycie na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik: zmiana danych buforowanych w skoroszycie na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
