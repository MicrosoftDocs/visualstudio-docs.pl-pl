---
title: Utwórz relację wzorca głównego przy użyciu buforowanego zestawu danych
description: Dowiedz się więcej o tworzeniu relacji wzorzec/szczegóły w arkuszu i buforowaniu danych, aby umożliwić korzystanie z rozwiązania w trybie offline.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de7bf3ba34a2a7dd3e7db9ff549e4a839800d524
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524871"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Wskazówki: Tworzenie relacji głównej szczegółów przy użyciu buforowanego zestawu danych
  W tym instruktażu pokazano, jak utworzyć relację wzorzec/szczegóły w arkuszu i buforować dane, aby umożliwić korzystanie z rozwiązania w trybie offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W tym instruktażu dowiesz się, jak:

- Dodawanie formantów do arkusza.

- Skonfiguruj zestaw danych do buforowania w arkuszu.

- Dodaj kod, aby włączyć przewijanie rekordów.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do przykładowej bazy danych Northwind SQL Server. Baza danych może być na komputerze deweloperskim lub na serwerze.

- Uprawnienia do odczytu i zapisu w bazie danych SQL Server.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **My master-detail**, używając obu Visual Basic lub C#. Upewnij się, że wybrano **Utwórz nowy dokument** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Program Visual Studio otwiera nowy skoroszyt programu Excel w Projektancie i dodaje projekt **My master-detail** do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **dalej**.

6. Usuń zaznaczenie opcji Zapisz połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **tabele** w oknie **obiekty bazy danych** .

8. Wybierz tabelę **Orders** i tabelę **Order Details** .

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje dwie tabele do okna **źródła danych** . Dodaje również typ DataSet do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 W tym kroku dodasz nazwany zakres, obiekt listy i dwa przyciski do pierwszego arkusza. Najpierw Dodaj nazwany zakres i obiekt list z okna **źródła danych** , aby były one automatycznie powiązane ze źródłem danych. Następnie Dodaj przyciski z **przybornika**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Aby dodać nazwany zakres i obiekt listy

1. Upewnij się, że skoroszyt **My Master-Detail.xlsx** jest otwarty w projektancie programu Visual Studio z wyświetlonym arkuszem **Arkusz1** .

2. Otwórz okno **źródła danych** i rozwiń węzeł **zamówienia** .

3. Wybierz kolumnę **IDZamówienia** , a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Kliknij pozycję **NamedRange** na liście rozwijanej, a następnie przeciągnij kolumnę **IDZamówienia** do komórki **a2**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `OrderIDNamedRange` W komórce **a2** zostanie utworzona kontrolka o nazwie. W tym samym czasie <xref:System.Windows.Forms.BindingSource> nazwa `OrdersBindingSource` , karta tabeli i <xref:System.Data.DataSet> wystąpienie są dodawane do projektu. Formant jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z <xref:System.Data.DataSet> wystąpieniem.

5. Przewiń w dół do kolumn, które znajdują się w tabeli **Orders (zamówienia** ). W dolnej części listy znajduje się tabela **Order Details** . jest to możliwe, ponieważ jest elementem podrzędnym tabeli **Orders** . Wybierz tabelę **szczegóły zamówienia** , a nie taką, która znajduje się na tym samym poziomie co tabela **Orders** , a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Na liście rozwijanej kliknij pozycję **Lista** , a następnie przeciągnij tabelę **OrderDetails** do komórki **a6**.

7. <xref:Microsoft.Office.Tools.Excel.ListObject>Kontrolka o nazwie **Order_DetailsListObject** jest tworzona w komórce **a6** i powiązana z <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Aby dodać dwa przyciski

1. Na karcie **Formanty standardowe** **przybornika** Dodaj <xref:System.Windows.Forms.Button> kontrolkę do komórki **a3** arkusza.

    Ten przycisk ma nazwę `Button1` .

2. Dodaj kolejną <xref:System.Windows.Forms.Button> kontrolkę do komórki **B3** arkusza.

    Ten przycisk ma nazwę `Button2` .

   Następnie Oznacz zestaw danych, który ma zostać zbuforowany w dokumencie.

## <a name="cache-the-dataset"></a>Buforowanie zestawu danych
 Oznacz zestaw danych, który ma zostać zbuforowany w dokumencie, przez udostępnienie elementu DataSet i ustawienie właściwości **CacheInDocument** .

### <a name="to-cache-the-dataset"></a>Aby buforować zestaw danych

1. Wybierz pozycję **NorthwindDataSet** w zasobniku składników.

2. W oknie **Właściwości** Zmień właściwość **Modyfikatory** na **Public**.

    Zestawy danych muszą być publiczne przed włączeniem buforowania.

3. Zmień wartość właściwości **CacheInDocument** na **true**.

   Następnym krokiem jest dodanie tekstu do przycisków i w języku C# Dodaj kod, aby podłączyć procedury obsługi zdarzeń.

## <a name="initialize-the-controls"></a>Inicjowanie formantów
 Ustaw tekst przycisku i Dodaj obsługę zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzenia.

### <a name="to-initialize-the-data-and-the-controls"></a>Aby zainicjować dane i kontrolki

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Arkusz1. vb** lub **Sheet1.cs**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do metody, `Sheet1_Startup` Aby ustawić tekst przycisków.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. W przypadku tylko języka C# Dodaj obsługę zdarzeń dla przycisku kliknij zdarzenia do `Sheet1_Startup` metody.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodaj kod, aby włączyć przewijanie rekordów
 Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń każdego przycisku, aby przejść przez rekordy.

### <a name="to-scroll-through-the-records"></a>Aby przewijać rekordy

1. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button1` i Dodaj następujący kod, aby przejść do tyłu przez rekordy:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button2` i Dodaj następujący kod, aby przejść do rekordu:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że dane są wyświetlane w oczekiwany sposób, i że można użyć rozwiązania w trybie offline.

### <a name="to-test-the-data-caching"></a>Aby przetestować buforowanie danych

1. Naciśnij klawisz **F5**.

2. Sprawdź, czy nazwany zakres i obiekt list są wypełnione danymi ze źródła danych.

3. Przewiń kilka rekordów, klikając przyciski.

4. Zapisz skoroszyt, a następnie zamknij skoroszyt i program Visual Studio.

5. Wyłącz połączenie z bazą danych. Odłącz kabel sieciowy od komputera, jeśli baza danych znajduje się na serwerze, lub Zatrzymaj usługę SQL Server, jeśli baza danych znajduje się na komputerze deweloperskim.

6. Otwórz program Excel, a następnie otwórz **moją Master-Detail.xlsx** z katalogu *\Bin* (*\Moje Master-Detail\bin* w Visual Basic lub *\Moje Master-Detail\bin\debug* w języku C#).

7. Przewiń kilka rekordów, aby zobaczyć, że arkusz działa normalnie po rozłączeniu.

8. Ponownie nawiąż połączenie z bazą danych. Ponownie podłącz komputer do sieci, jeśli baza danych znajduje się na serwerze, lub Uruchom usługę SQL Server, jeśli baza danych znajduje się na komputerze deweloperskim.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące tworzenia relacji danych master/detail w arkuszu i buforowania zestawu danych. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Wdróż rozwiązanie. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
