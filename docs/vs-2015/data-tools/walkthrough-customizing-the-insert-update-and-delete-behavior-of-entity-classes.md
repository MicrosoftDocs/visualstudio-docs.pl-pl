---
title: 'Przewodnik: Dostosowywanie zachowania INSERT, Update i DELETE klas jednostek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602573"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Przewodnik: Dostosowywanie zachowania INSERT, Update i DELETE klas jednostek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oferują wizualną powierzchnię projektową do tworzenia i edytowania klas [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] (klasy jednostek), które są oparte na obiektach w bazie danych. Korzystając z [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), można używać technologii LINQ do uzyskiwania dostępu do baz danych SQL. Aby uzyskać więcej informacji, zobacz [LINQ (zapytanie zintegrowane z językiem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Domyślnie logika do wykonywania aktualizacji jest zapewniana przez środowisko uruchomieniowe [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Środowisko uruchomieniowe tworzy domyślne instrukcje INSERT, Update i DELETE w oparciu o schemat tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz używać zachowania domyślnego, możesz skonfigurować zachowanie aktualizacji i wyznaczyć określone procedury składowane do wykonywania niezbędnych operacji wstawiania, aktualizacji i usuwania wymaganych do pracy z danymi w bazie danych. Można to również zrobić, gdy domyślne zachowanie nie jest generowane, na przykład gdy klasy jednostek mapują się na widoki. Ponadto można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabeli za pomocą procedur składowanych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji za pomocą procedur składowanych](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> Ten Instruktaż wymaga dostępności procedur składowanych **InsertCustomer**, **UpdateCustomer**i **DeleteCustomer** dla bazy danych Northwind.

 W tym instruktażu przedstawiono kroki, które należy wykonać, aby zastąpić domyślne zachowanie środowiska uruchomieniowego LINQ to SQL na potrzeby zapisywania danych z powrotem w bazie danych przy użyciu procedur składowanych.

 W tym instruktażu dowiesz się, jak wykonywać następujące zadania:

- Utwórz nową aplikację Windows Forms i Dodaj do niej plik [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].

- Utwórz klasę jednostki, która jest mapowana na tabelę Customers firmy Northwinds.

- Utwórz źródło danych obiektu, które odwołuje się do klasy klienta LINQ to SQL.

- Utwórz formularz systemu Windows zawierający <xref:System.Windows.Forms.DataGridView>, który jest powiązany z klasą klienta.

- Implementowanie funkcji Save dla formularza.

- Utwórz metody <xref:System.Data.Linq.DataContext>, dodając procedury składowane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

- Skonfiguruj klasę Customer, aby używać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są następujące elementy:

- Dostęp do SQL Server wersji przykładowej bazy danych Northwind.

- Procedury składowane **InsertCustomer**, **UpdateCustomer**i **DeleteCustomer** dla bazy danych Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Tworzenie aplikacji i Dodawanie LINQ to SQL klas
 Ponieważ będziesz pracować z klasami [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] i wyświetlać dane w formularzu systemu Windows, Utwórz nową aplikację Windows Forms i Dodaj plik LINQ to SQL klas.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Aby utworzyć nowy projekt aplikacji systemu Windows, który zawiera klasy LINQ to SQL

1. Z menu **plik** Utwórz nowy projekt.

2. Nazwij projekt **UpdatingwithSProcsWalkthrough**.

    > [!NOTE]
    > @No__t_0 jest obsługiwana w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i C# projektach. W związku z tym Utwórz nowy projekt w jednym z tych języków.

3. Kliknij szablon **aplikacji Windows Forms** i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt UpdatingwithSProcsWalkthrough został utworzony i dodany do **Eksplorator rozwiązań**.

4. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

5. Kliknij szablon **LINQ to SQL klas** i wpisz **Northwind. dbml** w polu **Nazwa** .

6. Kliknij przycisk **Dodaj**.

     Do projektu zostanie dodany pusty plik klas LINQ to SQL (Northwind. dbml), a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zostanie otwarty.

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Tworzenie klasy jednostki klienta i źródła danych obiektu
 Utwórz klasy [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], które są mapowane na tabele bazy danych, przeciągając tabele z **Eksplorator serwera** /**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Wynik jest LINQ to SQL klas jednostek, które są mapowane na tabele w bazie danych. Po utworzeniu klas jednostek mogą one być używane jako źródła danych obiektów, podobnie jak inne klasy z właściwościami publicznymi.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Aby utworzyć klasę jednostki klienta i skonfigurować dla niej źródło danych

1. W **Eksplorator serwera** /**Eksplorator bazy danych**Znajdź tabelę Customer w wersji SQL Server przykładowej bazy danych Northwind.

2. Przeciągnij węzeł **Customers** z **Eksplorator serwera** /**Eksplorator bazy danych** na powierzchnię [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Utworzono klasę jednostki o nazwie **Klient** . Ma właściwości, które odpowiadają kolumnom w tabeli Customers. Klasa jednostki nosi nazwę **klienta** (nie **klientów**), ponieważ reprezentuje jednego klienta z tabeli Customers.

    > [!NOTE]
    > Takie zachowanie zmiany nazwy nosi nazwę *pluralizacja*. Można ją włączyć lub wyłączyć w oknie [dialogowym Opcje](../ide/reference/options-dialog-box-visual-studio.md). Aby uzyskać więcej informacji, zobacz [How to: skręć pluralizacja on and off (Projektant O/R)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. W menu **kompilacja** kliknij pozycję **Kompiluj UpdatingwithSProcsWalkthrough** , aby skompilować projekt.

4. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

5. W oknie **źródła danych** kliknij pozycję **Dodaj nowe źródło danych**.

6. Kliknij pozycję **obiekt** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

7. Rozwiń węzeł **UpdatingwithSProcsWalkthrough** i Znajdź i wybierz klasę **Customer (klient** ).

    > [!NOTE]
    > Jeśli Klasa **Customer** jest niedostępna, Anuluj działanie kreatora, Skompiluj projekt i ponownie uruchom kreatora.

8. Kliknij przycisk **Zakończ** , aby utworzyć źródło danych i dodać klasę jednostki **klienta** do okna **źródła danych** .

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Tworzenie kontrolki DataGridView do wyświetlania danych klienta w formularzu systemu Windows
 Utwórz formanty, które są powiązane z klasami jednostek, przeciągając elementy [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] źródła danych z okna **źródła danych** na formularz systemu Windows.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Aby dodać formanty, które są powiązane z klasami jednostek

1. Otwórz formularz Form1 w widok Projekt.

2. W oknie **źródła danych** przeciągnij węzeł **klienta** na formularz Form1.

    > [!NOTE]
    > Aby wyświetlić okno **źródła danych** , kliknij przycisk **Pokaż źródła danych** w menu **dane** .

3. Otwórz formularz Form1 w edytorze kodu.

4. Dodaj następujący kod do formularza, który jest globalny do formularza, poza dowolną określoną metodą, ale wewnątrz klasy Form1:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. Utwórz procedurę obsługi zdarzeń dla zdarzenia `Form_Load` i Dodaj następujący kod do programu obsługi:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;

    ```

## <a name="implementing-save-functionality"></a>Implementowanie funkcji zapisywania
 Domyślnie przycisk Zapisz nie jest włączony i funkcja zapisywania nie jest zaimplementowana. Ponadto kod nie jest automatycznie dodawany do zapisywania zmienionych danych w bazie danych, gdy dla źródeł danych obiektów tworzone są kontrolki powiązane z danymi. W tej sekcji wyjaśniono, jak włączyć przycisk Zapisz i zaimplementować funkcję Save dla [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obiektów.

#### <a name="to-implement-save-functionality"></a>Aby zaimplementować funkcję zapisywania

1. Otwórz formularz Form1 w widok Projekt.

2. Wybierz przycisk Zapisz na **CustomerBindingNavigator** (przycisk z ikoną dyskietki).

3. W oknie **Właściwości** ustaw właściwość **Enabled** na **wartość true**.

4. Kliknij dwukrotnie przycisk Zapisz, aby utworzyć program obsługi zdarzeń i przełączyć się do edytora kodu.

5. Dodaj następujący kod do programu obsługi zdarzeń przycisku Zapisz:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Zastępowanie domyślnego zachowania dla przeprowadzania aktualizacji (wstawia, aktualizuje i usuwa)

#### <a name="to-override-the-default-update-behavior"></a>Aby zastąpić domyślne zachowanie aktualizacji

1. Otwórz plik LINQ to SQL w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie plik **Northwind. dbml** w **Eksplorator rozwiązań**).

2. W **Eksplorator serwera** /**Eksplorator bazy danych**rozwiń węzeł **procedury składowane** bazy danych Northwind, a następnie zlokalizuj procedury składowane **InsertCustomers**, **UpdateCustomers**i **DeleteCustomers** .

3. Przeciągnij wszystkie trzy procedury składowane na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Procedury składowane są dodawane do okienka metody jako metody <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki **klienta** w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

5. W oknie **Właściwości** wybierz właściwość **Wstaw** .

6. Kliknij przycisk wielokropka (...) obok pozycji **Użyj środowiska uruchomieniowego** , aby otworzyć okno dialogowe **Konfigurowanie zachowania** .

7. Wybierz pozycję **Dostosuj**.

8. Wybierz metodę **InsertCustomers** na liście **Dostosuj** .

9. Kliknij przycisk **Zastosuj** , aby zapisać konfigurację wybranej klasy i zachowania.

    > [!NOTE]
    > Można nadal skonfigurować zachowanie dla każdej kombinacji klas/zachowań, o ile po wprowadzeniu każdej zmiany klikniesz przycisk **Zastosuj** . Jeśli zmienisz klasę lub zachowanie przed kliknięciem przycisku **Zastosuj**, zostanie wyświetlone okno dialogowe z ostrzeżeniem z możliwością zastosowania wszelkich zmian.

10. Na liście **zachowanie** wybierz pozycję **Aktualizuj** .

11. Wybierz pozycję **Dostosuj**.

12. Wybierz metodę **UpdateCustomers** na liście **Dostosuj** .

     Sprawdź listę **argumentów metod** i **właściwości klasy** oraz Zwróć uwagę na to, że istnieją dwa **argumenty metody** i dwie **właściwości klasy** dla niektórych kolumn w tabeli. Ułatwia to śledzenie zmian i Tworzenie instrukcji, które sprawdzają naruszenia współbieżności.

13. Mapuj argument metody **Original_CustomerID** na właściwość klasy **CustomerID (oryginalna)** .

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Jeśli nazwy właściwości są zmieniane i nie są już zgodne między tabelą a klasą jednostki, może być konieczne wybranie równoważnej właściwości klasy do zamapowania, jeśli Projektant O/R nie może określić poprawnego mapowania. Ponadto jeśli argumenty metody nie mają prawidłowych właściwości klasy do zamapowania, można ustawić wartość **właściwości klasy** na **(brak)** .

14. Kliknij przycisk **Zastosuj** , aby zapisać konfigurację wybranej klasy i zachowania.

15. Na liście **zachowanie** wybierz pozycję **Usuń** .

16. Wybierz pozycję **Dostosuj**.

17. Wybierz metodę **DeleteCustomers** na liście **Dostosuj** .

18. Mapuj argument metody **Original_CustomerID** na właściwość klasy **CustomerID (oryginalna)** .

19. Kliknij przycisk **OK**.

> [!NOTE]
> Chociaż nie jest to problem z tym konkretnym instruktażem, warto zauważyć, że [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] automatycznie obsługuje wartości generowane przez bazę danych dla tożsamości (Automatyczne zwiększenie), ROWGUIDCOL (GUID wygenerowanej przez bazę danych) i kolumn sygnatur czasowych podczas wstawiania i Dostępności. Wartości wygenerowane przez bazę danych w innych typach kolumn nieoczekiwanie spowodują wartość null. Aby zwrócić wartości generowane przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> na `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> jedną z następujących opcji: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> lub <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Testowanie aplikacji
 Uruchom aplikację ponownie, aby sprawdzić, czy w ramach procedury składowanej **UpdateCustomers** prawidłowo Zaktualizowano rekord klienta w bazie danych.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij F5.

2. Zmodyfikuj rekord w siatce, aby przetestować zachowanie aktualizacji.

3. Dodaj nowy rekord, aby przetestować zachowanie wstawiania.

4. Kliknij przycisk Zapisz, aby zapisać zmiany z powrotem w bazie danych.

5. Zamknij formularz.

6. Naciśnij klawisz F5 i sprawdź, czy zaktualizowany rekord i nowo wstawionego rekordu zostały utrwalone.

7. Usuń nowy rekord utworzony w kroku 3, aby przetestować zachowanie usuwania.

8. Kliknij przycisk Zapisz, aby przesłać zmiany i usunąć usunięty rekord z bazy danych

9. Zamknij formularz.

10. Naciśnij klawisz F5 i sprawdź, czy usunięty rekord został usunięty z bazy danych.

    > [!NOTE]
    > Jeśli aplikacja używa wersji SQL Server Express, w zależności od wartości właściwości **Kopiuj do katalogu wyjściowego** pliku bazy danych, zmiany mogą nie pojawiać się po naciśnięciu klawisza F5 w kroku 10.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klas jednostek. Niektóre ulepszenia, które można wprowadzić w tej aplikacji, to m.in.:

- Zaimplementuj sprawdzanie współbieżności podczas aktualizacji. Aby uzyskać więcej informacji, zobacz [optymistyczne współbieżność: Omówienie](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Dodaj zapytania LINQ do filtrowania danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytańC#LINQ ()](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL zapytań](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) [metod elementów DataContext (Projektant o/r)](../data-tools/datacontext-methods-o-r-designer.md) [instrukcje: przypisywanie procedur składowanych do przeprowadzania aktualizacji, wstawianych i usuwanych (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Pave nowości dla Opracowywanie aplikacji dla danych w programie Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
