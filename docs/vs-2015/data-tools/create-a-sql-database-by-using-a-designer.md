---
title: Tworzenie bazy danych SQL przy użyciu projektanta | Dokumentacja firmy Microsoft
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: f816095992379748b6d1888b5df54dc5433a8306
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436965"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Tworzenie bazy danych SQL za pomocą projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz eksplorować podstawowe zadania, takie jak dodawanie tablic i definiowanie kolumn, używając Visual Studio do tworzenia i aktualizowania lokalnego pliku bazy danych w SQL Server Express LocalDB. Po zakończeniu tego instruktażu można odkryć więcej zaawansowanych możliwości przy użyciu lokalnej bazy danych jako punkt wyjścia dla innych instruktaży, które tego wymagają.  
  
 Można również utworzyć bazę danych przy użyciu programu SQL Server Management Studio (pobrania osobno) lub instrukcji języka Transact-SQL w **Eksplorator obiektów SQL Server** okna narzędzi w programie Visual Studio.  
  
 W czasie instruktażu dowiesz się o następujących zadaniach:  
  
- [Tworzenie projektu i pliku lokalnej bazy danych](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
- [Tworzenie tabel, kolumn, kluczy podstawowych i kluczy obcych](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
- [Wypełnianie tabel danymi](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Do przeprowadzenia tego instruktażu, upewnij się, że masz zainstalowany program SQL Server Data Tools. Na **widoku** menu, powinien zostać wyświetlony **Eksplorator obiektów SQL Server**. Jeśli tak nie jest dostępne, przejdź do **apletu Dodaj lub usuń programy**, kliknij przycisk **programu Visual Studio 2015**, wybierz opcję **zmiany**, a następnie zaznacz pole obok pozycji **SQL Server Data Tools**.  
  
## <a name="BKMK_CreateNewSQLDB"></a> Tworzenie projektu i pliku lokalnej bazy danych  
  
#### <a name="to-create-a-project-and-a-database-file"></a>Aby utworzyć projekt i plik bazy danych  
  
1. Utwórz projekt Windows Forms o nazwie `SampleDatabaseWalkthrough`.  
  
2. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3. Na liście szablonów elementów przewiń w dół i wybierz **usługową bazę danych**.  
  
    ![Okno dialogowe Szablony elementu](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. Nazwij bazę danych **SampleDatabase**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
5. Jeśli **źródeł danych** okno nie jest otwarte, otwórz go, wybierając klawisze Shift + Alt + D lub na pasku menu, wybierając **widoku** > **Windows inne**  >  **Źródeł danych**.  
  
6. W **źródeł danych** wybierz **Dodaj nowe źródło danych** łącza.  
  
7. W **Kreatora konfiguracji źródła danych**, wybierz opcję **dalej** cztery razy, aby zaakceptować ustawienia domyślne, a następnie wybierz przycisk **Zakończ** przycisku.  
  
   Otwierając okno właściwości bazy danych, możesz wyświetlić parametry połączenia i lokalizację głównego pliku bazy danych (mdf). Zobaczysz, że plik bazy danych znajduje się w folderze projektu.  
  
- W programie Visual Studio, wybierz **widoku** > **Eksplorator obiektów SQL Server** Jeśli to okno nie jest jeszcze otwarte. Otwórz okno właściwości, rozwijając **połączeń danych** węzła, otwierając menu skrótów pliku sampledatabase.mdf i wybierając **właściwości**.  
  
- Alternatywnie, można wybrać **widoku** > **Eksploratora serwera**, jeśli to okno nie jest jeszcze otwarte. Otwórz okno właściwości, rozwijając **połączeń danych** węzła. Otwórz menu skrótów pliku sampledatabase.mdf, a następnie wybierz **właściwości**.  
  
## <a name="BKMK_CreateNewTbls"></a> Tworzenie tabel, kolumn, kluczy podstawowych i kluczy obcych  
 W tej sekcji utworzysz kilka tabel, klucz podstawowy w każdej tabeli i kilka wierszy przykładowych danych. W następnym instruktażu dowiesz się, jak te informacje mogą pojawiać się w aplikacji. Utworzysz też klucz obcy, aby określić, jak rekordy w jednej tabeli mogą odpowiadać rekordom w drugiej tabeli.  
  
#### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers  
  
1. W **Eksploratora serwera** lub **Eksplorator obiektów SQL Server**, rozwiń węzeł **połączeń danych** węzła, a następnie rozwiń węzeł **SampleDatabase.mdf**węzła.  
  
2. Otwórz menu skrótów dla **tabel**, a następnie wybierz pozycję **Dodaj nową tabelę**.  
  
     **Projektanta tabel** otwiera i pokazuje siatkę z jednym domyślnym wierszem, który reprezentuje pojedynczą kolumnę w tabeli, które tworzysz. Przez dodawanie wierszy do siatki dodajesz kolumny w tabeli.  
  
3. W siatce dodaj wiersz dla każdego z poniższych wpisów:  
  
    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (usunięty)|  
    |`CompanyName`|`nvarchar(50)`|False (usunięty)|  
    |`ContactName`|`nvarchar (50)`|True (wybrane)|  
    |`Phone`|`nvarchar (24)`|True (wybrane)|  
  
4. Otwórz menu skrótów dla `CustomerID` wiersza, a następnie wybierz pozycję **Ustaw klucz podstawowy**.  
  
5. Otwórz menu skrótów dla domyślnego wiersza, a następnie wybierz **Usuń**.  
  
6. Nadaj tabeli nazwę Customers, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     Powinien zostać wyświetlony podobny do poniższego:  
  
     ![Tabela projektanta](../data-tools/media/raddata-table-designer.png "raddata Projektant tabel")  
  
7. W lewym górnym rogu **projektanta tabel**, wybierz opcję **aktualizacji** przycisku.  
  
8. W **Podgląd aktualizacji bazy danych** okno dialogowe, wybierz opcję **Aktualizuj bazę danych** przycisku.  
  
     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.  
  
#### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders  
  
1. Dodaj inną tabelę, a następnie dodaj wiersz dla każdego wpisu w tabeli poniżej:  
  
    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (usunięty)|  
    |`CustomerID`|`nchar(5)`|False (usunięty)|  
    |`OrderDate`|`datetime`|True (wybrane)|  
    |`OrderQuantity`|`int`|True (wybrane)|  
  
2. Ustaw **OrderID** jako klucz podstawowy, a następnie usuń domyślny wiersz.  
  
3. Nadaj tabeli nazwę Orders, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4. W lewym górnym rogu **projektanta tabel**, wybierz opcję **aktualizacji** przycisku.  
  
5. W **Podgląd aktualizacji bazy danych** okno dialogowe, wybierz opcję **Aktualizuj bazę danych** przycisku.  
  
     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.  
  
#### <a name="to-create-a-foreign-key"></a>Aby utworzyć obcy klucz  
  
1. W okienku kontekstowym po prawej stronie siatki, otwórz menu skrótów dla **klucze obce**, a następnie wybierz pozycję **Dodaj nowy klucz obcy**, jak pokazano na poniższej ilustracji.  
  
     ![Dodawanie klucza obcego w Projektancie tabel](../data-tools/media/foreignkey.png "klucza obcego")  
  
2. W wyświetlonym polu tekstowym Zamień **ToTable** z `Customers`.  
  
3. W okienku języka T-SQL zaktualizuj ostatni wiersz, aby dopasować następujący przykład:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4. W lewym górnym rogu **projektanta tabel**, wybierz opcję **aktualizacji** przycisku.  
  
5. W **Podgląd aktualizacji bazy danych** okno dialogowe, wybierz opcję **Aktualizuj bazę danych** przycisku.  
  
     Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.  
  
## <a name="BKMK_Populating"></a> Wypełnianie tabel danymi  
  
#### <a name="to-populate-the-tables-with-data"></a>Aby wypełnić tabele danymi  
  
1. W **Eksploratora serwera** lub **Eksplorator obiektów SQL Server**, rozwiń węzeł przykładowej bazy danych.  
  
2. Otwórz menu skrótów dla **tabel** węzeł **Odśwież**, a następnie rozwiń węzeł **tabel** węzła.  
  
3. Otwórz menu skrótów dla tabeli Customers, a następnie wybierz **Pokaż dane tabeli**.  
  
4. Dodaj wszelkie dane, jakie chcesz dla co najmniej trzech klientów.  
  
     Można określić dowolne pięć znaków jako identyfikatory klienta, ale należy wybrać co najmniej jeden, który można zapamiętać do użycia w dalszej części tej procedury.  
  
5. Otwórz menu skrótów dla tabeli zamówienia, a następnie wybierz **Pokaż dane tabeli**.  
  
6. Dodawanie danych dla co najmniej trzech zamówień.  
  
    > [!IMPORTANT]
    > Upewnij się, że wszystkie identyfikatory zamówień i ilości zamówienia są liczbami całkowitymi i że każdy identyfikator klienta odpowiada wartości określonej w kolumnie CustomerID w tabeli Customers.  
  
7. Na pasku menu wybierz **pliku** > **Zapisz wszystko**.  
  
8. Na pasku menu wybierz **pliku** > **Zamknij rozwiązanie**.  
  
    > [!NOTE]
    > Zgodnie z zaleceniami można zrobić kopię zapasową pliku bazy danych, która właśnie została utworzona przez skopiowanie jej i następnie wklejenie kopii w innej lokalizacji lub nadając kopii pod inną nazwą.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy posiadasz plik lokalnej bazy danych, z pewnymi przykładowymi danymi, można wykonać instruktaży, które przedstawiają zadania bazy danych.
