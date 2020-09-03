---
title: Powiązywanie kontrolek WPF z usługą danych programu WCF
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7371e08925ad9227cf15a93a339e6e0ed36d11db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282855"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Powiązywanie kontrolek WPF z usługą danych programu WCF

W tym instruktażu utworzysz aplikację WPF, która zawiera kontrolki powiązane z danymi. Formanty są powiązane z rekordami klientów, które są hermetyzowane w usłudze danych programu WCF. Dodasz również przyciski, za pomocą których klienci mogą wyświetlać i aktualizować rekordy.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie Entity Data Model wygenerowanego na podstawie danych z przykładowej bazy danych AdventureWorksLT.

- Tworzenie usługi danych programu WCF, która uwidacznia dane w Entity Data Model w aplikacji WPF.

- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie elementów z okna **źródła danych** do projektanta WPF.

- Tworzenie przycisków przechodzenia do przodu i do tyłu przez rekordy klientów.

- Tworzenie przycisku, który zapisuje zmiany danych w kontrolkach do usługi danych programu WCF i bazowego źródła danych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express z dołączoną przykładową bazą danych AdventureWorksLT. Bazę danych AdventureWorksLT można pobrać z [witryny sieci Web CodePlex](https://archive.codeplex.com/?p=SqlServerSamples).

Wcześniejsza znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończenia przewodnika:

- [Usługi danych programu WCF](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modele danych w programie [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] .

- Modele danych jednostek i Entity Framework ADO.NET. Aby uzyskać więcej informacji, zobacz [Entity Framework przegląd](/dotnet/framework/data/adonet/ef/overview).

- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Tworzenie projektu usługi

1. Rozpocznij ten przewodnik, tworząc projekt **aplikacji sieci Web** w języku C# lub Visual Basic ASP.NET. Nazwij projekt **AdventureWorksService**.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **default. aspx** i wybierz pozycję **Usuń**. Ten plik nie jest konieczny dla przewodnika.

## <a name="create-an-entity-data-model-for-the-service"></a>Tworzenie Entity Data Model dla usługi

Aby udostępnić dane aplikacji przy użyciu usługi danych programu WCF, należy zdefiniować model danych dla usługi. Usługa danych programu WCF obsługuje dwa typy modeli danych: modele danych jednostek i niestandardowe modele danych, które są zdefiniowane przy użyciu obiektów środowiska uruchomieniowego języka wspólnego (CLR), które implementują <xref:System.Linq.IQueryable%601> interfejs. W tym instruktażu utworzysz Entity Data Model dla modelu danych.

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. Na liście zainstalowane szablony kliknij pozycję **dane**, a następnie wybierz element projektu **ADO.NET Entity Data Model** .

3. Zmień nazwę na `AdventureWorksModel.edmx` , a następnie kliknij przycisk **Dodaj**.

     Zostanie otwarty Kreator **Entity Data Model** .

4. Na stronie **Wybierz zawartość modelu** kliknij pozycję **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wybierz jedną z następujących opcji:

    - Jeśli połączenie danych z przykładową bazą danych AdventureWorksLT jest dostępne na liście rozwijanej, wybierz ją.

    - Kliknij pozycję **nowe połączenie**i Utwórz połączenie z bazą danych AdventureWorksLT.

6. Na stronie **Wybierz połączenie danych** upewnij się, że zaznaczone jest pole **Zapisz ustawienia połączenia jednostki w App.Config jako** opcja, a następnie kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**, a następnie wybierz tabelę **SalesOrderHeader** .

8. Kliknij przycisk **Zakończ**.

## <a name="create-the-service"></a>Tworzenie usługi

Utwórz usługę danych programu WCF, aby uwidocznić dane w Entity Data Model w aplikacji WPF:

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. Na liście **zainstalowane szablony** kliknij pozycję **Sieć Web**, a następnie wybierz element projekt **usługi danych programu WCF** .

3. W polu **Nazwa** wpisz `AdventureWorksService.svc` , a następnie kliknij przycisk **Dodaj**.

     Program Visual Studio dodaje `AdventureWorksService.svc` do projektu.

## <a name="configure-the-service"></a>Konfigurowanie usługi

Należy skonfigurować usługę do działania w utworzonym Entity Data Model:

1. W `AdventureWorks.svc` pliku kodu Zastąp deklarację klasy **AdventureWorksService** następującym kodem.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Ten kod aktualizuje klasę **AdventureWorksService** , tak aby dziedziczyć z <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` klasy kontekstu obiektów w Entity Data Model. Aktualizuje także metodę, `InitializeService` Aby umożliwić klientom usługi pełny dostęp do odczytu/zapisu do `SalesOrderHeader` jednostki.

2. Skompiluj projekt i sprawdź, czy nie ma błędów.

## <a name="create-the-wpf-client-application"></a>Tworzenie aplikacji klienckiej WPF

Aby wyświetlić dane z usługi danych programu WCF, Utwórz nową aplikację WPF ze źródłem danych opartym na usłudze. W dalszej części tego instruktażu dodasz kontrolki powiązane z danymi do aplikacji.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie, kliknij polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **Windows**.

3. Wybierz szablon projektu **aplikacji WPF** .

4. W polu **Nazwa** wpisz `AdventureWorksSalesEditor` , a następnie kliknij przycisk **OK**.

   Program Visual Studio dodaje `AdventureWorksSalesEditor` projekt do rozwiązania.

5. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

6. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

   Zostanie otwarty Kreator **konfiguracji źródła danych** .

7. Na stronie **Wybierz typ źródła danych** kreatora wybierz pozycję **Usługa**, a następnie kliknij przycisk **dalej**.

8. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odkryj**.

   Program Visual Studio przeszukuje bieżące rozwiązanie pod kątem dostępnych usług i dodaje `AdventureWorksService.svc` do listy dostępnych usług w polu **usługi** .

9. W polu **przestrzeń nazw** wpisz **AdventureWorksService**.

10. W polu **usługi** kliknij pozycję **AdventureWorksService. svc**, a następnie kliknij przycisk **OK**.

    Program Visual Studio pobierze informacje o usłudze, a następnie powróci do kreatora **konfiguracji źródła danych** .

11. Na stronie **Dodaj odwołanie do usługi** kliknij przycisk **Zakończ**.

    Program Visual Studio dodaje węzły reprezentujące dane zwrócone przez usługę do okna **źródła danych** .

## <a name="define-the-user-interface"></a>Zdefiniuj interfejs użytkownika

Dodaj kilka przycisków do okna, modyfikując kod XAML w projektancie WPF. W dalszej części tego instruktażu zostanie dodany kod umożliwiający użytkownikom wyświetlanie i aktualizowanie rekordów sprzedaży przy użyciu tych przycisków.

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **MainWindow. XAML**.

   Okno zostanie otwarte w projektancie WPF.

2. W [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] widoku projektanta Dodaj następujący kod między `<Grid>` tagami:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Skompiluj projekt.

## <a name="create-the-data-bound-controls"></a>Tworzenie formantów powiązanych z danymi

Utwórz kontrolki, które wyświetlają rekordy klientów, przeciągając `SalesOrderHeaders` węzeł z okna **źródła danych** do projektanta.

1. W oknie **źródła danych** kliknij menu rozwijane dla węzła **SalesOrderHeaders** , a następnie wybierz pozycję **szczegóły**.

2. Rozwiń węzeł **SalesOrderHeaders** .

3. W tym przykładzie niektóre pola nie będą wyświetlane, więc kliknij menu rozwijane obok następujących węzłów i wybierz opcję **Brak**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **danej**

    Ta akcja uniemożliwia programowi Visual Studio Tworzenie formantów powiązanych z danymi dla tych węzłów w następnym kroku. W tym przewodniku założono, że użytkownik końcowy nie musi widzieć tych danych.

4. W oknie **źródła danych** przeciągnij węzeł **SalesOrderHeaders** do wiersza siatki w wierszu, który zawiera przyciski.

     Program Visual Studio generuje XAML i kod, który tworzy zestaw kontrolek, które są powiązane z danymi w tabeli **Product** . Aby uzyskać więcej informacji na temat wygenerowanej XAML i kodu, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. W projektancie kliknij pole tekstowe obok etykiety **Identyfikator klienta** .

6. W oknie **Właściwości** zaznacz pole wyboru obok właściwości **IsReadOnly** .

7. Ustaw właściwość **IsReadOnly** dla każdego z następujących pól tekstowych:

    - **Numer zamówienia zakupu**

    - **Identyfikator zamówienia sprzedaży**

    - **Numer zamówienia sprzedaży**

## <a name="load-the-data-from-the-service"></a>Ładowanie danych z usługi

Użyj obiektu serwera proxy usługi, aby załadować dane sprzedaży z usługi. Następnie przypisz zwrócone dane do źródła danych <xref:System.Windows.Data.CollectionViewSource> w oknie WPF.

1. W projektancie, aby utworzyć `Window_Loaded` program obsługi zdarzeń, kliknij dwukrotnie tekst, który odczytuje: **MainWindow**.

2. Zastąp procedurę obsługi zdarzeń poniższym kodem. Upewnij się, że adres *localhost* jest zastępowany w tym kodzie adresem hosta lokalnego na komputerze deweloperskim.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Nawigowanie po rekordach sprzedaży

Dodaj kod, który umożliwia użytkownikom przewijanie rekordów sprzedaży przy użyciu **\<** and **>** przycisków.

1. W projektancie kliknij dwukrotnie **<** przycisk na powierzchni okna.

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `backButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Dodaj następujący kod do wygenerowanego `backButton_Click` programu obsługi zdarzeń:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Wróć do projektanta i kliknij dwukrotnie **>** przycisk.

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `nextButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

4. Dodaj następujący kod do wygenerowanego `nextButton_Click` programu obsługi zdarzeń:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Zapisz zmiany w rekordach sprzedaży

Dodaj kod, który umożliwia użytkownikom wyświetlanie i zapisywanie zmian w rekordach sprzedaży przy użyciu przycisku **Zapisz zmiany** :

1. W projektancie kliknij dwukrotnie przycisk **Zapisz zmiany** .

     Program Visual Studio otwiera plik związany z kodem i tworzy nowy `saveButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia.

2. Dodaj następujący kod do `saveButton_Click` programu obsługi zdarzeń.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Testowanie aplikacji

Skompiluj i uruchom aplikację, aby sprawdzić, czy można wyświetlać i aktualizować rekordy klientów:

1. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**. Sprawdź, czy rozwiązanie nie ma błędów.

2. Naciśnij klawisz **Ctrl** + **F5**.

     Program Visual Studio uruchamia projekt **AdventureWorksService** bez jego debugowania.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **AdventureWorksSalesEditor** .

4. W menu rozwijanym prawym przyciskiem myszy (menu kontekstowe) w obszarze **debugowanie**kliknij polecenie **Uruchom nowe wystąpienie**.

     Aplikacja zostanie uruchomiona. Sprawdź następujące informacje:

    - Pola tekstowe wyświetlają różne pola danych z pierwszego rekordu sprzedaży, który ma numer zamówienia sprzedaży **71774**.

    - Możesz kliknąć przycisk **>** lub, **<** Aby nawigować po innych rekordach sprzedaży.

5. W jednym z rekordów sprzedaży wpisz tekst w polu **komentarz** , a następnie kliknij przycisk **Zapisz zmiany**.

6. Zamknij aplikację, a następnie ponownie uruchom aplikację z poziomu programu Visual Studio.

7. Przejdź do rekordu sprzedaży, który został zmieniony, i sprawdź, czy zmiana jest zachowywana po zamknięciu i ponownym otwarciu aplikacji.

8. Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tego instruktażu można wykonać następujące powiązane zadania:

- Dowiedz się, jak za pomocą okna **źródła danych** w programie Visual Studio POWIĄZAĆ formanty WPF z innymi typami źródeł danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Dowiedz się, jak używać okna **źródła danych** w programie Visual Studio, aby wyświetlić powiązane dane (czyli dane w relacji nadrzędny-podrzędny) w kontrolkach WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Omówienie WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Przegląd Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Przegląd powiązań danych (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
