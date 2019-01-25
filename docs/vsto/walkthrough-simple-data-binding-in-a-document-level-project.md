---
title: 'Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5ae634a87e8b105df88fed4168b6a70909efbc7f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869004"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu
  W tym instruktażu przedstawiono podstawy powiązanie danych w projektach na poziomie dokumentu. Jedno pole danych w bazie danych programu SQL Server jest powiązana z nazwanym zakresem w programie Microsoft Office Excel. Przewodnik pokazuje także sposobu dodawania formantów, które umożliwiają użytkownikowi przewiń wszystkie rekordy w tabeli.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie źródła danych w projekcie programu Excel.  
  
- Dodawanie formantów do arkusza.  
  
- Przewijanie rekordów bazy danych.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do serwera z przykładową bazą danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 W tym kroku utworzysz projektu skoroszytu programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1. Utwórz projektu skoroszytu programu Excel o nazwie **Moje proste powiązanie danych**, za pomocą Visual Basic lub C#. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje proste powiązanie danych** projekt **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.  
  
### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.  
  
2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3. Wybierz **bazy danych** a następnie kliknij przycisk **dalej**.  
  
4. Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie, używając **nowe połączenie** przycisku.  
  
5. Po zostało wybrane lub utworzyć połączenie, kliknij przycisk **dalej**.  
  
6. Usuń zaznaczenie opcji, aby zapisać połączenie, jeśli jest ono zaznaczone, a następnie kliknij **dalej**.  
  
7. Rozwiń **tabel** w węźle **obiektów bazy danych** okna.  
  
8. Zaznacz pole wyboru obok pozycji **klientów** tabeli.  
  
9. Kliknij przycisk **Zakończ**.  
  
   Kreator dodaje **klientów** do tabeli **źródeł danych** okna. Dodaje także typizowany zestaw danych do projektu, który jest widoczny w **Eksploratora rozwiązań**.  
  
## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 W tym przewodniku potrzebujesz dwóch nazwane zakresy i cztery przyciski pierwszego arkusza. Najpierw dodaj dwa nazwane zakresy z **źródeł danych** okna tak, aby automatycznie są one powiązane ze źródłem danych. Następnie dodaj przyciski z **przybornika**.  
  
### <a name="to-add-two-named-ranges"></a>Aby dodać dwa nazwane zakresy  
  
1.  Upewnij się, że *Moje proste Binding.xlsx danych* skoroszyt jest otwarty w Projektancie Visual Studio za pomocą **Arkusz1** wyświetlane.  
  
2.  Otwórz **źródeł danych** okna i rozwiń **klientów** węzła.  
  
3.  Wybierz **CompanyName** kolumny, a następnie kliknij strzałkę listy rozwijanej, która pojawia się.  
  
4.  Wybierz **NamedRange** w listy rozwijanej, a następnie przeciągnij **CompanyName** kolumny do komórki **A1**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `companyNameNamedRange` jest tworzony w komórce **A1**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
5.  Wybierz **CustomerID** kolumny w **źródeł danych** okna, a następnie kliknij strzałkę listy rozwijanej, która pojawia się.  
  
6.  Kliknij przycisk **NamedRange** w listy rozwijanej, a następnie przeciągnij **CustomerID** kolumny do komórki **B1**.  
  
7.  Inny <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `customerIDNamedRange` jest tworzony w komórce **B1**i powiązane z <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Aby dodać cztery przyciski  
  
1. Z **wspólnych formantów** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> kontrolkę komórki **A3** arkusza.  
  
    Ta pozycja nosiła `Button1`.  
  
2. Dodawanie trzech przycisków do następujących komórek w następującej kolejności, tak, aby nazwy są, jak pokazano:  
  
   |Komórki|(Nazwa)|  
   |----------|--------------|  
   |B3|Button2|  
   |C3|Button3|  
   |D3|Button4|  
  
   Następnym krokiem jest dodanie tekstu, przycisków, a w C# Dodawanie obsługi zdarzeń.  
  
## <a name="initialize-the-controls"></a>Inicjowanie kontrolki  
 Ustawianie tekstu przycisku i dodawanie obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń.  
  
### <a name="to-initialize-the-controls"></a>Aby zainicjować kontrolki  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.  
  
2. Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst dla każdego przycisku.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. W przypadku tylko język C#, dodać procedury obsługi zdarzeń dla przycisku kliknij zdarzenia `Sheet1_Startup` metody.  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   Teraz Dodaj kod, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia przycisków, aby umożliwić użytkownikom przeglądanie rekordy.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Dodaj kod, aby włączyć przewijanie rekordów  
 Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń każdego przycisku do przechodzenia między rekordami.  
  
### <a name="to-move-to-the-first-record"></a>Aby przejść do pierwszego rekordu  
  
1.  Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button1` przycisku i Dodaj następujący kod, aby przejść do pierwszego rekordu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Aby przejść do poprzedniej rekordu  
  
1.  Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button2` przycisku i Dodaj następujący kod do jego położenia wstecz o jeden:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Aby przejść do następnego rekordu  
  
1.  Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button3` przycisku i Dodaj następujący kod, aby awansować pozycji o jeden:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Przejdź do ostatniego rekordu  
  
1.  Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button4` przycisku i Dodaj następujący kod, aby przejść do ostatniego rekordu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować skoroszytu, aby upewnić się, mogą przeglądać rekordy w bazie danych.  
  
### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że pierwszy rekord pojawi się w komórkach **A1** i **B1**.  
  
3.  Kliknij przycisk **>** (`Button3`) znajdujący się i upewnij się, że następnego rekordu jest wyświetlana w komórce **A1** i **B1**.  
  
4.  Kliknij przycisk inne przyciski przewijania, aby upewnić się, że rekord zmienia się zgodnie z oczekiwaniami.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe informacje dotyczące powiązania nazwanego zakresu do pola w bazie danych. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:  
  
-   Buforuje te dane, dzięki czemu mogą być używane w trybie offline. Aby uzyskać więcej informacji, zobacz [jak: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Powiązać z komórek do wielu kolumn w tabeli, a nie jedno pole. Aby uzyskać więcej informacji, zobacz [instruktażu: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Użyj <xref:System.Windows.Forms.BindingNavigator> kontroli do przewijania rekordów. Aby uzyskać więcej informacji, zobacz [jak: Nawigowanie po danych za pomocą kontrolki BindingNavigator formularzy Windows](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
