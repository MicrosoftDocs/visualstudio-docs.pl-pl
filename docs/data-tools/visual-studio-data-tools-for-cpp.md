---
title: Narzędzia danych dla języka C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 5157f1d6a851e0784e79dfbfe5b94aef0490a026
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930561"
---
# <a name="visual-studio-data-tools-for-c"></a>Narzędzia Visual Studio data tools dla języka C++

Natywnych języka C++ często może zapewnić największą wydajność, gdy uzyskują dostęp do źródeł danych. Jednak dane narzędzia dla aplikacji w języku C++ w programie Visual Studio nie są tak zaawansowane jak w przypadku aplikacji .NET. Na przykład **źródeł danych** okna nie można ich przeciąganie i upuszczanie źródeł danych na powierzchnię projektu C++. Jeśli potrzebujesz warstwa obiektowo relacyjny, należy napisać własny lub użyj innej firmy. To samo dotyczy funkcji wiązania danych, mimo że aplikacje korzystające z biblioteki MFC można użyć niektórych klas baz danych, wraz z dokumentami i widokami, przechowywanie danych w pamięci i wyświetlania ich do użytkownika. Aby uzyskać więcej informacji, zobacz [dostęp do danych w programie Visual C++](/cpp/data/data-access-in-cpp).

Aby połączyć z bazy danych SQL, natywnych aplikacji w języku C++ można użyć sterowników ODBC i OLE DB i ADO dostawcy, które są dołączone do Windows. Te można nawiązać dowolnej bazy danych, która obsługuje te interfejsy. Sterownik ODBC jest standardowym. OLE DB zapewnia zgodność z poprzednimi wersjami. Aby uzyskać więcej informacji na temat tych technologii danych, zobacz [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Aby korzystać z zalet funkcji niestandardowych w programie SQL Server 2005 i później użyć [klienta macierzystego programu SQL Server](/sql/relational-databases/native-client/sql-server-native-client). Natywny klient zawiera także sterownika SQL Server ODBC i SQL Server dostawcy OLE DB w jednej bibliotece dołączanej dynamicznie (DLL). Obsługuje te aplikacje za pomocą API kodu macierzystego (ODBC, OLE DB i ADO) do programu Microsoft SQL Server. Instaluje program SQL Server Native Client z SQL Server Data Tools. Podręcznik programowania jest tutaj: [Natywny klient programu SQL Server, programowania](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Nawiązywanie połączenia z localDB, ODBC i SQL Native Client w aplikacji w języku C++

1. Zainstaluj narzędzia SQL Server Data Tools.

2. Jeśli potrzebujesz przykładową bazę danych SQL można połączyć się z pobrać bazy danych Northwind i Rozpakuj go do nowej lokalizacji.

3. Użyj programu SQL Server Management Studio, aby dołączyć rozpakowany *Northwind.mdf* pliku do localDB. Po uruchomieniu programu SQL Server Management Studio połącz się z (localdb) \MSSQLLocalDB.

   ![SSMS połączyć z okna dialogowego](../data-tools/media/raddata-ssms-connect-dialog.png)

   Kliknij prawym przyciskiem myszy w węźle localdb w okienku po lewej stronie i wybierz polecenie **Dołącz**.

   ![SSMS dołączyć bazy danych](../data-tools/media/raddata-ssms-attach-database.png)

4. Pobierz przykładowy zestaw SDK Windows ODBC i Rozpakuj go do nowej lokalizacji. Niniejszy przykład pokazuje podstawowe polecenia ODBC, które służą do łączenia z bazą danych i polecenia oraz kwerend problem. Dowiedz się więcej na temat tych funkcji w [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Podczas pierwszego ładowania rozwiązania (jest w folderze C++), programu Visual Studio będzie oferować uaktualniania rozwiązania do bieżącej wersji programu Visual Studio. Kliknij przycisk **Tak**.

5. Aby korzystać z natywnego klienta, należy jej *nagłówka* pliku i *lib* pliku. Te pliki zawierają funkcje i definicje specyficzne dla programu SQL Server poza funkcje ODBC, zdefiniowane w sql.h. W **projektu** > **właściwości** > **katalogi VC ++**, Dodaj katalog dołączania następujące czynności:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   I to katalog biblioteki:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Dodaj następujące wiersze w *odbcsql.cpp*. #Define zapobiega kompilowanego znaczenia definicji OLE DB.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Pamiętaj, że próbki nie faktycznie używać dowolną funkcję klienta natywnego, więc poprzednie kroki nie są niezbędne do kompilowania i uruchamiania. Ale projektu jest teraz skonfigurowane do użycia tej funkcji. Aby uzyskać więcej informacji, zobacz [programowania programu SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).

7. Określ, które sterownik do użycia w podsystemie ODBC. Przykład przekazuje atrybut parametrów połączenia sterownika w jako argument wiersza polecenia. W **projektu** > **właściwości** > **debugowanie**, Dodaj ten argument polecenia:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Należy pojawi się okno dialogowe ze sterownika, który wyświetli monit o wprowadzenie bazy danych. Wprowadź `(localdb)\MSSQLLocalDB`i sprawdź **Użyj zaufanego połączenia**. Naciśnij klawisz **OK**. Konsola z komunikatów, które wskazują pomyślnym nawiązaniu połączenia powinny być widoczne. Powinien być też widoczny wiersza polecenia można wpisać w instrukcji SQL. Na poniższym ekranie przedstawiono przykładowe zapytanie i wyniki:

   ![ODBC przykładowych zapytań w danych wyjściowych](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)