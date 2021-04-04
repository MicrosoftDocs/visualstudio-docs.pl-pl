---
title: Powiązywanie kontrolek WPF z zestawem danych
description: Utwórz aplikację WPF w programie Visual Studio, która zawiera kontrolki powiązane z danymi, które są powiązane z rekordami produktów, które są hermetyzowane w zestawie danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b67e70792f6e7864749b603f30ab868ef177336a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215568"
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

- Visual Studio

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express, które ma dołączoną przykładową bazę danych AdventureWorks Light (AdventureWorksLT). Bazę danych AdventureWorksLT można pobrać z [archiwum CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Wcześniejsza znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończenia przewodnika:

- Zestawy danych i TableAdapters. Aby uzyskać więcej informacji, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) i [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Tworzenie projektu

Utwórz nowy projekt WPF do wyświetlania rekordów produktów.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. W menu **Plik** wybierz pozycję **Nowy** > **Projekt**.

3. Rozwiń węzeł **Visual Basic** lub **Visual C#**, a następnie wybierz pozycję **Windows**.

4. Wybierz szablon projektu **aplikacji WPF** .

5. W polu **Nazwa** wprowadź **AdventureWorksProductsEditor** , a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Wyszukaj szablon projektu **aplikacji WPF** w języku C# i postępuj zgodnie z instrukcjami, aby utworzyć projekt, nadając nazwę projektu **AdventureWorksProductsEditor**.

::: moniker-end

   Program Visual Studio tworzy projekt AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Tworzenie zestawu danych dla aplikacji

Aby można było tworzyć kontrolki powiązane z danymi, należy zdefiniować model danych dla aplikacji i dodać go do okna **źródła danych** . W tym instruktażu utworzysz zestaw danych, który będzie używany jako model danych.

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

   Zostanie otwarty Kreator **konfiguracji źródła danych** .

3. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz model bazy danych** wybierz pozycję **zestaw danych**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wybierz jedną z następujących opcji:

   - Jeśli połączenie danych z przykładową bazą danych AdventureWorksLT jest dostępne na liście rozwijanej, wybierz ją, a następnie kliknij przycisk **dalej**.

   - Kliknij pozycję **nowe połączenie** i Utwórz połączenie z bazą danych AdventureWorksLT.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** zaznacz pole wyboru **tak, Zapisz połączenie jako** , a następnie kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**, a następnie wybierz tabelę **Product (tabeli SalesLT)** .

8. Kliknij przycisk **Finish** (Zakończ).

   Program Visual Studio dodaje nowy `AdventureWorksLTDataSet.xsd` plik do projektu i dodaje odpowiedni element **AdventureWorksLTDataSet** do okna **źródła danych** . `AdventureWorksLTDataSet.xsd`Plik definiuje określony zestaw danych o nazwie `AdventureWorksLTDataSet` i TableAdapter o nazwie `ProductTableAdapter` . W dalszej części tego instruktażu zostanie użyta funkcja `ProductTableAdapter` do wypełnienia zestawu danych danymi i zapisania zmian z powrotem w bazie danych.

9. Skompiluj projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edytuj domyślną metodę Fill elementu TableAdapter

Aby wypełnić zestaw danych danymi, użyj `Fill` metody `ProductTableAdapter` . Domyślnie `Fill` Metoda wypełnia `ProductDataTable` w programie `AdventureWorksLTDataSet` wszystkie wiersze danych z tabeli Product. Możesz zmodyfikować tę metodę, aby zwrócić tylko podzestaw wierszy. W tym instruktażu zmodyfikuj `Fill` metodę, aby zwracała tylko wiersze dla produktów mających zdjęcia.

1. W **Eksplorator rozwiązań** kliknij dwukrotnie plik *AdventureWorksLTDataSet. xsd* .

     Zostanie otwarty projektant obiektów DataSet.

2. W projektancie kliknij prawym przyciskiem myszy zapytanie **wypełnienie**, **GetData ()** i wybierz pozycję **Konfiguruj**.

     Zostanie otwarty Kreator **konfiguracji TableAdapter** .

3. Na stronie **wprowadzanie instrukcji SQL** Dodaj następującą klauzulę WHERE po `SELECT` instrukcji w polu tekstowym.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Kliknij przycisk **Finish** (Zakończ).

## <a name="define-the-user-interface"></a>Zdefiniuj interfejs użytkownika

Dodaj kilka przycisków do okna, modyfikując kod XAML w projektancie WPF. W dalszej części tego instruktażu zostanie dodany kod umożliwiający użytkownikom przewijanie i zapisywanie zmian w rekordach produktów przy użyciu tych przycisków.

1. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję *MainWindow. XAML*.

    Okno zostanie otwarte w **projektancie WPF**.

2. W [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] widoku projektanta Dodaj następujący kod między `<Grid>` tagami:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75">&lt;</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">&gt;</Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Skompiluj projekt.

## <a name="create-data-bound-controls"></a>Tworzenie formantów powiązanych z danymi

Utwórz kontrolki, które wyświetlają rekordy klientów, przeciągając `Product` tabelę z okna **źródła danych** do projektanta WPF.

1. W oknie **źródła danych** kliknij menu rozwijane dla węzła **produkt** i wybierz polecenie **szczegóły**.

2. Rozwiń węzeł **produkt** .

3. W tym przykładzie niektóre pola nie będą wyświetlane, więc kliknij menu rozwijane obok następujących węzłów i wybierz opcję **Brak**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - danej

    - ModifiedDate

4. Kliknij menu rozwijane obok węzła **ThumbNailPhoto** i wybierz pozycję **obraz**.

    > [!NOTE]
    > Domyślnie elementy w oknie **źródła danych** , które reprezentują obrazy, mają ustawioną domyślną kontrolkę **none**. Dzieje się tak dlatego, że obrazy są przechowywane jako tablice bajtów w bazach danych, a tablice bajtowe mogą zawierać dowolne elementy z prostej tablicy bajtów do pliku wykonywalnego dużej aplikacji.

5. W oknie **źródła danych** przeciągnij węzeł **produktu** do wiersza siatki w wierszu, który zawiera przyciski.

     Program Visual Studio generuje kod XAML, który definiuje zestaw kontrolek, które są powiązane z danymi w tabeli **Products** . Generuje również kod, który ładuje dane. Aby uzyskać więcej informacji na temat wygenerowanej XAML i kodu, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. W projektancie kliknij pole tekstowe obok etykiety **Identyfikator produktu** .

7. W oknie **Właściwości** zaznacz pole wyboru obok właściwości **IsReadOnly** .

## <a name="navigate-product-records"></a>Przejdź do rekordu produktu

Dodaj kod, który umożliwia użytkownikom przewijanie rekordów produktów za pomocą **\<** and **>** przycisków.

1. W projektancie kliknij dwukrotnie **<** przycisk na powierzchni okna.

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `backButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Zmodyfikuj `Window_Loaded` procedurę obsługi zdarzeń, a więc `ProductViewSource` , `AdventureWorksLTDataSet` , i, `AdventureWorksLTDataSetProductTableAdapter` znajdują się poza metodą i dostępną dla całego formularza. Zadeklaruj tylko te, które mają być globalne dla formularza, i przypisz je w ramach `Window_Loaded` procedury obsługi zdarzeń podobne do następujących:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet1":::

3. Dodaj następujący kod do `backButton_Click` programu obsługi zdarzeń:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet2":::

4. Wróć do projektanta i kliknij dwukrotnie **>** przycisk.

5. Dodaj następujący kod do `nextButton_Click` programu obsługi zdarzeń:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet3":::

## <a name="save-changes-to-product-records"></a>Zapisz zmiany w rekordach produktu

Dodaj kod, który umożliwia użytkownikom zapisywanie zmian w rekordach produktu przy użyciu przycisku **Zapisz zmiany** .

1. W projektancie kliknij dwukrotnie przycisk **Zapisz zmiany** .

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `saveButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Dodaj następujący kod do `saveButton_Click` programu obsługi zdarzeń:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet4":::

    > [!NOTE]
    > W tym przykładzie zastosowano `Save` metodę, `TableAdapter` Aby zapisać zmiany. Jest to odpowiednie w tym instruktażu, ponieważ zmieniana jest tylko jedna tabela danych. Jeśli zachodzi potrzeba zapisania zmian w wielu tabelach danych, można alternatywnie użyć `UpdateAll` metody `TableAdapterManager` , która generuje program Visual Studio z zestawem danych. Aby uzyskać więcej informacji, zobacz [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testowanie aplikacji

Skompiluj i uruchom aplikację. Sprawdź, czy można wyświetlać i aktualizować rekordy produktów.

1. Naciśnij klawisz **F5**.

     Aplikacja zostanie skompilowana i uruchomiona. Sprawdź następujące informacje:

    - Pola tekstowe wyświetlają dane z pierwszego rekordu produktu, który ma zdjęcie. Ten produkt ma identyfikator produktu 713, a nazwa w **logo z długą cyfrą**().

    - Możesz kliknąć przycisk **>** lub, **<** Aby nawigować po innych rekordach produktu.

2. W jednym z rekordów produktu Zmień wartość w polu **rozmiar** , a następnie kliknij przycisk **Zapisz zmiany**.

3. Zamknij aplikację, a następnie uruchom ponownie aplikację, naciskając klawisz **F5** w programie Visual Studio.

4. Przejdź do rekordu produktu, który został zmieniony, i sprawdź, czy zmiana została utrwalona.

5. Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tego instruktażu można wypróbować następujące powiązane zadania:

- Dowiedz się, jak za pomocą okna **źródła danych** w programie Visual Studio POWIĄZAĆ formanty WPF z innymi typami źródeł danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Dowiedz się, jak używać okna **źródła danych** w programie Visual Studio, aby wyświetlić powiązane dane (czyli dane w relacji nadrzędny-podrzędny) w kontrolkach WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Przegląd powiązań danych](/dotnet/desktop-wpf/data/data-binding-overview)
