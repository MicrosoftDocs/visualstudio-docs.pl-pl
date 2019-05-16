---
title: 'Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db27e8665d74477f3bb668831cbfaeef00d622bd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700225"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) udostępnia powierzchnia projektowania wizualnego służące do tworzenia i edytowania [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy (klas jednostek), które są oparte na obiektach w bazie danych. Za pomocą [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), można użyć technologii LINQ do dostępu do bazy danych z programu SQL. Aby uzyskać więcej informacji, zobacz [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Domyślnie logiki, aby przeprowadzić aktualizacje są dostarczane przez [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego. Środowisko uruchomieniowe tworzy domyślne instrukcji Insert, Update i Delete na podstawie schematu tabeli (definicje kolumn i informacje o kluczu podstawowym). Gdy użytkownik nie chce Użyj zachowania domyślnego, można skonfigurować zachowanie aktualizacji i wyznaczyć określonych procedur składowanych do wykonania niezbędnych operacji wstawiania, aktualizacji, i usuwa wymagane do pracy z danymi w bazie danych. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład, gdy Twoje klas jednostek mapy do widoków. Ponadto można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabel za pomocą procedur składowanych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacje, przy użyciu procedur składowanych](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
> Ten poradnik wymaga dostępności **InsertCustomer**, **UpdateCustomer**, i **DeleteCustomer** procedury składowane dla bazy danych Northwind.
  
 Ten przewodnik zawiera kroki, które należy wykonać, aby zastąpić domyślne LINQ do zachowania w czasie wykonywania SQL do zapisywania danych do bazy danych przy użyciu procedur składowanych.  
  
 Z tego instruktażu dowiesz się, jak wykonywać następujące zadania:  
  
- Tworzenie nowej aplikacji Windows Forms i Dodaj [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] pliku do niego.  
  
- Utwórz klasę jednostki, który jest zamapowany do tabeli klientów Northwind.  
  
- Utwórz źródło danych obiektu, który odwołuje się do programu LINQ do klas SQL klienta.  
  
- Tworzenie formularza Windows, który zawiera <xref:System.Windows.Forms.DataGridView> , jest powiązany z klasy klienta.  
  
- Implementowanie zapisać funkcjonalności formularza.  
  
- Tworzenie <xref:System.Data.Linq.DataContext> metod, dodając przechowywane procedury [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
- Konfiguruj klasę odbiorcy, używać procedur składowanych do wykonywania operacji wstawienia, aktualizacje i usunięcia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są następujące elementy:  
  
- Dostęp do wersji programu SQL Server w bazie danych Northwind.
  
- **InsertCustomer**, **UpdateCustomer**, i **DeleteCustomer** procedury składowane dla bazy danych Northwind.
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Tworzenie aplikacji i dodawanie LINQ do klas SQL  
 Ponieważ będzie on pracować z [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy i wyświetlanie danych w formularzu Windows, Utwórz nową aplikację Windows Forms i Dodaj LINQ do klas SQL pliku.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Aby utworzyć nowy projekt aplikacji Windows, który zawiera LINQ do klas SQL  
  
1. Z **pliku** menu, Utwórz nowy projekt.  
  
2. Nadaj projektowi nazwę **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Jest obsługiwana w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i projektów języka C#. W związku z tym Utwórz nowy projekt w jeden z tych języków.  
  
3. Kliknij przycisk **aplikacja interfejsu Windows Forms** szablon i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Projekt UpdatingwithSProcsWalkthrough zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
4. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
5. Kliknij przycisk **klasy LINQ do SQL** szablonu i typ **Northwind.dbml** w **nazwa** pole.  
  
6. Kliknij przycisk **Dodaj**.  
  
     Pusty plik LINQ to SQL klas (Northwind.dbml) jest dodawany do projektu, a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zostanie otwarty.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Tworzenie klas jednostek klienta i źródło danych obiektu  
 Tworzenie [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas, które są mapowane do tabel bazy danych, przeciągając tabel z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Wynik jest LINQ do klas jednostek SQL, które mapują do tabel w bazie danych. Po utworzeniu klasy jednostek, możesz używać jako źródła danych obiektu, podobnie jak inne klasy, które mają właściwości publiczne.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Utwórz klasę jednostki klienta i skonfigurować źródło danych z nią  
  
1. W **Eksploratora serwera**/**Eksplorator bazy danych**, Znajdź w tabeli klienta w wersji programu SQL Server w bazie danych Northwind.
  
2. Przeciągnij **klientów** węzła z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] powierzchni.  
  
     Klasa jednostki o nazwie **klienta** zostanie utworzony. Posiada właściwości, które odnoszą się do kolumn w tabeli Customers. Klasa jednostki nosi nazwę **klienta** (nie **klientów**), ponieważ reprezentuje on jednego klienta z tabeli Customers.  
  
    > [!NOTE]
    > Zmiana nazwy jest to *pluralizacja*. Można je włączyć lub wyłączyć [okno dialogowe Opcje](../ide/reference/options-dialog-box-visual-studio.md). Aby uzyskać więcej informacji, zobacz [jak: Włącz pluralizacja włączać i wyłączać (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3. Na **kompilacji** menu, kliknij przycisk **kompilacji UpdatingwithSProcsWalkthrough** do skompilowania projektu.  
  
4. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
5. W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
6. Kliknij przycisk **obiektu** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
7. Rozwiń **UpdatingwithSProcsWalkthrough** węzła i Znajdź i zaznacz **klienta** klasy.  
  
    > [!NOTE]
    > Jeśli **klienta** klasy nie jest dostępna, Anuluj kreatora, skompiluj projekt i uruchom ponownie kreatora.  
  
8. Kliknij przycisk **Zakończ** Utwórz źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Tworzenie DataGridView do wyświetlania danych klientów w formularzu Windows  
 Tworzenie formantów, które są powiązane z klasami jednostki, przeciągając [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] elementów ze źródła danych **źródeł danych** okna w formularzu Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Aby dodać formanty powiązane z klasami jednostki  
  
1. Otwórz formularz Form1 w widoku Projekt.  
  
2. Z **źródeł danych** okna, przeciągnij **klienta** węzła na formularz Form1.  
  
    > [!NOTE]
    > Aby wyświetlić **źródeł danych** okna, kliknij przycisk **Pokaż źródła danych** na **danych** menu.  
  
3. Otwórz formularz Form1 w edytorze kodu.  
  
4. Dodaj następujący kod do formularza, globalne do formularza, poza określonej metody, ale wewnątrz klasy Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5. Utwórz procedurę obsługi zdarzeń dla `Form_Load` zdarzeń i Dodaj następujący kod do narzędzia obsługi:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## <a name="implementing-save-functionality"></a>Implementowanie funkcja zapisywania  
 Domyślnie, Zapisz przycisk nie jest włączona i nie jest zaimplementowana funkcja zapisywania. Ponadto kod nie jest automatycznie dodawane do zapisać zmienione dane w bazie danych podczas tworzenia formantów powiązanych z danymi dla źródła danych obiektu. W tej sekcji omówiono sposób umożliwienia zapisywania przycisk i zaimplementować Zapisz funkcji [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obiektów.  
  
#### <a name="to-implement-save-functionality"></a>Aby zaimplementować funkcja zapisywania  
  
1. Otwórz formularz Form1 w widoku Projekt.  
  
2. Wybierz opcję Zapisz znajdujący się na **CustomerBindingNavigator** (przycisk z ikoną dyskietki).  
  
3. W **właściwości** oknie **włączone** właściwości **True**.  
  
4. Kliknij dwukrotnie przycisk Zapisz, aby utworzyć program obsługi zdarzeń i przejdź do edytora kodu.  
  
5. Dodaj następujący kod do zapisywania obsługi zdarzeń przycisku:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Zastępowanie domyślnego zachowania do wykonywania aktualizacji (operacje wstawiania, aktualizacji i usuwania)  
  
#### <a name="to-override-the-default-update-behavior"></a>Zastępowanie domyślnego zachowania aktualizacji  
  
1. Otwórz plik LINQ to SQL w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie **Northwind.dbml** w pliku **Eksploratora rozwiązań**.)  
  
2. W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł bazy danych Northwind **procedur składowanych** węzła i Znajdź  **InsertCustomers**, **UpdateCustomers**, i **DeleteCustomers** procedur składowanych.  
  
3. Przeciągnij wszystkie trzy procedury przechowywane na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Procedury składowane są dodawane do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4. Wybierz **klienta** Klasa jednostki w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5. W **właściwości** wybierz **Wstaw** właściwości.  
  
6. Kliknij przycisk wielokropka (...) obok **Użyj środowiska uruchomieniowego** otworzyć **Konfigurowanie zachowania** okno dialogowe.  
  
7. Wybierz **dostosować**.  
  
8. Wybierz **InsertCustomers** method in Class metoda **Dostosuj** listy.  
  
9. Kliknij przycisk **Zastosuj** można zapisać konfiguracji dla wybranej klasy lub zachowania.  
  
    > [!NOTE]
    > Można kontynuować, skonfiguruj zachowanie dla każdej kombinacji klasy/zachowania, tak długo, jak możesz kliknąć pozycję **Zastosuj** po wprowadzeniu każdej zmiany. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, okno dialogowe ostrzeżenia, zapewniając pojawi się możliwości, aby zastosować zmiany.  
  
10. Wybierz **aktualizacji** w **zachowanie** listy.  
  
11. Wybierz **dostosować**.  
  
12. Wybierz **UpdateCustomers** method in Class metoda **Dostosuj** listy.  
  
     Sprawdź listę **argumenty metody** i **właściwości klasy** i zwróć uwagę, że istnieją dwa **argumenty metody** oraz dwóch **właściwości klasy**dla niektórych kolumn w tabeli. To ułatwia śledzenie zmian i tworzenie instrukcji, które sprawdzaj naruszeń współbieżności.  
  
13. Mapa **Original_CustomerID** argument metody **CustomerID (oryginalny)** właściwości klasy.  
  
    > [!NOTE]
    > Domyślnie argumenty metody będzie zmapowana do właściwości klasy, gdy nazwy są zgodne. Jeśli nazwy właściwości zostały zmienione, a nie są już zgodne w tabeli i Klasa jednostki, Niewykluczone, że właściwość odpowiednik klasy do mapowania na, jeśli O/R Designer nie może określić poprawne mapowania. Ponadto, jeśli argumenty metody nie ma właściwości prawidłową klasę do mapowania, możesz ustawić **właściwości klasy** wartość **(Brak)**.  
  
14. Kliknij przycisk **Zastosuj** można zapisać konfiguracji dla wybranej klasy lub zachowania.  
  
15. Wybierz **Usuń** w **zachowanie** listy.  
  
16. Wybierz **dostosować**.  
  
17. Wybierz **DeleteCustomers** method in Class metoda **Dostosuj** listy.  
  
18. Mapa **Original_CustomerID** argument metody **CustomerID (oryginalny)** właściwości klasy.  
  
19. Kliknij przycisk **OK**.  
  
> [!NOTE]
> Chociaż nie jest to problem dla tego konkretnego przewodnika, warto zauważyć, że [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obsługuje wygenerowanych w bazie danych wartości automatycznie tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazy danych) i kolumn sygnatur czasowych podczas wstawiania i aktualizacje. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości wygenerowanych w bazie danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, lub <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Uruchom aplikację ponownie, aby sprawdzić, czy **UpdateCustomers** procedury składowanej poprawnie aktualizuje rekord klienta w bazie danych.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Naciśnij F5.  
  
2. Zmodyfikuj rekord w siatce, aby sprawdzić zachowanie aktualizacji.  
  
3. Dodaj nowy rekord do testowanie zachowania wstawiania.  
  
4. Kliknij przycisk Zapisz, aby zapisać zmiany w bazie danych.  
  
5. Zamknij formularz.  
  
6. Naciśnij klawisz F5, a następnie sprawdź zaktualizowany rekord a nowo wstawionej rekord trwałość.  
  
7. Delete nowe rejestrowanie utworzonego w kroku 3, aby sprawdzić zachowanie dotyczące usuwania.  
  
8. Kliknij przycisk Zapisz przycisk, aby przesłać zmiany i Usuń rekord usuniętych z bazy danych  
  
9. Zamknij formularz.  
  
10. Naciśnij klawisz F5, a następnie sprawdź, czy usunięto rekord został usunięty z bazy danych.  
  
    > [!NOTE]
    > Jeśli aplikacja używa programu SQL Server Express Edition, w zależności od wartości **Kopiuj do katalogu wyjściowego** właściwości pliku bazy danych, zmiany mogą być niewidoczne po naciśnięciu klawisza F5 w kroku 10.
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które warto wykonać po utworzeniu [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas jednostek. Niektóre udoskonalenia, których można dokonać w tej aplikacji są następujące:  
  
- Implementowanie współbieżności sprawdzanie podczas aktualizacji. Aby uzyskać informacje, zobacz [optymistycznej współbieżności: Omówienie](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
- Dodawanie zapytań LINQ do filtrowania danych. Aby uzyskać informacje, zobacz [wprowadzenie do zapytań LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Zapytania LINQ to SQL](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New do tworzenia aplikacji danych w programie Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
