---
title: Narzędzia danych dlaC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 2be19729b61831e6f15ff40b6b4e1d7b4b0bb541
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586058"
---
# <a name="visual-studio-data-tools-for-c"></a>Narzędzia do obsługi danych programu Visual Studio dla języka C++

Natywny C++ może często zapewnić największą wydajność podczas uzyskiwania dostępu do źródeł danych. Jednak narzędzia danych dla C++ aplikacji w programie Visual Studio nie są tak rozbudowane, jak w przypadku aplikacji .NET. Na przykład okno **źródła danych** nie może służyć do przeciągania i upuszczania źródeł danych na powierzchni C++ projektowej. Jeśli potrzebujesz warstwy relacyjnej obiektu, musisz napisać własny lub użyć produktu innej firmy. Ta sama wartość dotyczy funkcji powiązania danych, chociaż aplikacje korzystające z biblioteki klas Microsoft Foundation mogą używać niektórych klas baz danych wraz z dokumentami i widokami w celu przechowywania danych w pamięci i wyświetlania ich użytkownikowi. Aby uzyskać więcej informacji, zobacz [dostęp do danych C++w programie Visual ](/cpp/data/data-access-in-cpp).

Aby nawiązać połączenie z bazami C++ danych SQL, natywne aplikacje mogą korzystać ze sterowników ODBC i OLE DB oraz dostawcy ADO dołączonego do systemu Windows. Mogą one łączyć się z dowolnymi bazami danych, które obsługują te interfejsy. Sterownik ODBC jest standardem. OLE DB zapewnia zgodność z poprzednimi wersjami. Aby uzyskać więcej informacji na temat tych technologii danych, zobacz [składniki dostępu do danych systemu Windows](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Aby skorzystać z funkcji niestandardowych w SQL Server 2005 i nowszych, użyj [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Natywny klient zawiera również SQL Server sterownika ODBC i SQL Server dostawcę OLE DB w jednej natywnej bibliotece dołączanej dynamicznie (DLL). Te aplikacje obsługują używanie interfejsów API kodu natywnego (ODBC, OLE DB i ADO) do Microsoft SQL Server. SQL Server Native Client instalowany za pomocą narzędzi SQL Server Data Tools. Przewodnik programowania jest tutaj: [SQL Server natywne programowanie klientów](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Aby nawiązać połączenie z usługą localDB za pośrednictwem C++ ODBC i SQL Native Client z aplikacji

1. Zainstaluj narzędzia SQL Server Data Tools.

2. Jeśli potrzebujesz przykładowej bazy danych SQL, z którą chcesz nawiązać połączenie, Pobierz bazę danych Northwind i rozpakuj ją do nowej lokalizacji.

3. Użyj SQL Server Management Studio, aby dołączyć niespakowany plik *Northwind. mdf* do localDB. Po rozpoczęciu SQL Server Management Studio Połącz się z (LocalDB) \MSSQLLocalDB.

   ![Okno dialogowe programu SSMS Connect](../data-tools/media/raddata-ssms-connect-dialog.png)

   Następnie kliknij prawym przyciskiem myszy węzeł LocalDB w lewym okienku, a następnie wybierz pozycję **Dołącz**.

   ![Dołącz bazę danych programu SSMS](../data-tools/media/raddata-ssms-attach-database.png)

4. Pobierz przykład ODBC Windows SDK i rozpakuj go do nowej lokalizacji. Ten przykład pokazuje podstawowe polecenia ODBC, które są używane do łączenia się z bazą danych i wysyłania zapytań i poleceń. Więcej informacji na temat tych funkcji można znaleźć w [witrynie Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Po pierwszym załadowaniu rozwiązania (znajdującego się w C++ folderze) program Visual Studio będzie oferować uaktualnienie rozwiązania do bieżącej wersji programu Visual Studio. Kliknij przycisk **Tak**.

5. Aby można było korzystać z klienta natywnego, potrzebny jest plik *nagłówkowy* i plik *lib* . Te pliki zawierają funkcje i definicje charakterystyczne dla SQL Server, poza funkcjami ODBC zdefiniowanymi w pliku SQL. h. We **właściwościach** > **projektu** > **katalogów VC + +** Dodaj następujący katalog dołączania:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   I ten katalog biblioteki:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Dodaj te wiersze w *ODBCSQL. cpp*. #Define zapobiega kompilowaniu nieistotnych OLE DB definicji.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Należy zauważyć, że w przykładzie nie jest faktycznie używana żadna z natywnych funkcji klienta, dlatego poprzednie kroki nie są niezbędne do skompilowania i uruchomienia. Ale projekt jest teraz skonfigurowany do korzystania z tej funkcji. Aby uzyskać więcej informacji, zobacz [programowanie SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).

7. Określ, który sterownik ma być używany w podsystemie ODBC. Przykład przekazuje atrybut parametrów połączenia sterownika w jako argument wiersza polecenia. W oknie **właściwości** > **projektu** > **debugowanie**Dodaj następujący argument polecenia:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Powinno zostać wyświetlone okno dialogowe ze sterownika, które wyświetla komunikat z prośbą o wprowadzenie bazy danych. Wprowadź `(localdb)\MSSQLLocalDB`i zaznacz pole wyboru **Użyj zaufanego połączenia**. Naciśnij klawisz **OK**. Powinna zostać wyświetlona konsola z komunikatami informującymi o pomyślnym nawiązaniu połączenia. Należy również wyświetlić wiersz polecenia, w którym można wpisać instrukcję języka SQL. Na poniższym ekranie przedstawiono przykładowe zapytanie i wyniki:

   ![Przykładowe dane wyjściowe zapytania ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
