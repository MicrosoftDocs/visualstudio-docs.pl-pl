---
title: Dodawanie źródła danych do testu wydajności sieci Web
description: Dowiedz się, jak powiązać dane w celu podania różnych wartości do tego samego testu, na przykład w celu podania różnych wartości parametrom wpisów w formularzu.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761007"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Dodawanie źródła danych do testu wydajności sieci Web

Powiąż dane, aby podać różne wartości do tego samego testu, na przykład w celu podania różnych wartości parametrom post formularza.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Wiązanie danych z internetowym testem wydajnościowym](../test/media/web_test_databinding_conceptual.png)

Użyjemy przykładowej aplikacji ASP.NET aplikacji. Ma trzy *strony aspx* — stronę domyślną, czerwoną i niebieską. Strona domyślna ma kontrolkę przycisku radiowego do wybrania czerwonego lub niebieskiego i przycisku przesyłania. Pozostałe dwie strony *aspx* są bardzo proste. Jeden ma etykietę o nazwie Red (Czerwony), a drugi ma etykietę o nazwie Blue (Niebieski). Po wybraniu opcji Prześlij na stronie domyślnej zostanie wyświetlana jedna z pozostałych stron. Możesz pobrać [przykładową aplikację ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) lub po prostu postępować zgodnie z samodzielnie swoją aplikacją internetową.

![Uruchamianie aplikacji internetowej do przetestowania](../test/media/web_test_databinding_runwebapp.png)

Rozwiązanie powinno również zawierać internetowy test wydajnościowy, który przegląda strony aplikacji internetowej.

![Rozwiązanie z internetowym testem wydajnościowym](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Tworzenie bazy danych SQL

::: moniker range="vs-2017"

1. Jeśli nie masz jeszcze konta Visual Studio Enterprise, możesz go pobrać ze strony [Visual Studio pobierania.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

2. Utwórz bazę danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Tworzenie nowego projektu z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodawanie nowej tabeli do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych z Eksplorator rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Jeśli nie masz jeszcze konta Visual Studio Enterprise, możesz go pobrać ze strony [Visual Studio pobierania.](https://visualstudio.microsoft.com/downloads)

2. Utwórz bazę danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Tworzenie nowego projektu z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodawanie nowej tabeli do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Publikowanie projektu bazy danych z Eksplorator rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodaj dane do pól.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Dodawanie źródła danych

1. Dodaj źródło danych.

     ![Dodawanie źródła danych do internetowego testu wydajnościowego](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wybierz typ źródła danych i nadaj jego nazwę.

     ![Nazywanie źródła bazy danych](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Utwórz połączenie.

     ![Wybieranie nowego połączenia](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Wprowadź szczegóły połączenia.

     ![Wprowadzanie właściwości połączenia z bazą danych SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wybierz tabelę, której chcesz użyć do testu.

     ![Dodawanie tabeli Color jako źródła danych](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabela jest powiązana z testem.

     ![Dodawanie węzła Źródła danych do internetowego testu wydajnościowego](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Zapisz test.

## <a name="bind-the-data"></a>Wiązanie danych

1. Powiąż **pole ColorName.**

     ![Wiązanie pola ColorName z wartością RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otwórz plik *Local.testsettings* w Eksplorator rozwiązań **i** wybierz opcję **Jeden przebieg na wiersz źródła** danych.

     ![Edytowanie pliku ustawień testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Zapisz internetowy test wydajnościowy.

## <a name="run-the-test-with-the-data"></a>Uruchamianie testu z danymi

1. Uruchom test.

     ![Uruchamianie internetowego testu wydajnościowego w celu zweryfikowania powiązania](../test/media/web_test_databinding_sql_runtest.png)

     Dwa przebiegi są wyświetlane dla każdego wiersza danych. Przebieg 1 wysyła żądanie dla strony *Red.aspx,* a przebieg 2 wysyła żądanie dla *strony Blue.aspx.*

     ![Wyniki uruchomienia testu](../test/media/web_test_databinding_sql_runresults.png)

     Powiązanie ze źródłem danych może naruszać domyślną regułę adresu URL odpowiedzi. W takim przypadku błąd w uruchomieniu 2 jest spowodowany przez regułę, która oczekuje strony *Red.aspx* od oryginalnego nagrania testu, ale powiązanie danych kieruje teraz do *strony Blue.aspx.*

2. Popraw błąd walidacji, usuwając **regułę weryfikacji adresu URL** odpowiedzi i ponownie uruchamiając test.

     ![Usuwanie reguły weryfikacji adresu URL odpowiedzi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Internetowy test wydajnościowy przechodzi teraz przy użyciu powiązania danych.

     ![Testy przebiegły pomyślnie przy użyciu powiązania danych](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Pytanie: jakich baz danych można używać jako źródła danych?

**A:** Możesz użyć następujących funkcji:

- Microsoft SQL Azure.

- Dowolna wersja Microsoft SQL Server 2005 lub nowsza.

- Microsoft SQL Server bazy danych (w tym SQL Express).

- Microsoft ODBC.

- Plik programu Microsoft Access przy użyciu .NET Framework dostawcy OLE DB.

- Oracle 7.3, 8i, 9i lub 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Pytanie: Jak mogę używać pliku tekstowego wartości rozdzielanych przecinkami (CSV) jako źródła danych?

**A:** Oto jak to zrobić:

1. Utwórz folder, aby zorganizować artefakty bazy danych projektów i dodać element.

     ![Dodawanie nowego elementu do folderu Danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik tekstowy.

     ![Nazwij nowy plik tekstowy ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edytuj plik tekstowy i dodaj następujący kod:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Skorzystaj z procedury [Dodawanie źródła danych,](#add-the-data-source)ale wybierz plik CSV jako źródło danych.

     ![Wprowadź nazwę i wybierz plik CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Pytanie: Co zrobić, jeśli istniejący plik CSV nie zawiera nagłówków kolumn?

**A:** Jeśli nie możesz dodać nagłówków kolumn, możesz użyć pliku opisu schematu, aby traktować plik CSV jako bazę danych.

1. Dodaj nowy plik tekstowy o *nazwieschema.ini*.

     ![Dodawanie schema.ini plików](../test/media/web_test_databinding_schemafile.png)

2. Edytuj *plikschema.ini,* aby dodać informacje opisujące strukturę danych. Na przykład plik schematu opisujący plik CSV może wyglądać tak:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Dodaj źródło danych do testu.

     ![Dodawanie źródła danych do internetowego testu wydajnościowego](../test/media/web_test_databinding_sql_adddatasource.png)

4. Jeśli używasz pliku *schema.ini,* wybierz bazę danych **(nie** plik CSV) jako źródło danych i nadaj jej nazwę.

     ![Dodawanie źródła danych bazy danych](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Utwórz nowe połączenie.

     ![Wybieranie nowego połączenia](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wybierz .NET Framework Dostawca danych dla OLE DB.

     ![Wybieranie dostawcy danych OLE DB .NET Framework](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wybierz **pozycję Zaawansowane.**

     ![Wybierz pozycję Zaawansowane](../test/media/web_test_databinding_advanced.png)

8. W polu Właściwości dostawcy wybierz pozycję Microsoft.Jet.OLEDB.4.0, a następnie ustaw **pozycję Właściwości rozszerzone** na wartość Tekst. SCAL= NIE.

     ![Stosowanie właściwości zaawansowanych](../test/media/web_test_databinding_advancedproperties.png)

9. Wpisz nazwę folderu zawierającego plik schematu i przetestuj połączenie.

     ![Wprowadź ścieżkę do folderu danych](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wybierz plik CSV, którego chcesz użyć.

     ![Wybieranie pliku tekstowego](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po zakończeniu plik CSV zostanie wyświetlony jako tabela.

     ![Źródło danych dodane do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Pytanie: Jak mogę używać pliku XML jako źródła danych?

**Odpowiedź:** tak.

1. Utwórz folder, aby zorganizować artefakty bazy danych projektów i dodać element.

     ![Dodawanie nowego elementu do folderu Danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik XML.

     ![Dodawanie ColorData.xml plików](../test/media/web_test_databinding_additemxmlfile.png)

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

4. Skorzystaj z procedury [Dodawanie źródła danych,](#add-the-data-source)ale wybierz plik XML jako źródło danych.

     ![Wprowadź nazwę i wybierz pozycję Plik XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Pytanie: Czy mogę dodać powiązanie danych do żądania usługi internetowej, które korzysta z protokołu SOAP?

**A:** Tak, należy ręcznie zmienić xml protokołu SOAP.

1. Wybierz żądanie usługi internetowej w drzewie żądań, a następnie w okno Właściwości wybierz wielokropek (...) we właściwości Treść ciągu.

     ![Edytowanie treści ciągu usługi internetowej](../test/media/web_test_databinding_webservicerequest.png)

2. Zastąp wartości w treści protokołu SOAP wartościami powiązanymi z danymi przy użyciu następującej składni:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Jeśli na przykład masz następujący kod:

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

    Możesz go zmienić na ten:

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
