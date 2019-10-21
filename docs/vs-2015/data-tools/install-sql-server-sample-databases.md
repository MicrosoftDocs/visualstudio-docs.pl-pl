---
title: Instalowanie SQL Server przykładowych baz danych | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3991d3b741162b4b1993e5359ad427c17f00321a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651528"
---
# <a name="install-sql-server-sample-databases"></a>Instalowanie przykładowych baz danych programu SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przykładowe bazy danych są przydatne do eksperymentowania z kwerendami SQL i LINQ, danymi do Entity Framework modelowania i tak dalej.  Każdy produkt bazy danych ma własne przykładowe bazy danych. Northwind i AdventureWorks to dwie popularne SQL Server przykładowe bazy danych.

 **AdventureWorks** to bieżąca Przykładowa baza danych udostępniona dla SQL Server produktów. Możesz pobrać go jako plik. mdf ze [strony AdventureWorks w witrynie CodePlex](http://msftdbprodsamples.codeplex.com/). W tym miejscu są dostępne regularne i uproszczone (LT) wersje bazy danych. W większości scenariuszy preferowana jest wersja LT, ponieważ jest ona mniej złożona.

 **Northwind** to stosunkowo prosta baza danych SQL Server, która była używana przez wiele lat. Możesz pobrać go jako plik. bak ze [strony bazy danych Northwind na CodePlex](https://northwinddatabase.codeplex.com/). Aby uniknąć problemów z uprawnieniami, rozpakuj plik do nowego folderu, który nie znajduje się w folderze użytkownika.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Aby przywrócić bazę danych z pliku. bak w programie Visual Studio

1. W przypadku tworzenia kopii zapasowej bazy danych Microsoft SQL Server wynik jest plikiem. bak. Aby plik. bak można było użyć ponownie jako plik bazy danych, należy go *przywrócić*. W menu głównym wybierz pozycję **wyświetl**  > **Eksplorator obiektów SQL Server**. Jeśli go nie widzisz, może być konieczne jego zainstalowanie. Przejdź do **Panelu sterowania** ,  > **programy i funkcje**, Znajdź Microsoft Visual Studio 2015, a następnie kliknij przycisk **Zmień** . Gdy lista zainstalowanych składników zostanie wyświetlona w oknie instalatora, zaznacz pole wyboru **Eksplorator obiektów SQL Server** a następnie kontynuuj instalację.

2. W Eksplorator obiektów SQL Server kliknij prawym przyciskiem myszy dowolny aparat SQL Server Database (na przykład LocalDB), a następnie wybierz pozycję**nowe zapytanie**.

     ![Eksplorator obiektów SQL Server nowe zapytanie](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Eksplorator obiektów SQL Server nowe zapytanie")

3. Najpierw potrzebne są nazwy logiczne bazy danych i plików dziennika w pliku bak. Aby to zrobić, należy wprowadzić to zapytanie do edytora zapytań SQL, a następnie wybrać zielony przycisk **uruchamiania** w górnej części okna. Zmodyfikuj ścieżkę pliku, jeśli jest to konieczne, aby wskazać plik. bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Zapisz nazwy logiczne, które pojawiają się w oknie wyników.  W przypadku bazy danych Northwind dwie nazwy logiczne to Northwind i Northwind_log.

4. Teraz uruchom to zapytanie, aby utworzyć bazę danych. Zastąp własne ścieżki źródłowe i docelowe, logiczne nazwy baz danych i fizyczne nazwy plików dla Northwind, zgodnie z potrzebami. Zachowaj rozszerzenia. mdf i. ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. W Eksplorator obiektów SQL Server kliknij prawym przyciskiem myszy węzeł bazy **danych** i zobacz węzeł bazy danych Northwind. Jeśli nie, kliknij prawym przyciskiem myszy pozycję bazy danych i wybierz polecenie **Dodaj nową bazę danych**. Wprowadź nazwę i lokalizację pliku. mdf, który został właśnie utworzony.

6. Baza danych jest teraz gotowa do użycia jako źródło danych w programie Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Aby przywrócić bazę danych z pliku. bak w SQL Server Management Studio

1. Pobierz SQL Server Management Studio z witryny pobierania.

2. W oknie SSMS **Eksplorator obiektów** kliknij prawym przyciskiem myszy węzeł **bazy danych** , wybierz polecenie**Przywróć bazę danych**i podaj lokalizację pliku. bak.

     ![Przywracanie bazy danych programu SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata. Przywróć bazę danych programu SSMS")
