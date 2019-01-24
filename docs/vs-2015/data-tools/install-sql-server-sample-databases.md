---
title: Instalowanie programu SQL Server przykładowych baz danych | Dokumentacja firmy Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fc172e9ed91a354918fd536060f97fcbb259a94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765641"
---
# <a name="install-sql-server-sample-databases"></a>Instalowanie programu SQL Server przykładowych baz danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Przykładowe bazy danych są przydatne do eksperymentowania z zapytań SQL i LINQ, powiązań danych, modelowania programu Entity Framework i tak dalej.  Każdy produkt bazy danych ma swój własny przykładowych baz danych. Są dwa popularne przykładowej bazy danych SQL Server, Northwind i AdventureWorks.  
  
 **AdventureWorks** jest bieżącym przykładowej bazy danych udostępniane dla produktów programu SQL Server. Możesz ją pobrać jako plik mdf z [AdventureWorks strony w witrynie Codeplex](http://msftdbprodsamples.codeplex.com/). Brak dostępnych regularne i uproszczone wersje (Litwa), bazy danych w tym miejscu. W przypadku większości scenariuszy wersji LT jest preferowane, ponieważ jest mniej skomplikowany.  
  
 **Northwind** jest stosunkowo prosta bazy danych SQL Server, który został użyty przez wiele lat. Możesz ją pobrać jako plik z rozszerzeniem bak [strona bazy danych Northwind w witrynie CodePlex](https://northwinddatabase.codeplex.com/). Aby uniknąć problemów z uprawnieniami, Rozpakuj plik do nowego folderu, który nie znajduje się w folderze użytkownika.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Aby przywrócić bazę danych z pliku bak, w programie Visual Studio  
  
1.  Podczas wykonywania kopii zapasowej bazy danych programu Microsoft SQL Server, wynik jest plik bak. Aby .bak plików można używać ponownie jako plik bazy danych, musi być *przywrócić*. W menu głównym wybierz **widoku** > **Eksplorator obiektów SQL Server**. Jeśli nie widzisz, konieczne może go zainstalować. Przejdź do **Panelu sterowania** > **programy i funkcje**, Znajdź program Microsoft Visual Studio 2015 i kliknij przycisk **zmiany** przycisku. Gdy w oknie Instalatora zostanie wyświetlona lista zainstalowanych składników, wybierz pozycję **Eksplorator obiektów SQL Server** pole wyboru, a następnie kontynuuj instalację.  
  
2.  W Eksploratorze obiektów programu SQL Server, kliknij prawym przyciskiem myszy dowolnego aparatu bazy danych programu SQL Server (na przykład localdb), a następnie wybierz pozycję**nowe zapytanie**.  
  
     ![SQL Server Object Explorer nowe zapytanie](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server Object Explorer nowe zapytanie")  
  
3.  Najpierw należy logicznej nazwy plików dziennika i bazy danych wewnątrz pliku bak. Aby ją pobrać, wpisz to zapytanie do edytora zapytań SQL, a następnie wybierz zielony **Uruchom** znajdujący się u góry okna. Jeśli to konieczne wskazać plik bak, zmodyfikuj ścieżkę pliku.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Zanotuj nazwy logiczne, które są wyświetlane w oknie wyników.  Dla bazy danych Northwind dwie nazwy logicznej są Northwind i Northwind_log.  
  
4.  Teraz można uruchomić tego zapytania, aby utworzyć bazę danych. Zastąp swoje własne ścieżki źródłowe i docelowe, nazwy logicznej bazy danych i nazwy pliku fizycznego Northwind zgodnie z potrzebami. Zachowaj .mdf i .ldf rozszerzeń plików.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  W Eksploratorze obiektów programu SQL Server, kliknij prawym przyciskiem myszy **baz danych** węzłem, a powinien zostać wyświetlony węzeł bazy danych Northwind. Jeśli nie, kliknij prawym przyciskiem myszy na baz danych i wybierz **Dodaj nową bazę danych**. Wprowadź nazwę i lokalizację pliku .mdf, który został utworzony.  
  
6.  Baza danych jest teraz gotowa do użycia jako źródło danych w programie Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Aby przywrócić bazę danych z pliku bak w programie SQL Server Management Studio  
  
1.  SQL Server Management Studio można pobrać z witryny pobierania.  
  
2.  W programie SSMS **Eksplorator obiektów** okna, kliknij prawym przyciskiem myszy **baz danych** węzeł**Restore Database**i podać lokalizację pliku bak.  
  
     ![Przywracanie bazy danych programu SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata Przywracanie bazy danych programu SSMS")
