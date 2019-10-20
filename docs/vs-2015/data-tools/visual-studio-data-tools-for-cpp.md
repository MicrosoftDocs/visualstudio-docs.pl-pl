---
title: Visual Studio Data Tools dla C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621210"
---
# <a name="visual-studio-data-tools-for-c"></a>Narzędzia do obsługi danych programu Visual Studio dla języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Natywny C++ może często zapewnić największą wydajność podczas uzyskiwania dostępu do źródeł danych. Jednak narzędzia danych dla C++ aplikacji w programie Visual Studio nie są tak rozbudowane, jak w przypadku aplikacji .NET. Na przykład źródła danych nie mogą być używane do przeciągania i upuszczania źródeł danych na powierzchni C++ projektowej. Jeśli potrzebujesz warstwy relacyjnej obiektu, musisz napisać własny lub użyć produktu innej firmy.  Ta sama wartość dotyczy funkcji powiązania danych, chociaż aplikacje korzystające z biblioteki klas Microsoft Foundation mogą używać niektórych klas baz danych wraz z dokumentami i widokami w celu przechowywania danych w pamięci i wyświetlania ich użytkownikowi. Aby uzyskać więcej informacji, zobacz [dostęp do danych C++ w programie Visual](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Aby nawiązać połączenie z bazami C++ danych SQL, natywne aplikacje mogą korzystać ze sterowników ODBC i OLE DB oraz dostawcy ADO dołączonego do systemu Windows.     Mogą one łączyć się z dowolnymi bazami danych, które obsługują te interfejsy. Sterownik ODBC jest standardem. OLE DB zapewnia zgodność z poprzednimi wersjami. Aby uzyskać więcej informacji na temat tych technologii danych, zobacz [składniki dostępu do danych systemu Windows](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)

 Aby skorzystać z funkcji niestandardowych w SQL Server 2005 i nowszych, użyj [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Natywny klient zawiera również SQL Server sterownika ODBC i SQL Server dostawcę OLE DB w jednej natywnej bibliotece dołączanej dynamicznie (DLL). Te aplikacje obsługują używanie interfejsów API kodu natywnego (ODBC, OLE DB i ADO) do Microsoft SQL Server.  SQL Server Native Client instalowany za pomocą narzędzi SQL Server Data Tools. Przewodnik programowania to tutaj: [programowanie SQL Server Native Client](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Aby nawiązać połączenie z usługą localDB za pośrednictwem C++ ODBC i SQL Native Client z aplikacji

1. Zainstaluj narzędzia SQL Server Data Tools.

2. Jeśli potrzebujesz przykładowej bazy danych SQL, z którą chcesz nawiązać połączenie, Pobierz bazę danych Northwind i rozpakuj ją do nowej lokalizacji.

3. Użyj SQL Server Management Studio, aby dołączyć niespakowany plik Northwind. mdf do localDB. Po rozpoczęciu SQL Server Management Studio Połącz się z (LocalDB) \MSSQLLocalDB.

    ![Okno dialogowe programu SSMS Connect](../data-tools/media/raddata-ssms-connect-dialog.png "okno dialogowe programu raddata SSMS Connect")

    Następnie kliknij prawym przyciskiem myszy węzeł LocalDB w lewym okienku, a następnie wybierz pozycję **Dołącz**.

    ![Dołącz bazę danych programu SSMS](../data-tools/media/raddata-ssms-attach-database.png "raddata — Dołącz bazę danych programu SSMS")

4. Pobierz przykład ODBC Windows SDK i rozpakuj go do nowej lokalizacji. Ten przykład pokazuje podstawowe polecenia ODBC, które są używane do łączenia się z bazą danych i wysyłania zapytań i poleceń. Więcej informacji na temat tych funkcji można znaleźć w [witrynie Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Po pierwszym załadowaniu rozwiązania (znajdującego się w C++ folderze) program Visual Studio będzie oferować uaktualnienie rozwiązania do bieżącej wersji programu Visual Studio. Kliknij przycisk **Tak**.

5. Aby można było korzystać z klienta natywnego, potrzebny jest plik nagłówkowy i plik lib. Te pliki zawierają funkcje i definicje charakterystyczne dla SQL Server, poza funkcjami ODBC zdefiniowanymi w pliku SQL. h. We**właściwościach**  >  **projektu**  > **katalogów VC + +** Dodaj następujący katalog dołączania:

   **\<system dysku >: \Program Files\Microsoft SQL Server\110\SDK\Include**     I ten katalog biblioteki:

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. Dodaj te wiersze w ODBCSQL. cpp. #Define zapobiega kompilowaniu nieistotnych OLE DB definicji.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Należy zauważyć, że w przykładzie nie jest faktycznie używana żadna z natywnych funkcji klienta, dlatego poprzednie kroki nie są niezbędne do skompilowania i uruchomienia. Ale projekt jest teraz skonfigurowany do korzystania z tej funkcji. Aby uzyskać więcej informacji, zobacz [programowanie SQL Server Native Client](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Określ, który sterownik ma być używany w podsystemie ODBC. Przykład przekazuje atrybut parametrów połączenia sterownika w jako argument wiersza polecenia. W oknie**właściwości**  >  **projektu**  > **debugowanie**Dodaj następujący argument polecenia:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Powinno zostać wyświetlone okno dialogowe ze sterownika, które wyświetla komunikat z prośbą o wprowadzenie bazy danych. Wprowadź `(localdb)\MSSQLLocalDB` i zaznacz pole wyboru **Użyj zaufanego połączenia**. Naciśnij przycisk **OK**. Powinna zostać wyświetlona konsola z komunikatami informującymi o pomyślnym nawiązaniu połączenia. Należy również wyświetlić wiersz polecenia, w którym można wpisać instrukcję języka SQL. Na poniższym ekranie przedstawiono przykładowe zapytanie i wyniki:

    ![Przykładowe dane wyjściowe zapytania ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "Przykładowe dane wyjściowe zapytania ODBC raddata")

## <a name="see-also"></a>Zobacz też
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
