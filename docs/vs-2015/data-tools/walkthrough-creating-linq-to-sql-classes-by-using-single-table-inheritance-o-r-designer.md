---
title: 'Przewodnik: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7dfd293f5b2219eab6c3a2896c800a1337f2c8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111977"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Przewodnik: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) obsługuje dziedziczenie pojedynczej tabeli, ponieważ jest on zwykle implementowany w systemach relacyjnych. W tym przewodniku rozszerza ogólne kroki podane w [jak: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tematu i zawiera dane rzeczywiste, aby zademonstrować użycie dziedziczenie w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
 Z tego instruktażu wykonasz następujące zadania:  
  
- Utwórz tabelę bazy danych i Dodaj do niego dane.  
  
- Tworzenie aplikacji Windows Forms.  
  
- Dodaj [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] plik do projektu.  
  
- Tworzenie nowych klas jednostek.  
  
- Konfigurowanie do używania dziedziczenia klas jednostek.  
  
- Zapytania odziedziczoną klasę.  
  
- Wyświetlanie danych w formularzu Windows.  
  
## <a name="create-a-table-to-inherit-from"></a>Utwórz tabelę odziedziczone po  
 Aby zobaczyć, jak działa dziedziczenie, będzie tworzenie małej tabeli osoby, użyj go jako klasę bazową a następnie utwórz obiekt pracownika, który dziedziczy z niego.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Do utworzenia tabeli podstawowej, aby zademonstrować dziedziczenia  
  
1. W **Eksploratora serwera**/**Eksplorator bazy danych**, kliknij prawym przyciskiem myszy **tabel** węzła i kliknij przycisk **Dodaj nową tabelę**.  
  
    > [!NOTE]
    >  Można użyć bazy danych Northwind lub innej bazy danych można dodać do tabeli.  
  
2. W Projektancie tabel należy dodać następujące kolumny w tabeli:  
  
    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|  
    |-----------------|---------------|-----------------|  
    |**Identyfikator**|**int**|**False**|  
    |**Typ**|**int**|**True**|  
    |**Imię**|**nvarchar(200)**|**False**|  
    |**Nazwisko**|**nvarchar(200)**|**False**|  
    |**Menedżer**|**int**|**True**|  
  
3. Jako klucz podstawowy, należy ustawić kolumny Identyfikatora.  
  
4. Zapisz tabelę i nadaj mu nazwę **osoby**.  
  
## <a name="add-data-to-the-table"></a>Dodawanie danych do tabeli  
 Aby mogli zweryfikować, że dziedziczenie jest prawidłowo skonfigurowany, tabela musi niektóre dane dla każdej klasy w dziedziczeniu pojedynczej tabeli.  
  
#### <a name="to-add-data-to-the-table"></a>Aby dodać dane do tabeli  
  
1. Otwórz tabelę w widoku danych. (Kliknij prawym przyciskiem myszy **osoby** tabelę **Eksploratora serwera**/**Eksplorator bazy danych** i kliknij przycisk **Pokaż dane tabeli**.)  
  
2. Skopiuj następujące dane do tabeli. (Można go skopiować i następnie wkleić je do tabeli, wybierając cały wiersz w okienku wyników.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**Identyfikator**|**Typ**|**Imię**|**Nazwisko**|**Menedżer**|  
    |**1**|**1**|**Anna**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Hauser**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**ALEXEY**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Akończenie**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**Beata**|**Martin**|**3**|  
    |**12**|**2**|**Krzysztof**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>Utwórz nowy projekt  
 Teraz, po utworzeniu tabeli, należy utworzyć nowy projekt, aby zademonstrować Konfigurowanie dziedziczenia.  
  
#### <a name="to-create-the-new-windows-application"></a>Aby utworzyć nową aplikację Windows  
  
1. Z **pliku** menu, Utwórz nowy projekt.  
  
2. Nadaj projektowi nazwę **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Jest obsługiwane w projektach Visual Basic i C#. Utwórz nowy projekt w jednym z tych języków.  
  
3. Kliknij przycisk **aplikacja interfejsu Windows Forms** szablonu, a następnie kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4. Projekt InheritanceWalkthrough zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Dodawanie składnika LINQ to SQL klas pliku do projektu  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Aby dodać LINQ do SQL pliku do projektu  
  
1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2. Kliknij przycisk **klasy LINQ do SQL** szablonu, a następnie kliknij przycisk **Dodaj**.  
  
     Plik dbml zostanie dodany do projektu i [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] zostanie otwarty.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Tworzenie dziedziczenia za pomocą Projektanta obiektów relacyjnych  
 Konfigurowanie dziedziczenia, przeciągając **dziedziczenia** obiektu z **przybornika** na powierzchnię projektu.  
  
#### <a name="to-create-the-inheritance"></a>Aby utworzyć dziedziczenia  
  
1. W **Eksploratora serwera**/**Eksplorator bazy danych**, przejdź do **osoby** tabelę, która została utworzona wcześniej.  
  
2. Przeciągnij **osoby** tabeli na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] powierzchni projektowej.  
  
3. Przeciągnij sekundy **osoby** tabeli na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] i zmień jego nazwę na **pracowników**.  
  
4. Usuń **Menedżera** właściwość **osoby** obiektu.  
  
5. Usuń **typu**, **identyfikator**, **FirstName**, i **LastName** właściwości z **pracowników** obiektu. (Innymi słowy, Usuń wszystkie właściwości, z wyjątkiem **Menedżera**.)  
  
6. Z **Object Relational Designer** karcie **przybornika**, Utwórz **dziedziczenia** między **osoby** i  **Pracownik** obiektów. Aby to zrobić, kliknij przycisk **dziedziczenia** pozycja **przybornika** i zwolnij przycisk myszy. Następnie kliknij przycisk **pracowników** obiektu a następnie **osoby** obiektu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Wskaż strzałkę na linię dziedziczenia **osoby** obiektu.  
  
7. Kliknij przycisk **dziedziczenia** linia na powierzchni projektowej.  
  
8. Ustaw **właściwość rozróżniacza** właściwości **typu**.  
  
9. Ustaw **wartość dyskryminatora klasy pochodnej** właściwości **2**.  
  
10. Ustaw **wartość dyskryminatora klasy podstawowej** właściwości **1**.  
  
11. Ustaw **domyślne dziedziczenie** właściwości **osoby**.  
  
12. Skompiluj projekt.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Zapytanie odziedziczoną klasę i wyświetlić dane w formularzu  
 Teraz dodasz kod do formularza, który odpytuje dla określonej klasy w modelu obiektów.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Aby utworzyć zapytanie LINQ i wyświetlić wyniki na formularzu  
  
1. Przeciągnij **ListBox** na formularz Form1.  
  
2. Kliknij dwukrotnie formularz, aby utworzyć `Form1_Load` programu obsługi zdarzeń.  
  
3. Dodaj następujący kod do `Form1_Load` program obsługi zdarzeń:  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Uruchom aplikację i sprawdź, czy rekordy wyświetlana w polu listy są wszyscy pracownicy (rekordy, które mają wartość 2 w kolumnie ich typ).  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Naciśnij F5.  
  
2. Sprawdź, czy są wyświetlane tylko te rekordy, które mają wartość 2 w kolumnie ich typu.  
  
3. Zamknij formularz. (Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.)  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Instrukcje: Dodaj LINQ do klas SQL do projektu (Projektant O-R)](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Instrukcje: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Instrukcje: Generowanie modelu obiektu w języku Visual Basic lubC#](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
