---
title: Tworzenie relacji szczegółów wzorca przy użyciu buforowanych zestawów danych
description: Dowiedz się więcej na temat tworzenia relacji wzorzec/szczegół w arkuszu i buforowania danych, aby można było używać rozwiązania w trybie offline.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 177b21e2278153693601adf7b7dc18b751cf184e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824851"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Przewodnik: tworzenie relacji szczegółów wzorca przy użyciu buforowanych zestawów danych
  W tym przewodniku pokazano tworzenie relacji wzorzec/szczegół w arkuszu oraz buforowanie danych, dzięki czemu rozwiązanie może być używane w trybie offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W ramach tego przewodnika dowiesz się, jak:

- Dodawanie kontrolek do arkusza.

- Skonfiguruj zestaw danych do buforowania w arkuszu.

- Dodaj kod umożliwiający przewijanie rekordów.

- Przetestuj projekt.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do przykładowej bazy danych Northwind SQL Server Northwind. Baza danych może być na komputerze dewelopera lub na serwerze.

- Uprawnienia do odczytu i zapisu w SQL Server danych.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt skoroszytu programu Excel o nazwie **My Master-Detail** przy użyciu Visual Basic lub C#. Upewnij się, **że wybrano opcję Utwórz** nowy dokument. Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio nowy skoroszyt programu Excel w projektancie i dodaje projekt **My Master-Detail** do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Użyj okna **Źródła danych,** aby dodać typowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

2. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Wybierz **pozycję Baza danych,** a następnie kliknij przycisk **Dalej.**

4. Wybierz połączenie danych z przykładową bazą danych Northwind SQL Server lub dodaj nowe połączenie przy użyciu **przycisku Nowe** połączenie.

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **Dalej.**

6. Wyczyść opcję zapisywania połączenia, jeśli jest zaznaczone, a następnie kliknij przycisk **Dalej.**

7. Rozwiń **węzeł Tabele** w **oknie Obiekty bazy** danych.

8. Wybierz **tabelę Orders** (Zamówienia) i **tabelę Order Details (Szczegóły** zamówienia).

9. Kliknij przycisk **Finish** (Zakończ).

   Kreator dodaje dwie tabele do **okna Źródła** danych. Dodaje również typowany zestaw danych do projektu, który jest widoczny w **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 W tym kroku dodasz nazwany zakres, obiekt listy i dwa przyciski do pierwszego arkusza. Najpierw dodaj nazwany zakres i obiekt  listy z okna Źródła danych, aby były one automatycznie powiązane ze źródłem danych. Następnie dodaj przyciski z **przybornika**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Aby dodać nazwany zakres i obiekt listy

1. Sprawdź, czy **skoroszyt Moja Master-Detail.xlsx** jest otwarty w projektancie Visual Studio, z **wyświetlonym arkuszem Sheet1.**

2. Otwórz okno **Źródła danych** i rozwiń węzeł **Orders (Zamówienia).**

3. Wybierz **kolumnę OrderID,** a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

4. Kliknij **pozycję NamedRange** na liście rozwijanej, a następnie przeciągnij kolumnę **OrderID** do komórki **A2**.

     Kontrolka <xref:Microsoft.Office.Tools.Excel.NamedRange> o `OrderIDNamedRange` nazwie jest tworzona w komórce **A2**. W tym samym czasie do projektu są dodawane nazwane karty tabeli i <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` <xref:System.Data.DataSet> wystąpienie. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource> wystąpieniem <xref:System.Data.DataSet> .

5. Przewiń w dół po kolumnach, które znajdują się w **tabeli Orders** (Zamówienia). W dolnej części listy znajduje się tabela **Szczegóły** zamówienia. znajduje się tutaj, ponieważ jest ona podrzędną **tabelą Orders( Zamówienia).** Wybierz tę **tabelę Szczegóły** zamówienia, a nie tę, która znajduje się na tym samym poziomie co tabela **Orders( Zamówienia),** a następnie kliknij strzałkę listy rozwijanej, która zostanie wyświetlona.

6. Kliknij **pozycję ListObject** na liście rozwijanej, a następnie przeciągnij tabelę **OrderDetails** do komórki **A6**.

7. Kontrolka <xref:Microsoft.Office.Tools.Excel.ListObject> o **Order_DetailsListObject** jest tworzona w komórce **A6** i powiązana z <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Aby dodać dwa przyciski

1. Na karcie **Typowe kontrolki** **przybornika** dodaj kontrolkę <xref:System.Windows.Forms.Button> do komórki **A3** arkusza.

    Ten przycisk ma nazwę `Button1` .

2. Dodaj kolejną <xref:System.Windows.Forms.Button> kontrolkę do komórki **B3** arkusza.

    Ten przycisk ma nazwę `Button2` .

   Następnie oznacz zestaw danych do buforowania w dokumencie.

## <a name="cache-the-dataset"></a>Buforowanie zestawu danych
 Oznacz zestaw danych do buforowania w dokumencie, ustawiając zestaw danych jako publiczny i ustawiając właściwość **CacheInDocument.**

### <a name="to-cache-the-dataset"></a>Aby buforować zestaw danych

1. Wybierz **pozycję NorthwindDataSet** na pasku zadań.

2. W **oknie** Właściwości zmień właściwość **Modyfikatory na** **Public**.

    Przed włączeniu buforowania zestawy danych muszą być publiczne.

3. Zmień właściwość **CacheInDocument** na **True.**

   Następnym krokiem jest dodanie tekstu do przycisków, a w języku C# dodanie kodu w celu podpinania obsługi zdarzeń.

## <a name="initialize-the-controls"></a>Inicjowanie kontrolek
 Ustaw tekst przycisku i dodaj procedury obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzenia.

### <a name="to-initialize-the-data-and-the-controls"></a>Aby zainicjować dane i kontrolki

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Sheet1.vb** lub **Sheet1.cs,** a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do metody `Sheet1_Startup` , aby ustawić tekst przycisków.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet15":::

3. Tylko w przypadku języka C# dodaj procedury obsługi zdarzeń dla zdarzeń kliknięcia przycisku do `Sheet1_Startup` metody .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet16":::

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodawanie kodu umożliwiającego przewijanie rekordów
 Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń każdego przycisku, aby przechodzić przez rekordy.

### <a name="to-scroll-through-the-records"></a>Aby przewijać rekordy

1. Dodaj program obsługi zdarzeń dla zdarzenia , a następnie dodaj następujący kod, aby przechodzić <xref:System.Windows.Forms.Control.Click> `Button1` wstecz przez rekordy:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet17":::

2. Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia , a następnie dodaj następujący `Button2` kod, aby przejść przez rekordy:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet18":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować skoroszyt, aby upewnić się, że dane są wyświetlane zgodnie z oczekiwaniami i że możesz używać rozwiązania w trybie offline.

### <a name="to-test-the-data-caching"></a>Aby przetestować buforowanie danych

1. Naciśnij klawisz **F5**.

2. Sprawdź, czy nazwany zakres i obiekt listy są wypełnione danymi ze źródła danych.

3. Przewiń niektóre rekordy, klikając przyciski.

4. Zapisz skoroszyt, a następnie zamknij skoroszyt i Visual Studio.

5. Wyłącz połączenie z bazą danych. Odłącz kabel sieciowy od komputera, jeśli baza danych znajduje się na serwerze, lub zatrzymaj usługę SQL Server, jeśli baza danych znajduje się na komputerze dewelopera.

6. Otwórz program Excel, **Master-Detail.xlsx** w katalogu *\bin* (*\My Master-Detail\bin* w programie Visual Basic lub *\My Master-Detail\bin\debug* w języku C#).

7. Przewiń niektóre rekordy, aby zobaczyć, że arkusz działa normalnie po rozłączeniu.

8. Połącz się ponownie z bazą danych. Ponownie połącz komputer z siecią, jeśli baza danych znajduje się na serwerze, lub uruchom usługę SQL Server, jeśli baza danych znajduje się na komputerze dewelopera.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy tworzenia relacji danych wzorzec/szczegół w arkuszu i buforowania zestawu danych. Oto kilka zadań, które mogą pojawić się w następnej części:

- Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
