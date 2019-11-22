---
title: 'Wskazówki: wyświetlanie powiązanych danych w aplikacji WPF | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 787be52eeb546d2ab184a172464862d10cb43288
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299580"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Wskazówki: wyświetlanie powiązanych danych w aplikacji WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz aplikację WPF, która będzie wyświetlać dane z tabel bazy danych, które mają relację nadrzędny/podrzędny. Dane są hermetyzowane w jednostkach w Entity Data Model. Jednostka nadrzędna zawiera przegląd informacji dotyczących zestawu zamówień. Każda właściwość tej jednostki jest powiązana z inną kontrolką w aplikacji. Jednostka podrzędna zawiera szczegóły dotyczące poszczególnych zamówień. Ten zestaw danych jest powiązany z kontrolką <xref:System.Windows.Controls.DataGrid>.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie aplikacji WPF i Entity Data Model wygenerowanej na podstawie danych z przykładowej bazy danych AdventureWorksLT.

- Tworzenie zestawu formantów powiązanych z danymi, które wyświetlają przegląd informacji dla zestawu zamówień. Kontrolki można tworzyć, przeciągając jednostkę nadrzędną z okna **źródła danych** do **projektanta WPF**.

- Tworzenie kontrolki <xref:System.Windows.Controls.DataGrid>, która wyświetla powiązane szczegóły dla każdej zaznaczonej kolejności. Kontrolki można tworzyć, przeciągając jednostkę podrzędną z okna **źródła danych** do okna w **projektancie WPF**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].,

- Dostęp do uruchomionego wystąpienia SQL Server lub SQL Server Express z dołączoną przykładową bazą danych AdventureWorksLT. Bazę danych AdventureWorksLT można pobrać z [witryny sieci Web CodePlex](https://go.microsoft.com/fwlink/?linkid=87843).

  Wcześniejsza znajomość następujących pojęć jest również przydatna, ale nie jest wymagana do ukończenia przewodnika:

- Modele danych jednostek i Entity Framework ADO.NET. Aby uzyskać więcej informacji, zobacz [Entity Framework przegląd](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Praca z projektantem WPF. Aby uzyskać więcej informacji, zobacz [Omówienie narzędzia WPF i Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Powiązanie danych WPF. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Tworzenie projektu
 Utwórz nowy projekt WPF, aby wyświetlić rekordy zamówienia.

#### <a name="to-create-a-new-wpf-project"></a>Aby utworzyć nowy projekt WPF

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. Rozwiń **element C# Visual** lub **Visual Basic**, a następnie wybierz pozycję **Windows**.

4. Upewnij się, że w polu kombi w górnej części okna dialogowego została wybrana wartość **.NET Framework 4** . Formant <xref:System.Windows.Controls.DataGrid> używany w tym instruktażu jest dostępny tylko w .NET Framework 4.

5. Wybierz szablon projektu **aplikacji WPF** .

6. W polu **Nazwa** wpisz `AdventureWorksOrdersViewer`.

7. Kliknij przycisk **OK**.

     Program Visual Studio tworzy projekt `AdventureWorksOrdersViewer`.

## <a name="creating-an-entity-data-model-for-the-application"></a>Tworzenie Entity Data Model dla aplikacji
 Aby można było tworzyć kontrolki powiązane z danymi, należy zdefiniować model danych dla aplikacji i dodać go do okna **źródła danych** . W tym instruktażu modelem danych jest Entity Data Model.

#### <a name="to-create-an-entity-data-model"></a>Aby utworzyć Entity Data Model

1. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych** , aby otworzyć **Kreatora konfiguracji źródła danych**.

2. Na stronie **Wybierz typ źródła danych** kliknij pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

3. Na stronie **Wybierz model bazy danych** kliknij przycisk **Entity Data Model**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz zawartość modelu** kliknij pozycję **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

   - Jeśli połączenie danych z przykładową bazą danych AdventureWorksLT jest dostępne na liście rozwijanej, wybierz ją.

      —lub—

   - Kliknij pozycję **nowe połączenie** i Utwórz połączenie z bazą danych AdventureWorksLT.

     Upewnij się, że wybrano opcję **Zapisz ustawienia połączenia jednostki w pliku App. config jako** opcja, a następnie kliknij przycisk **dalej**.

6. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**, a następnie wybierz następujące tabele:

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. Kliknij przycisk **Zakończ**.

8. Skompiluj projekt.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Tworzenie kontrolek powiązanych z danymi, które wyświetlają zamówienia
 Utwórz kontrolki, które wyświetlają rekordy kolejności, przeciągając jednostkę `SalesOrderHeaders` z okna **źródła danych** do projektanta WPF.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Aby utworzyć kontrolki powiązane z danymi, które wyświetlają rekordy zamówienia

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję MainWindow. XAML.

    Okno zostanie otwarte w projektancie WPF.

2. Edytuj kod XAML, tak aby właściwości **Height** i **Width** zostały ustawione na 800

3. W oknie **źródła danych** kliknij menu rozwijane dla węzła **SalesOrderHeaders** i wybierz pozycję **szczegóły**.

4. Rozwiń węzeł **SalesOrderHeaders** .

5. Kliknij menu rozwijane obok pozycji **SalesOrderID** , a następnie wybierz **pole kombi**.

6. Dla każdego z następujących węzłów podrzędnych węzła **SalesOrderHeaders** kliknij menu rozwijane obok węzła i wybierz opcję **Brak**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **Suma częściowa**

   - **TaxAmt**

   - **Opłaty**

   - **danej**

   - **ModifiedDate**

     Ta akcja uniemożliwia programowi Visual Studio Tworzenie formantów powiązanych z danymi dla tych węzłów w następnym kroku. W tym przewodniku przyjęto założenie, że użytkownik końcowy nie musi widzieć tych danych.

7. W oknie **źródła danych** przeciągnij węzeł **SalesOrderHeaders** do okna w **projektancie WPF**.

    Program Visual Studio generuje kod XAML, który tworzy zestaw kontrolek, które są powiązane z danymi w jednostce **SalesOrderHeaders** i kodu ładującego dane. Aby uzyskać więcej informacji na temat wygenerowanej XAML i kodu, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. W projektancie kliknij pole kombi obok etykiety **Identyfikator zamówienia sprzedaży** .

9. W oknie **Właściwości** zaznacz pole wyboru obok właściwości **IsReadOnly** .

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Tworzenie elementu DataGrid wyświetlającego szczegóły zamówienia
 Utwórz kontrolkę <xref:System.Windows.Controls.DataGrid>, która wyświetla szczegóły kolejności, przeciągając jednostkę `SalesOrderDetails` z okna **źródła danych** do projektanta WPF.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Aby utworzyć element DataGrid, który wyświetla szczegóły zamówienia

1. W oknie **źródła danych** zlokalizuj węzeł **SalesOrderDetails** , który jest elementem podrzędnym węzła **SalesOrderHeaders** .

   > [!NOTE]
   > Istnieje również węzeł **SalesOrderDetails** , który jest elementem równorzędnym węzła **SalesOrderHeaders** . Upewnij się, że wybrano węzeł podrzędny węzła **SalesOrderHeaders** .

2. Rozwiń węzeł podrzędny **SalesOrderDetails** .

3. Dla każdego z następujących węzłów podrzędnych węzła **SalesOrderDetails** kliknij menu rozwijane obok węzła i wybierz opcję **Brak**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **danej**

   - **ModifiedDate**

     Ta akcja uniemożliwia programowi Visual Studio uwzględnienie tych danych w kontrolce <xref:System.Windows.Controls.DataGrid> utworzonej w następnym kroku. W tym przewodniku przyjęto założenie, że użytkownik końcowy nie musi widzieć tych danych.

4. W oknie **źródła danych** przeciągnij podrzędny węzeł **SalesOrderDetails** do okna w **projektancie WPF**.

    Program Visual Studio generuje kod XAML, aby zdefiniować nową kontrolkę <xref:System.Windows.Controls.DataGrid> powiązaną z danymi, a kontrolka pojawi się w projektancie. Program Visual Studio aktualizuje także wygenerowaną metodę `GetSalesOrderHeadersQuery` w pliku związanym z kodem, aby uwzględnić dane w jednostce **SalesOrderDetails** .

## <a name="testing-the-application"></a>Testowanie aplikacji
 Skompiluj i uruchom aplikację, aby sprawdzić, czy są wyświetlane rekordy zamówienia.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij klawisz **F5**.

     Aplikacja zostanie skompilowana i uruchomiona. Sprawdź następujące kwestie:

    - Pole kombi **Identyfikator zamówienia sprzedaży** zawiera **71774**. Jest to pierwszy identyfikator zamówienia w jednostce.

    - Dla każdego zamówienia wybieranego w polu kombi **Identyfikator zamówienia sprzedaży** w <xref:System.Windows.Controls.DataGrid>są wyświetlane szczegółowe informacje o kolejności.

2. Zamknij aplikację.

## <a name="next-steps"></a>Następne kroki
 Po zakończeniu tego instruktażu Dowiedz się, jak za pomocą okna **źródła danych** w programie Visual Studio POWIĄZAĆ formanty WPF z innymi typami źródeł danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) i [Powiązywanie formantów WPF z zestawem](../data-tools/bind-wpf-controls-to-a-dataset.md)danych.

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)