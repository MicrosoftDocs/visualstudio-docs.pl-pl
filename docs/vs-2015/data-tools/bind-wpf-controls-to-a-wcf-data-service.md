---
title: Powiązywanie kontrolek WPF z usługą danych programu WCF | Dokumentacja firmy Microsoft
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb08a016261ac0836ba6dd2dde5d8b0812aab806
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704917"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Powiązywanie kontrolek WPF z usługą danych programu WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz aplikację WPF, która zawiera formanty powiązane z danymi. Formanty są powiązane z rekordami klientów, które są hermetyzowane w [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Zostanie również dodać przyciski, które klienci mogą używać do wyświetlania i aktualizowania rekordów.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie modelu Entity Data Model, który jest generowany na podstawie danych w przykładowej bazie danych AdventureWorksLT.  
  
- Tworzenie [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] który uwidacznia dane w modelu Entity Data Model do aplikacji WPF.  
  
- Tworzenie zestawu formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna Projektanta WPF.  
  
- Tworzenie przycisków, które przejdź do przodu i wstecz za pośrednictwem rekordów klientów.  
  
- Tworzenie przycisku, który zapisuje zmiany danych w kontrolkach do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] i źródle danych.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który ma przykładowej bazy danych AdventureWorksLT podłączone do niego. Możesz pobrać bazy danych AdventureWorksLT z [witryny sieci CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończeni instruktażu:  
  
- Usługi danych WCF. Aby uzyskać więcej informacji, zobacz [Przegląd](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
- Modele danych w [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].  
  
- Jednostki danych modeli i ADO.NET Entity Framework. Aby uzyskać więcej informacji, zobacz [Omówienie programu Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Praca z projektanta WPF. Aby uzyskać więcej informacji, zobacz [WPF i Silverlight projektanta Przegląd](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-service-project"></a>Tworzenie projektu usługi  
 Skorzystaniem z tego przewodnika, tworząc projekt [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
#### <a name="to-create-the-service-project"></a>Aby utworzyć projekt usługi  
  
1. Uruchom program Visual Studio.  
  
2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3. Rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **Web**.  
  
4. Wybierz **aplikacji sieci Web ASP.NET** szablonu projektu.  
  
5. W **nazwa** wpisz `AdventureWorksService` i kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy `AdventureWorksService` projektu.  
  
6. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Default.aspx** i wybierz **Usuń**. Ten plik nie jest konieczne w tym przewodniku.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Tworzenie modelu danych jednostki usługi  
 Aby udostępnić dane do aplikacji przy użyciu [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], należy zdefiniować model danych do usługi. [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] Obsługuje dwa typy modeli danych: Jednostki danych modeli i modeli danych niestandardowych, które są definiowane za pomocą wspólnego języka wspólnego (CLR) obiekty, które implementują <xref:System.Linq.IQueryable%601> interfejsu. W tym instruktażu utworzysz Model danych jednostki do modelu danych.  
  
#### <a name="to-create-an-entity-data-model"></a>Aby utworzyć model Entity Data Model  
  
1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2. Na liście Zainstalowane szablony, kliknij **danych**, a następnie wybierz pozycję **ADO.NET Entity Data Model** elementu projektu.  
  
3. Zmień nazwę na `AdventureWorksModel.edmx`i kliknij przycisk **Dodaj**.  
  
     **Modelu Entity Data Model** zostanie otwarty Kreator.  
  
4. Na **wybierz zawartość modelu** kliknij **Generuj z bazy danych**i kliknij przycisk **dalej**.  
  
5. Na **wybierz połączenie danych** zaznacz jedną z następujących opcji:  
  
    - Jeśli połączenie danych z przykładowej bazy danych AdventureWorksLT jest dostępny na liście rozwijanej, wybierz ją.  
  
    - Kliknij przycisk **nowe połączenie**i Utwórz połączenie z bazą danych AdventureWorksLT.  
  
6. Na **wybierz połączenie danych** strony, upewnij się, że **zapisywanie ustawień połączenia w pliku App.Config jako jednostki** opcja jest zaznaczona, a następnie kliknij **dalej**.  
  
7. Na **wybierz obiekty bazy danych** rozwiń **tabel**, a następnie wybierz pozycję **SalesOrderHeader** tabeli.  
  
8. Kliknij przycisk **Zakończ**.  
  
## <a name="create-the-service"></a>Tworzenie usługi  
 Utwórz [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] do udostępniania danych w modelu Entity Data Model do aplikacji WPF.  
  
#### <a name="to-create-the-service"></a>Aby utworzyć usługę  
  
1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
2. Na liście Zainstalowane szablony, kliknij **Web**, a następnie wybierz pozycję **usługi danych WCF** elementu projektu.  
  
3. W **nazwa** wpisz `AdventureWorksService.svc`i kliknij przycisk **Dodaj**.  
  
     Program Visual Studio dodaje `AdventureWorksService.svc` do projektu.  
  
## <a name="configure-the-service"></a>Konfigurowanie usługi  
 Należy skonfigurować usługę, aby działały w modelu Entity Data Model, który został utworzony.  
  
#### <a name="to-configure-the-service"></a>Aby skonfigurować usługę  
  
1. W `AdventureWorks.svc` plik kodu, Zastąp `AdventureWorksService` klasy deklaracji z następującym kodem.  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     Ten kod aktualizuje `AdventureWorksService` klasy, tak aby pochodzi od klasy <xref:System.Data.Services.DataService%601> który operuje na `AdventureWorksLTEntities` obiektu context — klasa w modelu Entity Data Model. Aktualizuje również `InitializeService` metodę, aby umożliwić klientom usługi Dostęp pełny odczyt/zapis do `SalesOrderHeader` jednostki.  
  
2. Skompiluj projekt i sprawdź, czy opiera się bez błędów.  
  
## <a name="create-the-wpf-client-application"></a>Tworzenie aplikacji klienckiej WPF  
 Aby wyświetlić dane z [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], Utwórz nową aplikację WPF ze źródłem danych, która opiera się na usługę. W dalszej części tego przewodnika dodasz formantów powiązanych z danymi w aplikacji.  
  
#### <a name="to-create-the-wpf-client-application"></a>Do utworzenia aplikacji klienckiej WPF  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, kliknij przycisk **Dodaj**i wybierz **nowy projekt**.  
  
2. W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **Windows**.  
  
3. Wybierz **aplikacji WPF** szablonu projektu.  
  
4. W **nazwa** wpisz `AdventureWorksSalesEditor`i kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje `AdventureWorksSalesEditor` projektu do rozwiązania.  
  
5. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
     **Źródeł danych** zostanie otwarte okno.  
  
6. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Konfiguracji źródła danych** zostanie otwarty Kreator.  
  
7. W **wybierz typ źródła danych** strony kreatora, wybierz **usługi**, a następnie kliknij przycisk **dalej**.  
  
8. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdź**.  
  
     Wyszukuje w bieżącym rozwiązaniu dla dostępnych usług Visual Studio i dodaje `AdventureWorksService.svc` do listy dostępnych usług w **usług** pole.  
  
9. W **Namespace** wpisz `AdventureWorksService`.  
  
10. W **usług** kliknij **AdventureWorksService.svc**, a następnie kliknij przycisk **OK**.  
  
     Pobiera informacje o usłudze Visual Studio i powraca do **konfiguracji źródła danych** kreatora.  
  
11. W **Dodaj odwołanie do usługi** kliknij **Zakończ**.  
  
     Program Visual Studio dodaje węzły, które reprezentują dane zwrócone przez usługę **źródeł danych** okna.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definiowanie interfejsu użytkownika w oknie  
 Dodaj kilku przycisków do okna, modyfikując XAML w Projektancie WPF. W dalszej części tego przewodnika dodasz kod, który umożliwia użytkownikom wyświetlanie i aktualizowanie rekordów sprzedaży przy użyciu tych przycisków.  
  
#### <a name="to-create-the-window-layout"></a>Aby utworzyć układ okna  
  
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie opcję MainWindow.xaml.  
  
     Okno zostanie otwarty w Projektancie WPF.  
  
2. W [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] wyświetlić projektanta, Dodaj następujący kod między `<Grid>` tagi:  
  
    ```  
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
 Tworzenie formantów, które wyświetlają rekordy klientów, przeciągając `SalesOrderHeaders` węzła z **źródeł danych** okna projektanta.  
  
#### <a name="to-create-the-data-bound-controls"></a>Aby utworzyć formanty powiązane z danymi  
  
1. W **źródeł danych** okna, kliknij przycisk menu rozwijanej dla **SalesOrderHeaders** , a następnie wybierz węzeł **szczegóły**.  
  
2. Rozwiń **SalesOrderHeaders** węzła.  
  
3. Na przykład niektóre pola nie zostaną wyświetlone, więc kliknij menu rozwijane obok następujących węzłów i wybierz pozycję **Brak**:  
  
   - **CreditCardApprovalCode**  
  
   - **ModifiedDate**  
  
   - **OnlineOrderFlag**  
  
   - **RevisionNumber**  
  
   - **ROWGUID**  
  
     Ta akcja uniemożliwia tworzenie formantów powiązanych z danymi dla tych węzłów w następnym kroku programu Visual Studio. W tym przewodniku założono, że użytkownik końcowy nie musi widzieć tych danych.  
  
4. Z **źródeł danych** okna, przeciągnij **SalesOrderHeaders** węzeł, aby wiersz siatki w ramach wiersza, który zawiera przyciski.  
  
    Program Visual Studio generuje XAML i kodu, który tworzy zestaw elementów sterujących, które są powiązane z danymi w **produktu** tabeli. Aby uzyskać więcej informacji na temat wygenerowany XAML i kodu, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5. W projektancie, kliknij pole tekstowe **identyfikator klienta** etykiety.  
  
6. W **właściwości** okna, zaznacz pole wyboru obok pozycji **IsReadOnly** właściwości.  
  
7. Ustaw **IsReadOnly** właściwości dla każdego z następujących pól tekstowych:  
  
   - **Numer zamówienia zakupu**  
  
   - **Identyfikator zamówienia sprzedaży**  
  
   - **Numer zamówienia sprzedaży**  
  
## <a name="load-the-data-from-the-service"></a>Załaduj dane z usługi  
 Aby załadować dane sprzedaży z usługi, należy użyć obiektu serwera proxy usługi. Następnie przypisz zwróconych danych do źródła danych dla <xref:System.Windows.Data.CollectionViewSource> okna WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>Aby załadować dane z usługi  
  
1. W projektancie, aby utworzyć `Window_Loaded` procedura obsługi zdarzeń, kliknij dwukrotnie tekst, który odczytuje: **Główne**.  
  
2. Zastąp następujący kod obsługi zdarzeń. Upewnij się, że można zastąpić *localhost* adresów w tym kodzie adres hosta lokalnego na komputerze deweloperskim.  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Rekordy Navigatesales  
 Dodaj kod, który umożliwia użytkownikom do przewijania rekordów sprzedaży przy użyciu **\<** i **>** przycisków.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Aby umożliwić użytkownikom przechodzenie rekordy sprzedaży  
  
1. W projektancie, kliknij dwukrotnie **<** przycisku na powierzchni okna.  
  
     Visual Studio otwiera plik CodeBehind i tworzy nowy `backButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2. Dodaj następujący kod do wygenerowany `backButton_Click` program obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3. Wróć do projektanta, a następnie kliknij dwukrotnie **>** przycisku.  
  
     Visual Studio otwiera plik CodeBehind i tworzy nowy `nextButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
4. Dodaj następujący kod do wygenerowany `nextButton_Click` program obsługi zdarzeń:  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>Trwa zapisywanie zmian w rejestrach sprzedaży  
 Dodaj kod, który umożliwia użytkownikom wyświetlanie i zapisać zmiany do rekordów sprzedaży przy użyciu **Zapisz zmiany** przycisku.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Dodanie możliwości, aby zapisać zmiany do rekordów sprzedaży  
  
1. W projektancie, kliknij dwukrotnie **Zapisz zmiany** przycisku.  
  
     Visual Studio otwiera plik CodeBehind i tworzy nowy `saveButton_Click` program obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
2. Dodaj następujący kod do `saveButton_Click` programu obsługi zdarzeń.  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Skompiluj i uruchom aplikację, aby sprawdzić, wyświetlanie i aktualizowanie rekordów klientów.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Upewnij się, że rozwiązanie zostanie skompilowane bez błędów.  
  
2. Naciśnij klawisz **kombinację klawiszy Ctrl + F5**.  
  
     Program Visual Studio uruchamia **AdventureWorksService** projekt bez debugowania go.  
  
3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **AdventureWorksSalesEditor** projektu.  
  
4. W menu kontekstowym w obszarze **debugowania**, kliknij przycisk **Uruchom nowe wystąpienie**.  
  
     Aplikacja zostanie uruchomiona. Sprawdź następujące informacje:  
  
    - Pola tekstowe wyświetlanie różnych pól danych z pierwszego rekordu sprzedaży, która ma identyfikator zamówienia sprzedaży **71774**.  
  
    - Możesz kliknąć pozycję **>** lub **<** przycisków, aby przejść do innych rekordów sprzedaży.  
  
5. Z jednego z rekordów sprzedaży, wpisz tekst w **komentarz** , a następnie kliknij przycisk **Zapisz zmiany**.  
  
6. Zamknij aplikację, a następnie ponownie uruchom aplikację w programie Visual Studio.  
  
7. Przejdź do sprzedaży rekordu, który został zmodyfikowany i sprawdź, czy zmiana będzie nadal występować po zamknięciu i ponownym otwarciu aplikacji.  
  
8. Zamknij aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, należy wykonać następujące zadania:  
  
- Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby powiązać WPF formanty do innych typów źródeł danych. Aby uzyskać więcej informacji, zobacz [WPF powiązać formanty do zestawu danych](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
- Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby wyświetlić powiązane dane (czyli w relacji nadrzędny podrzędny) w formantach WPF. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Omówienie](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Omówienie programu Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [Omówienie projektanta Silverlight i WPF](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Powiązanie danych — omówienie](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
