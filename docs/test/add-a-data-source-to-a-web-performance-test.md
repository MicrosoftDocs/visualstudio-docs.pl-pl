---
title: Dodawanie źródła danych do testu wydajności sieci Web
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94ad53e4ac3d65bfe6cf08bf03f1f79c2075e03d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289069"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Dodawanie źródła danych do testu wydajności sieci Web

Powiąż dane, aby podać różne wartości na tym samym teście, na przykład, aby podać różne wartości parametrów post formularza.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Powiązywanie danych z testem wydajności sieci Web](../test/media/web_test_databinding_conceptual.png)

Będziemy używać przykładowej aplikacji ASP.NET. Ma trzy strony *. aspx* — domyślną stronę, czerwoną stronę i niebieską stronę. Strona domyślna zawiera formant radiowy, aby wybrać czerwony lub niebieski i przycisk Prześlij. Pozostałe dwie strony *. aspx* są bardzo proste. Jedna ma etykietę o nazwie czerwona, a druga ma etykietę o nazwie niebieska. Po wybraniu opcji Prześlij na stronie domyślnej zostanie wyświetlona jedna z innych stron. Możesz pobrać przykład [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) lub po prostu wykonać własną aplikację internetową.

![Uruchamianie aplikacji sieci Web w celu przetestowania](../test/media/web_test_databinding_runwebapp.png)

Rozwiązanie powinno również obejmować test wydajności sieci Web, który przegląda strony aplikacji sieci Web.

![Rozwiązanie z testem wydajności sieci Web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Tworzenie bazy danych SQL

::: moniker range="vs-2017"

1. Jeśli nie masz Visual Studio Enterprise, możesz pobrać go ze strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) .

2. Tworzenie bazy danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Utwórz nowy projekt z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodaj nową tabelę do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych z Eksplorator rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Jeśli nie masz Visual Studio Enterprise, możesz pobrać go ze strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) .

2. Tworzenie bazy danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Utwórz nowy projekt z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodaj nową tabelę do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych z Eksplorator rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Dodawanie źródła danych

1. Dodaj źródło danych.

     ![Dodaj źródło danych do testu wydajności sieci Web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wybierz typ źródła danych i nadaj mu nazwę.

     ![Nadaj nazwę źródłu bazy danych](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Utwórz połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Wprowadź szczegóły połączenia.

     ![Wprowadź właściwości połączenia z usługą SQL Database](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wybierz tabelę, której chcesz użyć dla testu.

     ![Dodawanie tabeli kolorów jako źródła danych](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabela jest powiązana z testem.

     ![Węzeł źródeł danych Dodaj do testu wydajności sieci Web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Zapisz test.

## <a name="bind-the-data"></a>Powiąż dane

1. Powiąż pole **ColorName** .

     ![Powiąż pole ColorName z wartością RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otwórz plik *Local. testsettings* w **Eksplorator rozwiązań** i wybierz opcję **jeden przebieg na wiersz źródła danych** .

     ![Edytuj plik ustawień testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Zapisz test wydajności sieci Web.

## <a name="run-the-test-with-the-data"></a>Uruchom test z danymi

1. Uruchom test.

     ![Uruchom test wydajności sieci Web, aby zweryfikować powiązanie](../test/media/web_test_databinding_sql_runtest.png)

     Dwa uruchomienia są wyświetlane dla każdego wiersza danych. Uruchomienie 1 powoduje wysłanie żądania dla strony *Red. aspx*i uruchomienia 2 wysyła żądanie dla strony *Blue. aspx*.

     ![Wyniki przebiegu testu](../test/media/web_test_databinding_sql_runresults.png)

     Po utworzeniu powiązania ze źródłem danych można naruszyć domyślną regułę adresu URL odpowiedzi. W takim przypadku błąd w przebiegu 2 jest spowodowany przez regułę, która oczekuje strony *Red. aspx* od oryginalnego nagrania testu, ale powiązanie danych teraz kieruje go do strony *Blue. aspx* .

2. Usuń błąd sprawdzania poprawności, usuwając regułę walidacji **adresu URL odpowiedzi** i ponownie uruchamiając test.

     ![Usuń regułę walidacji adresu URL odpowiedzi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test wydajności sieci Web przebiega teraz przy użyciu powiązania danych.

     ![Testy z użyciem powiązania danych](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>P: jakich baz danych można używać jako źródła danych?

Odp **.:** Można użyć następujących:

- Microsoft SQL Azure.

- Dowolna wersja Microsoft SQL Server 2005 lub nowsza.

- Plik bazy danych Microsoft SQL Server (w tym SQL Express).

- Microsoft ODBC.

- Plik programu Microsoft Access z dostawcą .NET Framework dla OLE DB.

- Oracle 7,3, 8i, 9i lub 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>P: Jak mogę użyć pliku tekstowego z wartościami rozdzielanymi przecinkami (CSV) jako źródła danych?

Odp **.:** Oto jak to zrobić:

1. Utwórz folder w celu zorganizowania artefaktów bazy danych projektów i dodania elementu.

     ![Dodaj nowy element do folderu danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik tekstowy.

     ![Nazwij nowy plik tekstowy ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edytuj plik tekstowy i Dodaj następujące elementy:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Wykonaj kroki opisane w sekcji [Dodawanie źródła danych](#add-the-data-source), ale wybierz plik CSV jako źródło danych.

     ![Wprowadź nazwę i wybierz plik CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>P: co zrobić, jeśli mój istniejący plik CSV nie zawiera nagłówków kolumn?

Odp **.:** Jeśli nie możesz dodać nagłówków kolumn, możesz użyć pliku opisu schematu, aby traktować plik CSV jako bazę danych.

1. Dodaj nowy plik tekstowy o nazwie *schema.ini*.

     ![Dodawanie pliku schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Edytuj plik *schema.ini* , aby dodać informacje opisujące strukturę danych. Na przykład plik schematu opisujący plik CSV może wyglądać następująco:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Dodaj źródło danych do testu.

     ![Dodaj źródło danych do testu wydajności sieci Web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Jeśli używasz pliku *schema.ini* , wybierz pozycję **baza danych** (nie plik CSV) jako źródło danych i nadaj jej nazwę.

     ![Dodaj źródło danych bazy danych](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Utwórz nowe połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wybierz Dostawca danych .NET Framework OLE DB.

     ![Wybierz dostawcę danych programu .NET Framework OLE DB](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wybierz pozycję **Zaawansowane**.

     ![Wybieranie zaawansowane](../test/media/web_test_databinding_advanced.png)

8. Dla właściwości dostawca wybierz pozycję Microsoft. Jet. OLEDB. 4.0, a następnie ustaw **właściwości rozszerzone** na tekst. HDR = NO.

     ![Zastosuj zaawansowane właściwości](../test/media/web_test_databinding_advancedproperties.png)

9. Wpisz nazwę folderu, który zawiera plik schematu i przetestuj połączenie.

     ![Wprowadź ścieżkę do folderu danych](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wybierz plik CSV, którego chcesz użyć.

     ![Wybierz plik tekstowy](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po zakończeniu plik CSV zostanie wyświetlony jako tabela.

     ![Źródło danych dodane do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>P: Jak mogę używać pliku XML jako źródła danych?

**Odpowiedź:** tak.

1. Utwórz folder w celu zorganizowania artefaktów bazy danych projektów i dodania elementu.

     ![Dodaj nowy element do folderu danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik XML.

     ![Dodaj plik ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Edytuj plik XML i Dodaj dane:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Wykonaj kroki opisane w sekcji [Dodawanie źródła danych](#add-the-data-source), ale wybierz plik XML jako źródło danych.

     ![Wprowadź nazwę i wybierz plik XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>P: Czy można dodać powiązanie danych do żądania usługi sieci Web, które używa protokołu SOAP?

Odp **.:** Tak, musisz ręcznie zmienić kod XML protokołu SOAP.

1. Wybierz żądanie usługi sieci Web w drzewie żądań i w okno Właściwości wybierz wielokropek (...) we właściwości treść ciągu.

     ![Edytuj treść ciągu usługi sieci Web](../test/media/web_test_databinding_webservicerequest.png)

2. Zastąp wartości w treści protokołu SOAP wartościami związanymi z danymi przy użyciu następującej składni:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Na przykład, jeśli masz następujący kod:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Można to zmienić w następujący sposób:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Zapisz test.
