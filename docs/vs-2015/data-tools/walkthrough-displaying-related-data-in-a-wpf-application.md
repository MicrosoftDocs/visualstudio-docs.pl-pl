---
title: 'Przewodnik: Wyświetlanie powiązanych danych w aplikacji WPF | Dokumentacja firmy Microsoft'
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
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: c7cd8a48092c39048d52a7ebe9cd27163ba32110
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424790"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Przewodnik: Wyświetlanie powiązanych danych w aplikacji WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz aplikację programu WPF, która wyświetla dane z tabel bazy danych, które mają relacji nadrzędny/podrzędny. Dane są hermetyzowane w jednostkach w modelu Entity Data Model. Jednostka nadrzędna zawiera informacje ogólne dotyczące zestawu zamówień. Każda właściwość ta jednostka jest powiązany z innej kontrolki w aplikacji. Jednostki podrzędne zawiera szczegóły dotyczące każdego zamówienia. Ten zestaw danych jest powiązany z <xref:System.Windows.Controls.DataGrid> kontroli.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie aplikacji WPF i modelu danych jednostki, który jest generowany na podstawie danych w przykładowej bazie danych AdventureWorksLT.  
  
- Tworzenie zestawu formantów powiązanych z danymi, które wyświetlają informacje ogólne dotyczące zestawu zamówień. Tworzenie kontrolki, przeciągając jednostka nadrzędna, z **źródeł danych** okna **projektanta WPF**.  
  
- Tworzenie <xref:System.Windows.Controls.DataGrid> zaznaczony formant, który wyświetla szczegóły powiązanych dla każdego zamówienia. Tworzenie kontrolki, przeciągając jednostce podrzędnej z **źródeł danych** okna do okna **projektanta WPF**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Dostęp do uruchomionego wystąpienia programu SQL Server lub SQL Server Express, który ma przykładowej bazy danych AdventureWorksLT podłączone do niego. Możesz pobrać bazy danych AdventureWorksLT z [witryny sieci CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończeni instruktażu:  
  
- Jednostki danych modeli i ADO.NET Entity Framework. Aby uzyskać więcej informacji, zobacz [Omówienie programu Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Praca z projektanta WPF. Aby uzyskać więcej informacji, zobacz [WPF i Silverlight projektanta Przegląd](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Utwórz nowy projekt WPF, aby wyświetlić rekordy zlecenia.  
  
#### <a name="to-create-a-new-wpf-project"></a>Aby utworzyć nowy projekt WPF  
  
1. Uruchom program Visual Studio.  
  
2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3. Rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **Windows**.  
  
4. Upewnij się, że **.NET Framework 4** jest zaznaczona w polu kombi na górze okna dialogowego. <xref:System.Windows.Controls.DataGrid> Formantu, którego używasz w tym przewodniku jest dostępny tylko w programie .NET Framework 4.  
  
5. Wybierz **aplikacji WPF** szablonu projektu.  
  
6. W **nazwa** wpisz `AdventureWorksOrdersViewer`.  
  
7. Kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy `AdventureWorksOrdersViewer` projektu.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Tworzenie modelu danych jednostki dla aplikacji  
 Można było utworzyć formanty powiązane z danymi, należy zdefiniować modelu danych dla aplikacji i dodać go do **źródeł danych** okna. W tym przewodniku model danych jest model Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Aby utworzyć model Entity Data Model  
  
1. Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych** otworzyć **Kreatora konfiguracji źródła danych**.  
  
2. Na **wybierz typ źródła danych** kliknij **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
3. Na **wybierz Model bazy danych** kliknij **modelu Entity Data Model**, a następnie kliknij przycisk **dalej**.  
  
4. Na **wybierz zawartość modelu** kliknij **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5. Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:  
  
   - Jeśli połączenie danych z przykładowej bazy danych AdventureWorksLT jest dostępny na liście rozwijanej, wybierz ją.  
  
      —lub—  
  
   - Kliknij przycisk **nowe połączenie** i Utwórz połączenie z bazą danych AdventureWorksLT.  
  
     Upewnij się, że **zapisywanie ustawień połączenia w pliku App.Config jako jednostki** opcja jest zaznaczona, a następnie kliknij **dalej**.  
  
6. Na **wybierz obiekty bazy danych** rozwiń **tabel**, a następnie wybierz następujące tabele:  
  
   - **SalesOrderDetail**  
  
   - **SalesOrderHeader**  
  
7. Kliknij przycisk **Zakończ**.  
  
8. Skompiluj projekt.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Tworzenie powiązanych z danymi kontrolki, które wyświetlają zamówienia  
 Tworzenie formantów, które wyświetlają rekordów zamówień, przeciągając `SalesOrderHeaders` jednostka z **źródeł danych** okna Projektanta WPF.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Aby utworzyć formanty powiązane z danymi, które wyświetla rekordy zlecenia  
  
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie opcję MainWindow.xaml.  
  
    Okno zostanie otwarty w Projektancie WPF.  
  
2. Edytuj XAML więc **wysokość** i **szerokość** właściwości są ustawione na 800  
  
3. W **źródeł danych** okna, kliknij przycisk menu rozwijanej dla **SalesOrderHeaders** a następnie wybierz węzeł **szczegóły**.  
  
4. Rozwiń **SalesOrderHeaders** węzła.  
  
5. Kliknij menu rozwijane **SalesOrderID** i wybierz **ComboBox**.  
  
6. Dla każdego następujące węzły podrzędne **SalesOrderHeaders** węzła, kliknij menu rozwijane, następnie węzeł i wybierz **Brak**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **Suma częściowa**  
  
   - **TaxAmt**  
  
   - **Transport**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Ta akcja uniemożliwia tworzenie formantów powiązanych z danymi dla tych węzłów w następnym kroku programu Visual Studio. W tym przewodniku zakłada się, że użytkownik końcowy nie musi widzieć tych danych.  
  
7. Z **źródeł danych** okna, przeciągnij **SalesOrderHeaders** węzła do okna **projektanta WPF**.  
  
    Program Visual Studio generuje XAML, która tworzy zestaw elementów sterujących, które są powiązane z danymi w **SalesOrderHeaders** jednostki i kod, który służy do ładowania danych. Aby uzyskać więcej informacji na temat wygenerowany XAML i kodu, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. W projektancie, kliknij pole kombi **identyfikator zamówienia sprzedaży** etykiety.  
  
9. W **właściwości** okna, zaznacz pole wyboru obok pozycji **IsReadOnly** właściwości.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Tworzenie elementu DataGrid, który wyświetla szczegóły zamówienia  
 Tworzenie <xref:System.Windows.Controls.DataGrid> formant, który wyświetla szczegóły zamówienia, przeciągając `SalesOrderDetails` jednostka z **źródeł danych** okna Projektanta WPF.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Aby utworzyć DataGrid, który wyświetla szczegóły zamówienia  
  
1. W **źródeł danych** oknie Znajdź **SalesOrderDetails** węzeł, który jest elementem podrzędnym **SalesOrderHeaders** węzła.  
  
   > [!NOTE]
   > Istnieje również **SalesOrderDetails** węzła, który jest elementem równorzędnym **SalesOrderHeaders** węzła. Upewnij się, że wybrano węzeł podrzędny **SalesOrderHeaders** węzła.  
  
2. Rozwiń węzeł podrzędny **SalesOrderDetails** węzła.  
  
3. Dla każdego następujące węzły podrzędne **SalesOrderDetails** węzła, kliknij menu rozwijane, następnie węzeł i wybierz **Brak**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Ta akcja uniemożliwia tych danych w tym Visual Studio <xref:System.Windows.Controls.DataGrid> formant zostanie utworzony w następnym kroku. W tym przewodniku zakłada się, że użytkownik końcowy nie musi widzieć tych danych.  
  
4. Z **źródeł danych** okna, przeciągnij element podrzędny **SalesOrderDetails** węzła do okna **projektanta WPF**.  
  
    Program Visual Studio generuje XAML, aby zdefiniować nowe powiązane z danymi <xref:System.Windows.Controls.DataGrid> sterowania i kontroli pojawia się w projektancie. Aktualizacje programu Visual Studio również wygenerowany `GetSalesOrderHeadersQuery` metody w pliku związanym z kodem, aby dołączyć dane w **SalesOrderDetails** jednostki.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Skompiluj i uruchom aplikację, aby sprawdzić, czy powoduje wyświetlenie rekordów zlecenia.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Naciśnij klawisz **F5**.  
  
     Aplikacja zostanie skompilowana i działa. Sprawdź następujące informacje:  
  
    - **Identyfikator zamówienia sprzedaży** wyświetla pola kombi **71774**. Jest to pierwszy identyfikator zamówienia w jednostce.  
  
    - Dla każdego zamówienia, należy wybrać w **identyfikator zamówienia sprzedaży** pola kombi kolejności szczegółowe informacje są wyświetlane w <xref:System.Windows.Controls.DataGrid>.  
  
2. Zamknij aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, Dowiedz się, jak używać **źródeł danych** okna w programie Visual Studio, aby powiązać WPF formanty do innych typów źródeł danych. Aby uzyskać więcej informacji, zobacz [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) i [WPF powiązać formanty do zestawu danych](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)