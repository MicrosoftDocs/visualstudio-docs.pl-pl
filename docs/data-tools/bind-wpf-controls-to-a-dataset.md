---
title: Powiązywanie kontrolek WPF z zestawem danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8de276bfb6d7ec8bc36380ee41d86de07fc8dd74
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586981"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Powiązywanie kontrolek WPF z zestawem danych

W tym instruktażu utworzysz aplikację WPF, która zawiera kontrolki powiązane z danymi. Formanty są powiązane z rekordami produktów, które są hermetyzowane w zestawie danych. Dodano również przyciski umożliwiające przeglądanie produktów i zapisywanie zmian w rekordach produktów.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie aplikacji WPF i zestawu danych, który jest generowany na podstawie danych z przykładowej bazy danych AdventureWorksLT.

- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie tabeli danych z okna **źródła danych** do okna w projektancie WPF.

- Tworzenie przycisków umożliwiających nawigowanie do przodu i do tyłu za poorednictwem rekordów produktów.

- Tworzenie przycisku, który zapisuje zmiany wprowadzane przez użytkowników w rekordach produktu do tabeli danych i bazowego źródła danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- {1&gt;Visual Studio&lt;1}

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express, które ma dołączoną przykładową bazę danych AdventureWorks Light (AdventureWorksLT). Bazę danych AdventureWorksLT można pobrać z [archiwum CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Wcześniejsza znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończenia przewodnika:

- Zestawy danych i TableAdapters. Aby uzyskać więcej informacji, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) i [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Utwórz projekt

Utwórz nowy projekt WPF do wyświetlania rekordów produktów.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. W menu **plik** wybierz pozycję **Nowy** **projekt**>.

3. Rozwiń węzeł **Visual Basic** lub **Wizualizacja C#** , a następnie wybierz pozycję **Windows**.

4. Wybierz szablon projektu **aplikacji WPF** .

5. W polu **Nazwa** wprowadź **AdventureWorksProductsEditor** , a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. C# Wyszukaj szablon projektu **aplikacji WPF** i postępuj zgodnie z instrukcjami, aby utworzyć projekt, nadając nazwę projektu **AdventureWorksProductsEditor**.

::: moniker-end

   Program Visual Studio tworzy projekt AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Tworzenie zestawu danych dla aplikacji

Aby można było tworzyć kontrolki powiązane z danymi, należy zdefiniować model danych dla aplikacji i dodać go do okna **źródła danych** . W tym instruktażu utworzysz zestaw danych, który będzie używany jako model danych.

1. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

   Zostanie otwarty Kreator **konfiguracji źródła danych** .

3. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz model bazy danych** wybierz pozycję **zestaw danych**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wybierz jedną z następujących opcji:

   - Jeśli połączenie danych z przykładową bazą danych AdventureWorksLT jest dostępne na liście rozwijanej, wybierz ją, a następnie kliknij przycisk **dalej**.

   - Kliknij pozycję **nowe połączenie**i Utwórz połączenie z bazą danych AdventureWorksLT.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** zaznacz pole wyboru **tak, Zapisz połączenie jako** , a następnie kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**, a następnie wybierz tabelę **Product (tabeli SalesLT)** .

8. Kliknij przycisk **Zakończ**.

   Program Visual Studio dodaje nowy plik `AdventureWorksLTDataSet.xsd` do projektu i dodaje odpowiedni element **AdventureWorksLTDataSet** do okna **źródła danych** . Plik `AdventureWorksLTDataSet.xsd` definiuje typ zestawu danych o nazwie `AdventureWorksLTDataSet` i TableAdapter o nazwie `ProductTableAdapter`. W dalszej części tego instruktażu użyjesz `ProductTableAdapter`, aby wypełnić zestaw danych danymi i zapisać zmiany z powrotem w bazie danych.

9. Skompiluj projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edytuj domyślną metodę Fill elementu TableAdapter

Aby wypełnić zestaw danych danymi, użyj metody `Fill` `ProductTableAdapter`. Domyślnie metoda `Fill` wypełnia `ProductDataTable` w `AdventureWorksLTDataSet` ze wszystkimi wierszami danych z tabeli Product. Możesz zmodyfikować tę metodę, aby zwrócić tylko podzestaw wierszy. W tym instruktażu zmodyfikuj metodę `Fill`, aby zwracała tylko wiersze dla produktów mających zdjęcia.

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik *AdventureWorksLTDataSet. xsd* .

     Zostanie otwarty projektant obiektów DataSet.

2. W projektancie kliknij prawym przyciskiem myszy zapytanie **wypełnienie**, **GetData ()** i wybierz pozycję **Konfiguruj**.

     Zostanie otwarty Kreator **konfiguracji TableAdapter** .

3. Na stronie **wprowadzanie instrukcji SQL** Dodaj następującą klauzulę WHERE po instrukcji `SELECT` w polu tekstowym.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Kliknij przycisk **Zakończ**.

## <a name="define-the-user-interface"></a>Zdefiniuj interfejs użytkownika

Dodaj kilka przycisków do okna, modyfikując kod XAML w projektancie WPF. W dalszej części tego instruktażu zostanie dodany kod umożliwiający użytkownikom przewijanie i zapisywanie zmian w rekordach produktów przy użyciu tych przycisków.

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję *MainWindow. XAML*.

    Okno zostanie otwarte w **projektancie WPF**.

2. W widoku [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] projektanta Dodaj następujący kod między tagami `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Skompiluj projekt.

## <a name="create-data-bound-controls"></a>Tworzenie formantów powiązanych z danymi

Utwórz kontrolki, które wyświetlają rekordy klientów, przeciągając tabelę `Product` z okna **źródła danych** do projektanta WPF.

1. W oknie **źródła danych** kliknij menu rozwijane dla węzła **produkt** i wybierz polecenie **szczegóły**.

2. Rozwiń węzeł **produkt** .

3. W tym przykładzie niektóre pola nie będą wyświetlane, więc kliknij menu rozwijane obok następujących węzłów i wybierz opcję **Brak**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - ROWGUID

    - Data modyfikacji

4. Kliknij menu rozwijane obok węzła **ThumbNailPhoto** i wybierz pozycję **obraz**.

    > [!NOTE]
    > Domyślnie elementy w oknie **źródła danych** , które reprezentują obrazy, mają ustawioną domyślną kontrolkę **none**. Dzieje się tak dlatego, że obrazy są przechowywane jako tablice bajtów w bazach danych, a tablice bajtowe mogą zawierać dowolne elementy z prostej tablicy bajtów do pliku wykonywalnego dużej aplikacji.

5. W oknie **źródła danych** przeciągnij węzeł **produktu** do wiersza siatki w wierszu, który zawiera przyciski.

     Program Visual Studio generuje kod XAML, który definiuje zestaw kontrolek, które są powiązane z danymi w tabeli **Products** . Generuje również kod, który ładuje dane. Aby uzyskać więcej informacji na temat wygenerowanej XAML i kodu, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. W projektancie kliknij pole tekstowe obok etykiety **Identyfikator produktu** .

7. W oknie **Właściwości** zaznacz pole wyboru obok właściwości **IsReadOnly** .

## <a name="navigate-product-records"></a>Przejdź do rekordu produktu

Dodaj kod, który umożliwia użytkownikom przewijanie rekordów produktów za pomocą przycisków **\<** i **>** .

1. W projektancie kliknij dwukrotnie przycisk **<** na powierzchni okna.

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy program obsługi zdarzeń `backButton_Click` dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Zmodyfikuj procedurę obsługi zdarzeń `Window_Loaded`, więc `ProductViewSource`, `AdventureWorksLTDataSet`i `AdventureWorksLTDataSetProductTableAdapter` znajdują się poza metodą i są dostępne dla całego formularza. Zadeklaruj tylko te, które mają być globalne dla formularza, i przypisz je w ramach procedury obsługi zdarzeń `Window_Loaded`, podobne do następujących:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Dodaj następujący kod do programu obsługi zdarzeń `backButton_Click`:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Wróć do projektanta i kliknij dwukrotnie przycisk **>** .

5. Dodaj następujący kod do programu obsługi zdarzeń `nextButton_Click`:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Zapisz zmiany w rekordach produktu

Dodaj kod, który umożliwia użytkownikom zapisywanie zmian w rekordach produktu przy użyciu przycisku **Zapisz zmiany** .

1. W projektancie kliknij dwukrotnie przycisk **Zapisz zmiany** .

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy program obsługi zdarzeń `saveButton_Click` dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Dodaj następujący kod do programu obsługi zdarzeń `saveButton_Click`:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > W tym przykładzie zastosowano metodę `Save` `TableAdapter`, aby zapisać zmiany. Jest to odpowiednie w tym instruktażu, ponieważ zmieniana jest tylko jedna tabela danych. Jeśli zachodzi potrzeba zapisania zmian w wielu tabelach danych, można użyć metody `UpdateAll` `TableAdapterManager`, którą program Visual Studio generuje wraz z zestawem danych. Aby uzyskać więcej informacji, zobacz [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testowanie aplikacji

Skompiluj i uruchom aplikację. Sprawdź, czy można wyświetlać i aktualizować rekordy produktów.

1. Naciśnij klawisz **F5**.

     Aplikacja zostanie skompilowana i uruchomiona. Sprawdź następujące informacje:

    - Pola tekstowe wyświetlają dane z pierwszego rekordu produktu, który ma zdjęcie. Ten produkt ma identyfikator produktu 713, a nazwa w **logo z długą cyfrą**().

    - Możesz kliknąć przycisk **>** lub **<** , aby nawigować po innych rekordach produktu.

2. W jednym z rekordów produktu Zmień wartość w polu **rozmiar** , a następnie kliknij przycisk **Zapisz zmiany**.

3. Zamknij aplikację, a następnie uruchom ponownie aplikację, naciskając klawisz **F5** w programie Visual Studio.

4. Przejdź do rekordu produktu, który został zmieniony, i sprawdź, czy zmiana została utrwalona.

5. Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tego instruktażu można wypróbować następujące powiązane zadania:

- Dowiedz się, jak za pomocą okna **źródła danych** w programie Visual Studio POWIĄZAĆ formanty WPF z innymi typami źródeł danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Dowiedz się, jak używać okna **źródła danych** w programie Visual Studio, aby wyświetlić powiązane dane (czyli dane w relacji nadrzędny-podrzędny) w kontrolkach WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Powiązanie danych — omówienie](/dotnet/desktop-wpf/data/data-binding-overview)
