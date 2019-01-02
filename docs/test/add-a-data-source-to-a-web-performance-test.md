---
title: Dodawanie źródła danych do testu wydajności sieci Web
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 52a6289d6b17528d31d66e26df2f15b85749aac3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823545"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Dodawanie źródła danych do testu wydajności sieci Web

Wiązanie danych, aby zapewnić różne wartości w ten sam test, na przykład, aby zapewnić różne wartości do formularza Parametry księgowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Wiązanie danych do testu wydajności sieci web](../test/media/web_test_databinding_conceptual.png)

Zamierzamy korzystanie z przykładowej aplikacji platformy ASP.NET. Posiada trzy *.aspx* strony — domyślną stronę, stronę czerwoną i niebieską stronę. Domyślna strona zawiera formant radiowy, do wyboru czerwony lub niebieski i przycisk Prześlij. Pozostałe dwa *.aspx* strony są bardzo proste. Jedna ma etykietę o nazwie czerwona, a druga ma etykietę o nazwie niebieska. Po wybraniu Prześlij na stronie domyślnej wyświetlamy jedną z innych stron. Możesz pobrać [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) przykładowy lub po prostu wykonaj własną aplikację sieci web.

![Uruchamianie aplikacji sieci web do zbadania](../test/media/web_test_databinding_runwebapp.png)

Twoje rozwiązanie powinien również zawierać test wydajności sieci web, który przegląda strony aplikacji sieci web.

![Rozwiązanie za pomocą testu wydajności sieci web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Tworzenie bazy danych SQL

1. Jeśli nie masz programu Visual Studio Enterprise, możesz pobrać go z [pobieranie Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony.

2. Utwórz bazę danych SQL.

     ![Dodawanie nowej bazy danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Utwórz nowy projekt z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodaj tabelę do projektu bazy danych.

     ![Dodaj nową tabelę do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodaj pola do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Opublikuj projekt bazy danych.

     ![Opublikuj projekt bazy danych za pomocą Eksploratora rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodawanie danych do pola.

     ![Dodawanie danych do pola](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

## <a name="add-the-data-source"></a>Dodawanie źródła danych

1. Dodawanie źródła danych.

     ![Dodawanie źródła danych do testu wydajności sieci web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wybierz typ źródła danych i nadaj mu nazwę.

     ![Nazwa źródłowej bazy danych](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Utwórz połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Wprowadź szczegóły połączenia.

     ![Wprowadź właściwości połączenia bazy danych SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wybierz tabelę, która ma być używana podczas testu.

     ![Dodawanie tabeli kolorów jako źródło danych](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tabela jest powiązana z testem.

     ![Węzeł źródła danych, Dodaj do testu wydajności sieci web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Zapisz test.

## <a name="bind-the-data"></a>Powiązania danych

1. Powiąż **ColorName** pola.

     ![Powiązania pola ColorName RadioButtonList1 wartości](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otwórz *Local.testsettings* w pliku **Eksploratora rozwiązań** i wybierz **jedno uruchomienie na wiersz źródła danych** opcji.

     ![Edytowanie pliku ustawień testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Zapisz test wydajności sieci web.

## <a name="run-the-test-with-the-data"></a>Uruchom test przy użyciu danych

1. Uruchom test.

     ![Uruchom test wydajności sieci web, aby sprawdzić powiązania](../test/media/web_test_databinding_sql_runtest.png)

     Dwa przebiegi są wyświetlane dla każdego wiersza danych. Uruchom 1 wysyła żądanie dla strony *Red.aspx*, uruchom 2 wysyła żądanie dla strony *Blue.aspx*.

     ![Wyniki przebiegu testu](../test/media/web_test_databinding_sql_runresults.png)

     Wiążąc się ze źródłem danych, możesz naruszyć regułę URL odpowiedzi domyślnej. W tym przypadku błąd w przebiegu 2 jest spowodowany przez regułę, która oczekuje *Red.aspx* strony z oryginalnego nagrania testu, ale teraz powiązanie danych kieruje go do *Blue.aspx* strony.

2. Popraw błąd sprawdzania poprawności, usuwając **adres URL odpowiedzi** reguła sprawdzania poprawności i ponownie uruchamiając test.

     ![Usuń regułę walidacji adresu URL odpowiedzi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test wydajności sieci web kończy się powodzeniem używanie powiązania danych.

     ![Test zakończy się pomyślnie używanie powiązania danych](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>PYT.: Jakie baz danych można używać jako źródła danych?

**ODP.:** Można użyć następujących czynności:

- Program Microsoft SQL Azure.

- Dowolna wersja programu Microsoft SQL Server 2005 lub nowszego.

- Plik bazy danych programu Microsoft SQL Server (w tym programu SQL Express).

- Microsoft ODBC.

- Plik programu Microsoft Access za pomocą dostawcy .NET Framework dla OLE DB.

- Oracle 7.3, 8i, 9i lub 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>PYT.: Jak używać pliku tekstowego (CSV) rozdzielanymi przecinkami jako źródło danych?

**ODP.:** Oto jak:

1. Utwórz folder do organizowania artefaktów projektów bazy danych i dodać element.

     ![Dodaj nowy element do folderu danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik tekstowy.

     ![Nazwa nowego pliku tekstowego ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edytuj plik tekstowy i Dodaj następujący kod:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Użyj kroków w [Dodaj źródło danych](#add-the-data-source), ale wybierz plik CSV jako źródło danych.

     ![Wprowadź nazwę i wybierz plik CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>PYT.: Co zrobić, jeśli Mój istniejący plik CSV nie zawiera nagłówków kolumn?

**ODP.:** Jeśli nie możesz dodać nagłówków kolumn, można użyć pliku opisu schematu do traktowania plik CSV jako bazy danych.

1. Dodaj nowy plik tekstowy o nazwie *schema.ini*.

     ![Dodaj plik schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Edytuj *schema.ini* plik, aby dodać informacje opisujące strukturę danych. Na przykład plik schematu opisujący plik CSV może wyglądać następująco:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Dodawanie źródła danych do testu.

     ![Dodawanie źródła danych do testu wydajności sieci web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Jeśli używasz *schema.ini* plików, wybierz **bazy danych** (nie plik CSV) jako źródło danych i nadaj mu nazwę.

     ![Dodawanie źródła danych bazy danych](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Utwórz nowe połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wybierz pozycję .NET Framework Data Provider for OLE DB.

     ![Wybieranie dostawcy danych .NET framework OLE DB](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wybierz **zaawansowane**.

     ![Wybierz zaawansowane](../test/media/web_test_databinding_advanced.png)

8. Dla właściwości dostawca zaznacz wartość Microsoft.Jet.OLEDB.4.0, a następnie ustaw **właściwości rozszerzone** na tekst; HDR = NO.

     ![Zastosuj zaawansowane właściwości](../test/media/web_test_databinding_advancedproperties.png)

9. Wpisz nazwę folderu, który zawiera plik schematu i przetestuj połączenie.

     ![Wprowadź ścieżkę do folderu danych](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wybierz plik CSV, którego chcesz używać.

     ![Wybierz plik tekstowy](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po zakończeniu plik CSV pojawia się jako tabela.

     ![Źródła danych dodane do testu](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>PYT.: Jak używać pliku XML jako źródło danych?

**ODP.:** Tak.

1. Utwórz folder do organizowania artefaktów projektów bazy danych i dodać element.

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

4. Użyj kroków w [Dodaj źródło danych](#add-the-data-source), ale wybierz plik XML jako źródła danych.

     ![Wprowadź nazwę i wybierz plik XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>PYT.: Można dodać powiązania danych na żądanie usługi sieci web używającego protokołu SOAP?

**ODP.:** Tak, należy ręcznie zmienić XML protokołu SOAP.

1. Wybierz żądanie usługi sieci web w drzewie żądań i w oknie dialogowym właściwości, wybierz wielokropek (...) we właściwości treść ciągu.

     ![Edytuj ciąg tekstowy usługi sieci web](../test/media/web_test_databinding_webservicerequest.png)

2. Zastąp wartości w treści protokołu SOAP wartościami powiązanych z danymi przy użyciu następującej składni:

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

    Możesz zmienić ją do tego:

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