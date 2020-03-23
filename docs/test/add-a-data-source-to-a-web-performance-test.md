---
title: Dodawanie źródła danych do testu wydajności sieci Web
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c7f947be01500b0d45b81d404206722ac71084a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565412"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Dodawanie źródła danych do testu wydajności sieci Web

Powiąż dane, aby zapewnić różne wartości do tego samego testu, na przykład, aby zapewnić różne wartości do parametrów wpisu formularza.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Powiązanie danych z testem wydajności sieci Web](../test/media/web_test_databinding_conceptual.png)

Użyjemy przykładowej aplikacji ASP.NET. Ma trzy strony *.aspx* — domyślną stronę, czerwoną i niebieską. Strona domyślna ma kontrolkę radiową, aby wybrać czerwony lub niebieski i przycisk prześlij. Pozostałe dwie strony *.aspx* są bardzo proste. Jeden ma etykietę o nazwie Red, a drugi ma etykietę o nazwie Blue. Gdy wybierzesz opcję prześlij na stronie domyślnej, wyświetlimy jedną z pozostałych stron. Możesz pobrać próbkę [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) lub po prostu postępować zgodnie z własną aplikacją internetową.

![Uruchamianie aplikacji sieci web do przetestowania](../test/media/web_test_databinding_runwebapp.png)

Rozwiązanie powinno również zawierać test wydajności sieci Web, który przegląda strony aplikacji sieci web.

![Rozwiązanie z testem wydajności sieci Web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Tworzenie bazy danych SQL

::: moniker range="vs-2017"

1. Jeśli nie masz programu Visual Studio Enterprise, możesz go pobrać ze strony [Pliki do pobrania programu Visual Studio.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

2. Tworzenie bazy danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Tworzenie projektu bazy danych.

     ![Tworzenie nowego projektu z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodawanie nowej tabeli do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych w Eksploratorze rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Jeśli nie masz programu Visual Studio Enterprise, możesz go pobrać ze strony [Pliki do pobrania programu Visual Studio.](https://visualstudio.microsoft.com/downloads)

2. Tworzenie bazy danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Tworzenie projektu bazy danych.

     ![Tworzenie nowego projektu z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodawanie nowej tabeli do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych w Eksploratorze rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Dodawanie źródła danych

1. Dodaj źródło danych.

     ![Dodawanie źródła danych do testu wydajności sieci Web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wybierz typ źródła danych i nadaj jego nazwę.

     ![Nadawanie nazwy źródle bazy danych](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Utwórz połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Wprowadź szczegóły połączenia.

     ![Wprowadzanie właściwości połączenia bazy danych SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wybierz tabelę, której chcesz użyć do testu.

     ![Dodawanie tabeli Kolor jako źródła danych](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabela jest powiązana z testem.

     ![Węzeł Źródła danych dodać do testu wydajności sieci Web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Zapisz test.

## <a name="bind-the-data"></a>Powiąż dane

1. Powiąż pole **ColorName.**

     ![Powiązanie pola ColorName z wartością RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otwórz plik *Local.testsettings* w **Eksploratorze rozwiązań** i wybierz opcję **Jeden uruchom na źródło danych.**

     ![Edytowanie pliku ustawień testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Zapisz test wydajności sieci Web.

## <a name="run-the-test-with-the-data"></a>Uruchom test z danymi

1. Uruchom test.

     ![Uruchom test wydajności sieci Web w celu weryfikacji powiązania](../test/media/web_test_databinding_sql_runtest.png)

     Dwa przebiegi są wyświetlane dla każdego wiersza danych. Uruchom 1 wysyła żądanie dla strony *Red.aspx,* a Uruchom 2 wysyła żądanie dla strony *Blue.aspx*.

     ![Wyniki testu](../test/media/web_test_databinding_sql_runresults.png)

     Po związaniu ze źródłem danych można naruszyć domyślną regułę adresu URL odpowiedzi. W takim przypadku błąd w uruchom 2 jest spowodowany przez regułę, która oczekuje *Red.aspx* strony z oryginalnego nagrywania testu, ale powiązanie danych teraz kieruje go do *Blue.aspx* strony.

2. Popraw błąd sprawdzania poprawności, usuwając regułę sprawdzania poprawności **adresu URL odpowiedzi** i ponownie uruchamiając test.

     ![Usuwanie reguły sprawdzania poprawności adresu URL odpowiedzi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test wydajności sieci web teraz przechodzi przy użyciu powiązania danych.

     ![Przebiegi testu przy użyciu powiązania danych](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Pyt.: Jakich baz danych można używać jako źródła danych?

**Odp.:** Można użyć następujących elementów:

- Microsoft SQL Azure.

- Dowolna wersja programu Microsoft SQL Server 2005 lub nowsza.

- Plik bazy danych programu Microsoft SQL Server (w tym program SQL Express).

- Microsoft ODBC.

- Plik programu Microsoft Access przy użyciu dostawcy programu .NET Framework dla ole db.

- Oracle 7.3, 8i, 9i lub 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Pyt.: Jak używać pliku tekstowego csv (łączu) jako źródła danych?

**Odp.:** Oto jak to zrobić:

1. Utwórz folder do organizowania artefaktów bazy danych projektów i dodawania elementu.

     ![Dodawanie nowego elementu do folderu Dane](../test/media/web_test_databinding_foldernewitem.png)

2. Tworzenie pliku tekstowego.

     ![Nadawanie nazwy nowemu plikowi tekstowemu ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edytuj plik tekstowy i dodaj następujące elementy:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Użyj kroków w [polu Dodaj źródło danych](#add-the-data-source), ale wybierz plik CSV jako źródło danych.

     ![Wprowadzanie nazwy i wybieranie pliku CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>P: Co zrobić, jeśli mój istniejący plik CSV nie zawiera nagłówków kolumn?

**Odp.:** Jeśli nie można dodać nagłówków kolumn, możesz użyć pliku opisu schematu, aby traktować plik CSV jako bazę danych.

1. Dodaj nowy plik tekstowy o nazwie *schema.ini*.

     ![Dodawanie pliku schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Edytuj plik *schema.ini,* aby dodać informacje opisujące strukturę danych. Na przykład plik schematu opisujący plik CSV może wyglądać następująco:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Dodaj źródło danych do testu.

     ![Dodawanie źródła danych do testu wydajności sieci Web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Jeśli używasz pliku *schema.ini,* wybierz **bazę danych** (nie plik CSV) jako źródło danych i nazwij go.

     ![Dodawanie źródła danych bazy danych](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Utwórz nowe połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wybierz dostawcę danych programu .NET Framework dla ole db.

     ![Wybierz dostawcę danych OLE DB programu .NET framework](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wybierz **pozycję Zaawansowane**.

     ![Wybierz pozycję Zaawansowane](../test/media/web_test_databinding_advanced.png)

8. Dla dostawcy właściwości, wybierz Microsoft.Jet.OLEDB.4.0, a następnie ustaw **rozszerzone właściwości** na tekst; HDR=NIE.

     ![Stosowanie właściwości zaawansowanych](../test/media/web_test_databinding_advancedproperties.png)

9. Wpisz nazwę folderu zawierającego plik schematu i przetestuj połączenie.

     ![Wprowadzanie ścieżki do folderu danych](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wybierz plik CSV, którego chcesz użyć.

     ![Zaznaczanie pliku tekstowego](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po zakończeniu plik CSV pojawi się jako tabela.

     ![Źródło danych dodane do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Pyt.: Jak używać pliku XML jako źródła danych?

**Odpowiedź:** tak.

1. Utwórz folder do organizowania artefaktów bazy danych projektów i dodawania elementu.

     ![Dodawanie nowego elementu do folderu Dane](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik XML.

     ![Dodawanie pliku ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Edytuj plik XML i dodaj dane:

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

4. Użyj kroków w [polu Dodaj źródło danych](#add-the-data-source), ale wybierz plik XML jako źródło danych.

     ![Wprowadzanie nazwy i wybieranie pliku XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Pyt.: Czy można dodać powiązanie danych do żądania usługi sieci web, która używa protokołu SOAP?

**Odp.:** Tak, należy ręcznie zmienić kod XML protokołu SOAP.

1. Wybierz żądanie usługi sieci web w drzewie żądań i w oknie Właściwości wybierz wielokropek (...) we właściwości Treść ciągu.

     ![Edytowanie treści ciągu usługi sieci Web](../test/media/web_test_databinding_webservicerequest.png)

2. Zamień wartości w treści SOAP na wartości związane z danymi, używając następującej składni:

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

    Można go zmienić na ten sposób:

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
