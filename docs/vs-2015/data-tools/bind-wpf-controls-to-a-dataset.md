---
title: Powiązywanie kontrolek WPF z zestawem danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 663665c77a966d793930326ae04f8d30c71de771
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665522"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Powiązywanie kontrolek WPF z zestawem danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz aplikację WPF, która zawiera formanty powiązane z danymi. Formanty są powiązane z rekordów produktu, które są hermetyzowane w zestawie danych. Zostanie również dodać przyciski, za pośrednictwem produktów i zapisać zmiany do rekordów produktu.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie aplikacji WPF i zestaw danych, który jest generowany na podstawie danych w przykładowej bazie danych AdventureWorksLT.  
  
- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie tabelę danych z **źródeł danych** okna do okna Projektanta WPF.  
  
- Tworzenie przycisków, które przejdź do przodu i wstecz za pośrednictwem rekordów produktu.  
  
- Tworzenie przycisku, który zapisuje zmiany wprowadzone przez użytkownika do rekordów produkt do tabeli danych i źródle danych.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który ma przykładowej bazy danych AdventureWorksLT podłączone do niego. Możesz pobrać bazy danych AdventureWorksLT z [witryny sieci CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończeni instruktażu:  
  
- Zestawy danych i adapterów TableAdapter. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
- Praca z projektanta WPF. Aby uzyskać więcej informacji, zobacz [WPF i Silverlight projektanta Przegląd](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Utwórz nowy projekt WPF. Projekt zostanie wyświetlona rekordy produktu.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  Rozwiń **języka Visual Basic** lub **Visual C#**, a następnie wybierz pozycję **Windows**.  
  
4.  Wybierz **aplikacji WPF** szablonu projektu.  
  
5.  W **nazwa** wpisz `AdventureWorksProductsEditor` i kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy `AdventureWorksProductsEditor` projektu.  
  
## <a name="create-a-dataset-for-the-application"></a>Tworzenie zestawu danych dla aplikacji  
 Można było utworzyć formanty powiązane z danymi, należy zdefiniować modelu danych dla aplikacji i dodać go do **źródeł danych** okna. W tym instruktażu utworzysz zestaw danych do użycia jako modelu danych.  
  
#### <a name="to-create-a-dataset"></a>Aby utworzyć zestaw danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
     **Źródeł danych** zostanie otwarte okno.  
  
2.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Konfiguracji źródła danych** zostanie otwarty Kreator.  
  
3.  Na **wybierz typ źródła danych** wybierz opcję **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz Model bazy danych** wybierz opcję **Dataset**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz połączenie danych** zaznacz jedną z następujących opcji:  
  
    -   Jeśli połączenie danych z przykładowej bazy danych AdventureWorksLT jest dostępny na liście rozwijanej, wybierz ją, a następnie kliknij przycisk **dalej**.  
  
    -   Kliknij przycisk **nowe połączenie**i Utwórz połączenie z bazą danych AdventureWorksLT.  
  
6.  Na **Zapisz parametry połączenia do pliku konfiguracyjnym aplikacji** wybierz opcję **tak, Zapisz połączenie jako** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
7.  Na **wybierz obiekty bazy danych** rozwiń **tabel**, a następnie wybierz pozycję **produktu (SalesLT)** tabeli.  
  
8.  Kliknij przycisk **Zakończ**.  
  
     Program Visual Studio dodaje nowy plik AdventureWorksLTDataSet.xsd do projektu, a następnie dodaje odpowiadające **AdventureWorksLTDataSet** elementu do **źródeł danych** okna. Plik AdventureWorksLTDataSet.xsd definiuje typizowany zestaw danych o nazwie `AdventureWorksLTDataSet` i TableAdapter o nazwie `ProductTableAdapter`. W dalszej części tego przewodnika, użyjesz `ProductTableAdapter` wypełnić dataset z danymi i zapisać zmiany w bazie danych.  
  
9. Skompiluj projekt.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edytuj domyślną metodę wypełnienia TableAdapter  
 Aby wypełnić dataset z danymi, należy użyć `Fill` metody `ProductTableAdapter`. Domyślnie `Fill` wypełnienia metoda `ProductDataTable` w `AdventureWorksLTDataSet` wszystkich wierszy danych w tabeli Product. Możesz zmodyfikować tę metodę, aby zwrócić tylko podzestaw wierszy. W ramach tego przewodnika należy zmodyfikować `Fill` metodę, aby zwracać tylko wiersze, dla produktów, które mają zdjęcia.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Aby załadować produktu wiersze, w których zdjęcia  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik AdventureWorksLTDataSet.xsd.  
  
     Zostanie otwarty projektant zestawu danych.  
  
2.  W projektancie, kliknij prawym przyciskiem myszy **Fill,GetData()** zapytania, a następnie wybierz pozycję **Konfiguruj**.  
  
     **Konfiguracji TableAdapter** zostanie otwarty Kreator.  
  
3.  W **wprowadź instrukcję SQL** strony, należy dodać następującą klauzulę WHERE po `SELECT` instrukcji w polu tekstowym.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Kliknij przycisk **Zakończ**.  
  
## <a name="define-the-user-interface"></a>Definiowanie interfejsu użytkownika  
 Dodaj kilku przycisków do okna, modyfikując XAML w Projektancie WPF. W dalszej części tego przewodnika należy dodać kod, który umożliwia przewijanie za pośrednictwem, a następnie zapisz zmiany rekordów produktów za pomocą tych przycisków.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Aby zdefiniować interfejs użytkownika okna  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie opcję MainWindow.xaml.  
  
     Okno zostanie otwarty w Projektancie WPF.  
  
2.  W [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] wyświetlić projektanta, Dodaj następujący kod między `<Grid>` tagi:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Skompiluj projekt.  
  
## <a name="createdata-bound-controls"></a>Formanty powiązane z Createdata  
 Tworzenie formantów, które wyświetlają rekordy klientów, przeciągając `Product` tabeli **źródeł danych** okna Projektanta WPF.  
  
#### <a name="to-create-data-bound-controls"></a>Aby utworzyć formanty powiązane z danymi  
  
1.  W **źródeł danych** okna, kliknij przycisk menu rozwijanej dla **produktu** a następnie wybierz węzeł **szczegóły**.  
  
2.  Rozwiń **produktu** węzła.  
  
3.  Na przykład niektóre pola nie zostaną wyświetlone, więc kliknij menu rozwijane obok następujących węzłów i wybierz pozycję **Brak**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   ROWGUID  
  
    -   Data modyfikacji  
  
4.  Kliknij menu rozwijane **thumbnailphoto usługa** a następnie wybierz węzeł **obraz**.  
  
    > [!NOTE]
    >  Domyślnie elementów w **źródeł danych** okna, które reprezentują obrazy mają ich domyślny formant równa **Brak**. Jest to spowodowane obrazy są przechowywane jako tablice bajtów w bazach danych i tablice bajtów może zawierać wszystko, od prostej tablicy bajtów do pliku wykonywalnego dużych aplikacji.  
  
5.  Z **źródeł danych** okna, przeciągnij **produktu** węzeł, aby wiersz siatki w ramach wiersza, który zawiera przyciski.  
  
     Program Visual Studio generuje XAML, który definiuje zestaw elementów sterujących, które są powiązane z danymi w **produktów** tabeli. Generuje kod, który służy do ładowania danych. Aby uzyskać więcej informacji na temat wygenerowany XAML i kodu, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  W projektancie, kliknij pole tekstowe **identyfikator produktu** etykiety.  
  
7.  W **właściwości** okna, zaznacz pole wyboru obok pozycji **IsReadOnly** właściwości.  
  
## <a name="navigating-product-records"></a>Nawigowania między rekordami produktu  
 Dodaj kod, który umożliwia użytkownikom do przewijania rekordów produktu przy użyciu **\<** i **>** przycisków.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Aby umożliwić użytkownikom przechodzenie rekordy produktu  
  
1.  W projektancie, kliknij dwukrotnie **<** przycisku na powierzchni okna.  
  
     Visual Studio otwiera plik CodeBehind i tworzy nowy `backButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2.  Modyfikowanie `Window_Loaded` procedura obsługi zdarzeń, więc `ProductViewSource`, `AdventureWorksLTDataSet`, i `AdventureWorksLTDataSetProductTableAdapter` są poza metodą i dostępne dla całego formularza. Zadeklaruj tylko żeby znajdowały się one globalne do formularza i przypisz je w ramach `Window_Loaded` obsługi zdarzeń jest podobny do następującego:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  Dodaj następujący kod do `backButton_Click` program obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  Wróć do projektanta i kliknij dwukrotnie plik **>** przycisku.  
  
5.  Dodaj następujący kod do `nextButton_Click` program obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>Funkcja SaveChanges zapisuje do rekordów produktu  
 Dodaj kod, który umożliwia użytkownikom zapisać zmiany rekordów produktu przy użyciu **Zapisz zmiany** przycisku.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Dodanie możliwości, aby zapisać zmiany do rekordów produktu  
  
1.  W projektancie, kliknij dwukrotnie **Zapisz zmiany** przycisku.  
  
     Visual Studio otwiera plik CodeBehind i tworzy nowy `saveButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2.  Dodaj następujący kod do `saveButton_Click` program obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  W tym przykładzie użyto `Save` metody `TableAdapter` Aby zapisać zmiany. Ta opcja jest odpowiednia w tym przewodniku, ponieważ tylko jeden danych tabeli został zmieniony. Jeśli potrzebujesz zapisać zmiany z wieloma tabelami danych, można też użyć `UpdateAll` metody `TableAdapterManager` generujący programu Visual Studio przy użyciu zestawu danych. Aby uzyskać więcej informacji, zobacz [TableAdapterManager — Przegląd](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Skompiluj i uruchom aplikację. Sprawdź, czy można wyświetlać i aktualizować rekordy produktu.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz **F5**.  
  
     Aplikacja zostanie skompilowana i działa. Sprawdź następujące informacje:  
  
    -   Pola tekstowe są wyświetlane dane z pierwszego rekordu produktu, który ma zdjęcie. Ten produkt ma produktu 713 identyfikator i nazwę **długich koszulka z Logo rękaw, S**.  
  
    -   Możesz kliknąć pozycję **>** lub **<** przycisków, aby przejść do innych rekordów produktu.  
  
2.  Z jednego z rekordów produktu, należy zmienić **rozmiar** wartość, a następnie kliknij przycisk **Zapisz zmiany**.  
  
3.  Zamknij aplikację, a następnie ponownie uruchom aplikację, naciskając klawisz **F5** w programie Visual Studio.  
  
4.  Przejdź do rekordu produktu, który został zmieniony i sprawdź, czy utrwalone zmiany.  
  
5.  Zamknij aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, należy wykonać następujące zadania:  
  
-   Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby powiązać WPF formanty do innych typów źródeł danych. Aby uzyskać więcej informacji, zobacz [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby wyświetlić powiązane dane (czyli w relacji nadrzędny podrzędny) w formantach WPF. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Omówienie projektanta Silverlight i WPF](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Powiązanie danych — omówienie](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
