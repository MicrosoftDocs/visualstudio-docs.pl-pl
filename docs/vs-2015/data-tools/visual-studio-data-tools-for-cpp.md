---
title: Narzędzia Visual Studio data tools dla języka C++ | Dokumentacja firmy Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 85978a79fc1e0110e5b13d6dc0e3198d20ac674a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146594"
---
# <a name="visual-studio-data-tools-for-c"></a>Narzędzia do obsługi danych programu Visual Studio dla języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Natywnych języka C++ często może zapewnić największą wydajność, gdy uzyskują dostęp do źródeł danych. Jednak dane narzędzia dla aplikacji w języku C++ w programie Visual Studio nie są tak zaawansowane jak w przypadku aplikacji .NET. Na przykład okna źródeł danych nie można ich przeciąganie i upuszczanie źródeł danych na powierzchnię projektu C++. Jeśli potrzebujesz warstwa obiektowo relacyjny, należy napisać własny lub użyj innej firmy.  To samo dotyczy funkcji wiązania danych, mimo że aplikacje korzystające z biblioteki MFC można użyć niektórych klas baz danych, wraz z dokumentami i widokami, przechowywanie danych w pamięci i wyświetlania ich do użytkownika. Aby uzyskać więcej informacji, zobacz [dostęp do danych w programie Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .  
  
 Aby połączyć z bazy danych SQL, natywnych aplikacji w języku C++ można użyć sterowników ODBC i OLE DB i ADO dostawcy, które są dołączone do Windows.     Te można nawiązać dowolnej bazy danych, która obsługuje te interfejsy. Sterownik ODBC jest standardowym. OLE DB zapewnia zgodność z poprzednimi wersjami. Aby uzyskać więcej informacji na temat tych technologii danych, zobacz [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Aby korzystać z zalet funkcji niestandardowych w programie SQL Server 2005 i później użyć [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Natywny klient zawiera także sterownika SQL Server ODBC i SQL Server dostawcy OLE DB w jednej bibliotece dołączanej dynamicznie (DLL). Obsługuje te aplikacje za pomocą API kodu macierzystego (ODBC, OLE DB i ADO) do programu Microsoft SQL Server.  Instaluje program SQL Server Native Client z SQL Server Data Tools. Podręcznik programowania jest tutaj: [Programowanie programu SQL Server Native Client](https://msdn.microsoft.com/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Nawiązywanie połączenia z localDB, ODBC i SQL Native Client w aplikacji w języku C++  
  
1. Zainstaluj narzędzia SQL Server Data Tools.  
  
2. Jeśli potrzebujesz przykładową bazę danych SQL można połączyć się z pobrać bazy danych Northwind i Rozpakuj go do nowej lokalizacji.  
  
3. Użyj programu SQL Server Management Studio można dołączyć plik Northwind.mdf rozpakowany do localDB. Po uruchomieniu programu SQL Server Management Studio połącz się z (localdb) \MSSQLLocalDB.  
  
    ![SSMS połączyć z okna dialogowego](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS połączyć z okna dialogowego")  
  
    Kliknij prawym przyciskiem myszy w węźle localdb w okienku po lewej stronie i wybierz polecenie **Dołącz**.  
  
    ![Dołączanie programu SSMS bazy danych](../data-tools/media/raddata-ssms-attach-database.png "raddata dołączyć SSMS w bazie danych")  
  
4. Pobierz przykładowy zestaw SDK Windows ODBC i Rozpakuj go do nowej lokalizacji. Niniejszy przykład pokazuje podstawowe polecenia ODBC, które służą do łączenia z bazą danych i polecenia oraz kwerend problem. Dowiedz się więcej na temat tych funkcji w [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Podczas pierwszego ładowania rozwiązania (jest w folderze C++), programu Visual Studio będzie oferować uaktualniania rozwiązania do bieżącej wersji programu Visual Studio. Kliknij przycisk **Tak**.  
  
5. Aby korzystać z natywnego klienta, należy jej plik nagłówkowy i plik lib. Te pliki zawierają funkcje i definicje specyficzne dla programu SQL Server poza funkcje ODBC, zdefiniowane w sql.h. W **projektu** > **właściwości** > **katalogi VC ++** , Dodaj katalog dołączania następujące czynności:  
  
   **\<dysk systemowy >: \Program Files\Microsoft SQL Server\110\SDK\Include** i ten katalog biblioteki:  
  
   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6. Dodaj następujące wiersze w odbcsql.cpp. #Define zapobiega kompilowanego znaczenia definicji OLE DB.  
  
   ```  
   #define _SQLNCLI_ODBC_  
   #include <sqlncli.h>  
   ```  
  
    Pamiętaj, że próbki nie faktycznie używać dowolną funkcję klienta natywnego, więc poprzednie kroki nie są niezbędne do kompilowania i uruchamiania. Ale projektu jest teraz skonfigurowane do użycia tej funkcji. Aby uzyskać więcej informacji, zobacz [programu SQL Server Native klienta programowania](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).  
  
7. Określ, które sterownik do użycia w podsystemie ODBC. Przykład przekazuje atrybut parametrów połączenia sterownika w jako argument wiersza polecenia. W **projektu** > **właściwości** > **debugowanie**, Dodaj ten argument polecenia:  
  
   ```  
   DRIVER="SQL Server Native Client 11.0"  
   ```  
  
8. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Należy pojawi się okno dialogowe ze sterownika, który wyświetli monit o wprowadzenie bazy danych. Wprowadź `(localdb)\MSSQLLocalDB`i sprawdź **Użyj zaufanego połączenia**. Naciśnij klawisz **OK**. Konsola z komunikatów, które wskazują pomyślnym nawiązaniu połączenia powinny być widoczne. Powinien być też widoczny wiersza polecenia można wpisać w instrukcji SQL. Na poniższym ekranie przedstawiono przykładowe zapytanie i wyniki:  
  
    ![ODBC przykładowych zapytań w danych wyjściowych](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC przykładowych zapytań w danych wyjściowych")  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
