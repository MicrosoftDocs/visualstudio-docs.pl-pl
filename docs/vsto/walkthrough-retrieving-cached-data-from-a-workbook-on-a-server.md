---
title: 'Wskazówki: Pobieranie danych z pamięci podręcznej ze skoroszytu na serwerze'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2365fc766ede37d39eccdccc664d5710dc68d586
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673006"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Wskazówki: Pobieranie danych z pamięci podręcznej ze skoroszytu na serwerze
  W tym instruktażu pokazano, jak pobierać dane z zestawu danych, który jest buforowany w skoroszytu programu Microsoft Excel pakietu Office bez uruchamiania programu Excel przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Definiowanie zestawu danych, która zawiera dane z *AdventureWorksLT* bazy danych.  
  
- Tworzenie wystąpień zestawu danych w projektu skoroszytu programu Excel i projekt aplikacji konsoli.  
  
- Tworzenie <xref:Microsoft.Office.Tools.Excel.ListObject> jest powiązane z zestawem danych w skoroszycie i wypełniania <xref:Microsoft.Office.Tools.Excel.ListObject> z danymi, po otwarciu skoroszytu.  
  
- Dodawanie zestawu danych w skoroszycie do pamięci podręcznej danych.  
  
- Odczytywanie danych z pamięci podręcznej zestawu danych do zestawu danych w aplikacji konsoli bez uruchamiania programu Excel.  
  
  Chociaż w tym przewodniku przyjęto założenie, że uruchomieniu kodu na komputerze deweloperskim, kod przedstawiona w tym instruktażu może być używany w taki sposób, na serwerze, który nie ma zainstalowanego programu Excel.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do uruchomionego wystąpienia programu Microsoft SQL Server lub programu Microsoft SQL Server Express ma przykładowej bazy danych AdventureWorksLT podłączone do niego. Możesz pobrać bazy danych AdventureWorksLT z [witryny sieci Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:  
  
    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).  
  
    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](/previous-versions/sql/).  
  
## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Utwórz projekt biblioteki klas, który definiuje zestaw danych  
 Aby użyć tego samego zestawu danych w projekcie skoroszytu programu Excel i aplikacji konsoli, należy zdefiniować zestaw danych w osobnym zestawie, który odwołuje się do obu tych projektów. W ramach tego przewodnika należy zdefiniować zestaw danych w projekcie biblioteki klas.  
  
### <a name="create-the-class-library-project"></a>Utwórz projekt biblioteki klas  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
4.  Na liście szablonów projektu wybierz **biblioteki klas**.  
  
5.  W **nazwa** wpisz **AdventureWorksDataSet**.  
  
6.  Kliknij przycisk **Przeglądaj**, przejdź do swojej *%UserProfile%\My dokumenty* (Windows XP i starszych) lub *%UserProfile%\Documents* (dla systemu Windows Vista) folder, a następnie kliknij przycisk **Wybierz Folder**.  
  
7.  W **nowy projekt** okna dialogowego pole, upewnij się, że **Utwórz katalog rozwiązania** nie zaznaczono pole wyboru.  
  
8.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **AdventureWorksDataSet** projekt **Eksploratora rozwiązań** i otwiera *Class1.cs* lub *Class1.vb* pliku kodu.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *Class1.cs* lub *Class1.vb*, a następnie kliknij przycisk **Usuń**. Nie potrzebujesz tego pliku w ramach tego przewodnika.  
  
## <a name="define-a-dataset-in-the-class-library-project"></a>Zdefiniuj zestaw danych w projekcie biblioteki klas  
 Zdefiniuj typizowany zestaw danych, która zawiera dane z bazy danych AdventureWorksLT dla programu SQL Server 2005. W dalszej części tego przewodnika będziesz odwoływać się tego zestawu danych z projektu skoroszytu programu Excel i projekt aplikacji konsoli.  
  
 Zestaw danych jest *typizowany zestaw danych* który reprezentuje dane w tabeli Product bazy danych AdventureWorksLT. Aby uzyskać więcej informacji na temat zestawów, zobacz [narzędzia zestawu danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Zdefiniuj typizowany zestaw danych w projekcie biblioteki klas  
  
1. W **Eksploratora rozwiązań**, kliknij przycisk **AdventureWorksDataSet** projektu.  
  
2. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.  
  
3. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
4. Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5. Jeśli masz istniejące połączenie z bazą danych AdventureWorksLT, wybierz to połączenie i kliknij przycisk **dalej**.  
  
    W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodaj połączenie** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
6. W **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.  
  
7. W **wybierz obiekty bazy danych** rozwiń **tabel** i wybierz **produktu (SalesLT)**.  
  
8. Kliknij przycisk **Zakończ**.  
  
    *AdventureWorksLTDataSet.xsd* plik zostanie dodany do **AdventureWorksDataSet** projektu. Ten plik definiuje następujące elementy:  
  
   - Typizowany zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość Tabela produktów w bazie danych AdventureWorksLT.  
  
   - TableAdapter o nazwie `ProductTableAdapter`. Ten obiekt TableAdapter można odczytywać i zapisywać dane `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Użyje obu tych obiektów w dalszej części tego przewodnika.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** i kliknij przycisk **kompilacji**.  
  
     Upewnij się, że projekt zostanie skompilowany bez błędów.  
  
## <a name="create-an-excel-workbook-project"></a>Utwórz projektu skoroszytu programu Excel  
 Utwórz projektu skoroszytu programu Excel dla interfejsu do danych. W dalszej części tego instruktażu utworzysz <xref:Microsoft.Office.Tools.Excel.ListObject> wyświetlającą dane, a wystąpienie zestawu danych zostanie dodany do pamięci podręcznej danych w skoroszycie.  
  
### <a name="create-the-excel-workbook-project"></a>Utwórz projektu skoroszytu programu Excel  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązań, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.  
  
3.  W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.  
  
4.  Na liście szablonów projektu wybierz **skoroszyt programu Excel 2010** lub **skoroszytu programu Excel 2013** projektu.  
  
5.  W **nazwa** wpisz **AdventureWorksReport**. Nie należy modyfikować lokalizacji.  
  
6.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.  
  
7.  Upewnij się, że **Utwórz nowy dokument** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **AdventureWorksReport** skoroszytu w Projektancie i dodaje **AdventureWorksReport** projekt **Eksploratora rozwiązań**.  
  
## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Dodaj zestaw danych do źródła danych w projekcie skoroszytu programu Excel  
 Aby wyświetlić zestaw danych w skoroszycie programu Excel, należy najpierw dodać zestaw danych ze źródłami danych w projekcie skoroszytu programu Excel.  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie *Sheet1.cs* lub *Sheet1.vb* w obszarze **AdventureWorksReport** projektu.  
  
     Skoroszyt zostanie otwarty w projektancie.  
  
2.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Kreatora konfiguracji źródła danych** zostanie otwarty.  
  
3.  Kliknij przycisk **obiektu**, a następnie kliknij przycisk **dalej**.  
  
4.  W **wybierz obiekt ma zostać powiązania** do strony, kliknij przycisk **Dodaj odwołanie**.  
  
5.  Na **projektów** kliknij pozycję **AdventureWorksDataSet** a następnie kliknij przycisk **OK**.  
  
6.  W obszarze **AdventureWorksDataSet** przestrzeń nazw **AdventureWorksDataSet** zestawu, kliknij przycisk **AdventureWorksLTDataSet** a następnie kliknij przycisk **Zakończ** .  
  
     **Źródeł danych** zostanie otwarte okno i **AdventureWorksLTDataSet** zostanie dodany do listy źródeł danych.  
  
## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Utwórz ListObject, który jest powiązany do wystąpienia zestawu danych  
 Aby wyświetlić zestaw danych w skoroszycie, Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> , jest powiązany do wystąpienia zestawu danych. Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
1.  W **źródeł danych** okna, rozwiń węzeł **AdventureWorksLTDataSet** węźle **AdventureWorksDataSet**.  
  
2.  Wybierz **produktu** węzła, kliknij strzałkę listy rozwijanej, która pojawia się, a następnie wybierz pozycję **ListObject** na liście rozwijanej.  
  
     Jeśli nie ma strzałkę listy rozwijanej, upewnij się, że skoroszyt jest otwarty w projektancie.  
  
3.  Przeciągnij **produktu** tabeli do komórki A1.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `productListObject` jest tworzony w arkuszu, począwszy od komórki A1. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `productBindingSource` są dodawane do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.  
  
## <a name="add-the-dataset-to-the-data-cache"></a>Dodaj zestaw danych do pamięci podręcznej danych  
 Aby włączyć kod poza projektu skoroszytu programu Excel do dostępu do zestawu danych w skoroszycie, należy dodać zestaw danych w pamięci podręcznej danych. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [dane dostosowywane na poziomie dokumentu z pamięci podręcznej](../vsto/cached-data-in-document-level-customizations.md) i [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
1.  W projektancie, kliknij **adventureWorksLTDataSet**.  
  
2.  W **właściwości** oknie **Modyfikatory** właściwości **publicznych**.  
  
3.  Ustaw **CacheInDocument** właściwości **True**.  
  
## <a name="initialize-the-dataset-in-the-workbook"></a>Zainicjuj zestaw danych w skoroszycie  
 Zanim będzie można pobrać danych z pamięci podręcznej zestawu danych za pomocą aplikacji konsoli, należy najpierw wypełnić buforowany zestaw danych z danymi.  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *Sheet1.cs* lub *Sheet1.vb* plik i kliknij przycisk **Wyświetl kod**.  
  
2.  Zastąp `Sheet1_Startup` programu obsługi zdarzeń z następującym kodem. Ten kod używa wystąpienia `ProductTableAdapter` klasy, która jest zdefiniowana w **AdventureWorksDataSet** projektu, aby wypełnić buforowany zestaw danych z danymi, jeśli jest obecnie pusty.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Kompilowanie i uruchamianie projektu skoroszytu programu Excel, aby upewnić się, że kompiluje i uruchamia bez błędów. Ta operacja również wypełnia buforowany zestaw danych i zapisuje dane w skoroszycie.  
  
### <a name="build-and-run-the-project"></a>Kompilowanie i uruchamianie projektu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksReport** projektu, wybierz **debugowania**, a następnie kliknij przycisk **Uruchom nowe wystąpienie**.  
  
     Projekt jest kompilowany i skoroszyt zostanie otwarty w programie Excel. Sprawdź następujące informacje:  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> Wypełnia przy użyciu danych.  
  
    -   Wartość w **ListPrice** kolumnie dla pierwszego wiersza <xref:Microsoft.Office.Tools.Excel.ListObject> jest 1431.5. W dalszej części tego przewodnika, użyjesz aplikacji konsoli, aby modyfikować wartości w **ListPrice** kolumny.  
  
2.  Zapisz skoroszyt. Nie zmieniaj nazwy pliku lub lokalizacji skoroszytu.  
  
3.  Zamknij program Excel.  
  
## <a name="create-a-console-application-project"></a>Utwórz projekt aplikacji konsoli  
 Utwórz projekt aplikacji konsoli, można używać do modyfikowania danych w pamięci podręcznej zestawu danych w skoroszycie.  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksDataSet** rozwiązań, wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **typów projektów** okienku rozwiń **Visual C#** lub **języka Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3.  W **szablony** okienku wybierz **aplikację Konsolową**.  
  
4.  W **nazwa** wpisz **DataReader**. Nie należy modyfikować lokalizacji.  
  
5.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **DataReader** projekt **Eksploratora rozwiązań** i otwiera *Program.cs* lub *Module1.vb* pliku kodu.  
  
## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Pobierać dane z pamięci podręcznej zestawu danych przy użyciu aplikacji konsoli  
 Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w aplikacji konsoli, aby odczytać dane lokalnie `AdventureWorksLTDataSet` obiektu. Aby upewnić się, że lokalnego zestawu danych został zainicjowany przy użyciu danych z pamięci podręcznej zestawu danych, aplikacja wyświetla liczbę wierszy w zestawie danych lokalnych.  
  
### <a name="retrieve-data-from-the-cached-dataset"></a>Pobieranie danych z pamięci podręcznej zestawu danych  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataReader** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
2. Na **.NET** zaznacz **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3. Kliknij przycisk **OK**.  
  
4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataReader** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
5. Na **projektów** zaznacz **AdventureWorksDataSet**i kliknij przycisk **OK**.  
  
6. Otwórz *Program.cs* lub *Module1.vb* plik w edytorze kodu.  
  
7. Dodaj następujący kod **przy użyciu** (dla C#) lub **Importy** (dla języka Visual Basic) instrukcji na górze pliku kodu.  
  
    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8. Dodaj następujący kod do `Main` metody. Ten kod deklaruje następujące obiekty:  
  
   - Wystąpienie `AdventureWorksLTDataSet` typu, który jest zdefiniowany w **AdventureWorksDataSet** projektu.  
  
   - Ścieżka do skoroszytu AdventureWorksReport w folderze kompilacji testowanego **AdventureWorksReport** projektu.  
  
   - A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> obiekt na potrzeby dostępu do pamięci podręcznej danych w skoroszycie.  
  
     > [!NOTE]  
     >  Poniższy kod zakłada, że skoroszyt jest zapisywany przy użyciu *xlsx* rozszerzenia. Jeśli skoroszyt w projekcie ma inne rozszerzenie, zmodyfikuj ścieżkę zgodnie z potrzebami.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Dodaj następujący kod do `Main` metoda po kodzie dodanym w poprzednim kroku. Kod będzie wykonywał następujące zadania:  
  
   - Używa ona <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> właściwość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w celu dostępu do pamięci podręcznej zestawu danych w skoroszycie.  
  
   - Odczytuje dane z pamięci podręcznej zestawu danych do lokalnego zestawu danych.  
  
   - Wyświetla liczbę wierszy w zestawie danych lokalnych, aby upewnić się, że zawiera on danych.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. Na **kompilacji** menu, kliknij przycisk **Tworzenie elementu DataReader**.  
  
## <a name="test-the-project"></a>Projekt testowy  
 Po uruchomieniu aplikacji konsoli, wyświetla liczbę wierszy w zestawie danych lokalnych.  
  
### <a name="test-the-workbook"></a>Testowanie skoroszytu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DataReader** projekt, wskaż opcję **debugowania**, a następnie kliknij przycisk **Uruchom nowe wystąpienie**.  
  
     Upewnij się, że aplikacja zgłasza, że lokalny zestaw danych zawiera objęto 295 wierszy.  
  
2.  Naciśnij klawisz **Enter** aby zamknąć aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej o pracy z pamięci podręcznej danych w tych tematach:  
  
-   Modyfikowanie danych w pamięci podręcznej zestawu danych bez konieczności uruchamiania programu Excel. Aby uzyskać więcej informacji, zobacz [wskazówki: Zmiana pamięci podręcznej danych ze skoroszytu na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki: Wstawianie danych do skoroszytu na serwerze](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Wskazówki: Zmiana danych w pamięci podręcznej ze skoroszytu na serwerze](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
  
  