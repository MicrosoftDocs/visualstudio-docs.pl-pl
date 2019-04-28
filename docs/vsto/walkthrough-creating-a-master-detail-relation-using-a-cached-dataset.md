---
title: 'Przewodnik: Tworzenie relacji wzorzec szczegół za pomocą pamięci podręcznej zestawu danych'
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
ms.openlocfilehash: 3380b9c5302ed6e8a1bf6965f5fb1f259e3a6682
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438556"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Przewodnik: Tworzenie relacji wzorzec szczegół za pomocą pamięci podręcznej zestawu danych
  W tym instruktażu przedstawiono tworzenie relacji wzorzec/szczegół w arkuszu, a buforowanie danych, dzięki czemu rozwiązanie może służyć w trybie offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Z tego instruktażu dowiesz się jak:

- Dodawanie formantów do arkusza.

- Konfigurowanie zestawu danych, można buforować w arkuszu.

- Dodaj kod, aby włączyć przewijanie rekordów.

- Testowanie projektu.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do przykładowej bazy danych Northwind programu SQL Server. Baza danych może być na komputerze deweloperskim lub na serwerze.

- Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projektu skoroszytu programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje wzorzec / szczegół**, za pomocą języka Visual Basic lub C#. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje wzorzec / szczegół** projekt **Eksploratora rozwiązań**.

## <a name="create-the-data-source"></a>Utwórz źródło danych
 Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.

2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Wybierz **bazy danych** a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.

5. Po wybraniu lub utworzenie połączenia, kliknij przycisk **dalej**.

6. Usuń zaznaczenie opcji, aby zapisać połączenie, jeśli jest ono zaznaczone, a następnie kliknij **dalej**.

7. Rozwiń **tabel** w węźle **obiektów bazy danych** okna.

8. Wybierz **zamówienia** tabeli i **Orderdetails** tabeli.

9. Kliknij przycisk **Zakończ**.

   Kreator dodaje dwie tabele, aby **źródeł danych** okna. Dodaje także typizowany zestaw danych do projektu, który jest widoczny w **Eksploratora rozwiązań**.

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 W tym kroku dodasz nazwanym zakresem, obiekt listy oraz dwa przyciski do pierwszego arkusza. Najpierw dodaj nazwany zakres i obiekt listy z **źródeł danych** okna tak, aby automatycznie są one powiązane ze źródłem danych. Następnie dodaj przyciski z **przybornika**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Aby dodać nazwany zakres i obiekt listy

1. Upewnij się, że **Moje Detail.xlsx wzorzec** skoroszyt jest otwarty w Projektancie Visual Studio za pomocą **Arkusz1** wyświetlane.

2. Otwórz **źródeł danych** okna i rozwiń **zamówienia** węzła.

3. Wybierz **OrderID** kolumny, a następnie kliknij strzałkę listy rozwijanej, która pojawia się.

4. Kliknij przycisk **NamedRange** w listy rozwijanej, a następnie przeciągnij **OrderID** kolumny do komórki **A2**.

     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `OrderIDNamedRange` jest tworzony w komórce **A2**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `OrdersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.

5. Przewiń w dół ostatnie kolumn, które podlegają **zamówienia** tabeli. W dolnej części listy jest **Orderdetails** tabeli; jest w tym miejscu, ponieważ jest elementem podrzędnym **zamówienia** tabeli. Wybierz tę opcję, **Orderdetails** tabeli nie ten, który znajduje się w tym samym poziomie co **zamówienia** tabeli, a następnie kliknij strzałkę listy rozwijanej, która pojawia się.

6. Kliknij przycisk **ListObject** w listy rozwijanej, a następnie przeciągnij **OrderDetails** tabeli do komórki **A6**.

7. A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie **Order_DetailsListObject** jest tworzony w komórce **A6**i powiązane z <xref:System.Windows.Forms.BindingSource>.

### <a name="to-add-two-buttons"></a>Aby dodać dwa przyciski

1. Z **wspólnych formantów** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> kontrolkę komórki **A3** arkusza.

    Ta pozycja nosiła `Button1`.

2. Dodaj kolejną <xref:System.Windows.Forms.Button> kontrolkę komórki **B3** arkusza.

    Ta pozycja nosiła `Button2`.

   Następnie oznaczyć zestaw danych w pamięci podręcznej w dokumencie.

## <a name="cache-the-dataset"></a>Zestaw danych w pamięci podręcznej
 Oznacz zestaw danych przechowywanie w pamięci podręcznej w dokumencie, wprowadzając zestawu danych publicznych i ustawienie **CacheInDocument** właściwości.

### <a name="to-cache-the-dataset"></a>Do zestawu danych w pamięci podręcznej

1. Wybierz **NorthwindDataSet** w zasobniku składnika.

2. W **właściwości** oknie zmiany **Modyfikatory** właściwości **publicznych**.

    Zestawy danych muszą być publiczne, zanim buforowanie jest włączone.

3. Zmiana **CacheInDocument** właściwości **True**.

   Następnym krokiem jest, aby dodać tekst do przycisków, a w języku C# Dodaj kod, aby Podłączanie programów obsługi zdarzeń.

## <a name="initialize-the-controls"></a>Inicjowanie kontrolki
 Ustawianie tekstu przycisku i dodawanie obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzeń.

### <a name="to-initialize-the-data-and-the-controls"></a>Aby zainicjować danych i kontrolek

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst przycisków.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. W przypadku tylko język C#, dodać procedury obsługi zdarzeń dla przycisku kliknij zdarzenia `Sheet1_Startup` metody.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodaj kod, aby włączyć przewijanie rekordów
 Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń każdego przycisku do przechodzenia między rekordami.

### <a name="to-scroll-through-the-records"></a>Do przewijania rekordów

1. Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button1`i Dodaj następujący kod, aby przesunąć się do tyłu rekordy:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button2`i Dodaj następujący kod w celu przechodzenia do rekordów:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można przetestować skoroszytu w taki sposób, aby upewnić się, że dane są wyświetlane zgodnie z oczekiwaniami i których rozwiązanie można używać w trybie offline.

### <a name="to-test-the-data-caching"></a>Aby przetestować, buforowanie danych

1. Naciśnij klawisz **F5**.

2. Sprawdź, czy nazwany zakres i obiekt listy są wypełnione danych ze źródła danych.

3. Przewiń niektórych rekordów za pomocą przycisków.

4. Zapisz skoroszyt, a następnie zamknij skoroszyt i programu Visual Studio.

5. Wyłącz połączenie z bazą danych. Odłącz kabel sieciowy z komputera, jeśli baza danych znajduje się na serwerze lub Zatrzymaj usługę programu SQL Server, jeśli baza danych znajduje się na komputerze deweloperskim.

6. Otwórz program Excel, a następnie otwórz **Moje Detail.xlsx wzorzec** z *\bin* katalogu (*\My Master-Detail\bin* w języku Visual Basic lub *\My Master-Detail\bin\ debugowanie* w języku C#).

7. Przewiń rekordów, aby zobaczyć, że arkusz działa normalnie po rozłączeniu.

8. Ponownie nawiąż połączenie z bazą danych. Ponownie nawiąż połączenie komputera z siecią, jeśli baza danych znajduje się na serwerze lub uruchom usługi programu SQL Server, jeśli baza danych znajduje się na komputerze deweloperskim.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawowe informacje dotyczące tworzenia relacji wzorzec/szczegół danych w arkuszu kalkulacyjnym i buforowania zestawu danych. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz także
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Dane w pamięci podręcznej](../vsto/caching-data.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
