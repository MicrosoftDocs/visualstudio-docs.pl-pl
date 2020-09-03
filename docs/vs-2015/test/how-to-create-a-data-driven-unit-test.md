---
title: 'Instrukcje: Tworzenie testu jednostkowego opartego na danych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9dc5ad44a73f517b91562209abfab8b0b3e8d4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660531"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Porady: tworzenie testu jednostkowego opartego na danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego, można skonfigurować metodę testową jednostkową, aby pobrać wartości używane w metodzie testowej ze źródła danych. Metoda jest uruchamiana kolejno dla każdego wiersza w źródle danych, co ułatwia przetestowanie różnych danych wejściowych przy użyciu pojedynczej metody.

 Ten temat zawiera następujące sekcje:

- [Testowana Metoda](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)

- [Tworzenie źródła danych](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)

- [Dodawanie TestContext do klasy testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)

- [Pisanie metody testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)

  - [Określanie DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)

  - [Używanie TestContext. DataRow do uzyskiwania dostępu do danych](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)

- [Uruchamianie testu i wyświetlanie wyników](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)

  Tworzenie testu jednostkowego opartego na danych obejmuje następujące kroki:

1. Utwórz źródło danych zawierające wartości, które są używane w metodzie testowej. Źródło danych może być dowolnego typu, który jest zarejestrowany na komputerze, na którym jest uruchamiany test.

2. Dodaj prywatne <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole i Właściwość publiczną `TestContext` do klasy testowej.

3. Utwórz metodę testową jednostkową i Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do niej atrybut.

4. Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Właściwości indeksator do pobrania wartości używanych w teście.

## <a name="the-method-under-test"></a><a name="BKMK_The_method_under_test"></a> Testowana Metoda
 Załóżmy na przykład, że utworzyliśmy:

1. Rozwiązanie o nazwie `MyBank` akceptujące i przetwarza transakcje dla różnych typów kont.

2. Projekt w programie `MyBank` o nazwie `BankDb` , który zarządza transakcjami dla kont.

3. Klasa wywoływana `Maths` w `DbBank` projekcie, która wykonuje funkcje matematyczne, aby zapewnić, że każda transakcja jest korzystna dla banku.

4. Projekt testu jednostkowego o nazwie `BankDbTests` do testowania zachowania `BankDb` składnika.

5. Klasa testów jednostkowych wywoływana `MathsTests` w celu zweryfikowania zachowania `Maths` klasy.

   Będziemy testować metodę w programie `Maths` , która dodaje dwie liczby całkowite przy użyciu pętli:

```
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="creating-a-data-source"></a><a name="BKMK_Creating_a_data_source"></a> Tworzenie źródła danych
 W celu przetestowania `AddIntegers` metody tworzymy źródło danych określające zakres wartości parametrów i sumę, która ma zostać zwrócona. W naszym przykładzie tworzymy bazę danych SQL Compact o nazwie `MathsData` i tabelę o nazwie `AddIntegersData` , która zawiera następujące nazwy kolumn i wartości

|Pierwszaliczba|Drugaliczba|Suma|
|-----------------|------------------|---------|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="adding-a-testcontext-to-the-test-class"></a><a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Dodawanie TestContext do klasy testowej
 Struktura testów jednostkowych tworzy `TestContext` obiekt do przechowywania informacji o źródle danych dla testu opartego na danych. Następnie struktura ustawia ten obiekt jako wartość `TestContext` właściwości, która została utworzona.

```

private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}

```

 W metodzie testowej dostęp do danych odbywa się za pomocą `DataRow` Właściwości indeksatora `TestContext` .

## <a name="writing-the-test-method"></a><a name="BKMK_Writing_the_test_method"></a> Pisanie metody testowej
 Metoda testowa dla `AddIntegers` jest dość prosta. Dla każdego wiersza w źródle danych wywołujemy `AddIntegers` wartości kolumn **Pierwszaliczba** i **drugaliczba** jako parametry i weryfikujemy wartość zwracaną względem wartości kolumny **sum** :

```

[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});

}

```

 Należy zauważyć, że `Assert` Metoda zawiera komunikat, który wyświetla `x` `y` wartości i iteracji zakończonych niepowodzeniem. Domyślnie potwierdzone wartości `expected` i `actual` są już zawarte w szczegółach testu zakończonego niepowodzeniem.

### <a name="specifying-the-datasourceattribute"></a><a name="BKMK_Specifying_the_DataSourceAttribute"></a> Określanie DataSourceAttribute
 Ten `DataSource` atrybut określa parametry połączenia dla źródła danych oraz nazwę tabeli, która jest używana w metodzie testowej. Dokładne informacje w parametrach połączenia różnią się w zależności od rodzaju źródła danych, z którego korzystasz. W tym przykładzie użyto bazy danych SqlServerCe.

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

 Atrybut DataSource ma trzy konstruktory.

```
[DataSource(dataSourceSettingName)]
```

 Konstruktor z jednym parametrem używa informacji o połączeniu, które są przechowywane w pliku app.config dla rozwiązania. *DataSourceSettingsName* jest nazwą elementu XML w pliku konfiguracji, który określa informacje o połączeniu.

 Użycie pliku app.config umożliwia zmianę lokalizacji źródła danych bez wprowadzania zmian do samego testu jednostkowego. Aby uzyskać informacje dotyczące sposobu tworzenia i używania pliku app.config, zobacz [Przewodnik: używanie pliku konfiguracji do definiowania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```
[DataSource(connectionString, tableName)]
```

 `DataSource`Konstruktor z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli, która zawiera dane dla metody testowej.

 Parametry połączenia zależą od typu źródła danych, ale powinny zawierać element dostawcy, który określa niezmienną nazwę dostawcy danych.

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="using-testcontextdatarow-to-access-the-data"></a><a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Używanie TestContext. DataRow do uzyskiwania dostępu do danych
 Aby uzyskać dostęp do danych w `AddIntegersData` tabeli, użyj `TestContext.DataRow` indeksatora. `DataRow` jest <xref:System.Data.DataRow> obiektem, dlatego pobieramy wartości kolumn według nazw indeksu lub kolumn. Ponieważ wartości są zwracane jako obiekty, musimy przekonwertować je na odpowiedni typ:

```
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);

```

## <a name="running-the-test-and-viewing-results"></a><a name="BKMK_Running_the_test_and_viewing_results"></a> Uruchamianie testu i wyświetlanie wyników
 Po zakończeniu pisania metody testowej Skompiluj projekt testowy. Metoda testowa pojawia się w oknie Eksplorator testów w grupie **nie uruchomiono testy** . Podczas uruchamiania, zapisywania i ponownego uruchamiania testów program Test Explorer wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, **testy zakończone pomyślnie**i **nie uruchamiają testów**. Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy, lub wybrać polecenie **Uruchom...** , aby wybrać podzbiór testów do uruchomienia.

 Pasek wyników testu w górnej części Eksploratora jest animowany w miarę przebiegu testu. Na końcu przebiegu testu pasek będzie zielony, jeśli wszystkie testy przebiegły lub czerwona, jeśli którykolwiek z testów zakończył się niepowodzeniem. Podsumowanie przebiegu testu pojawia się w okienku szczegółów u dołu okna Eksplorator testów. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.

 Jeśli `AddIntegers_FromDataSourceTest` w naszym przykładzie uruchomiono metodę, pasek wyników zmieni kolor na czerwony, a metoda testowa jest przenoszona do **testów zakończonych** niepowodzeniem, Test oparty na danych nie powiedzie się, jeśli którykolwiek z iteracji metod ze źródła danych zakończy się niepowodzeniem. Po wybraniu w oknie Eksplorator testów zakończonego niepowodzeniem testu opartego na danych, w okienku szczegółów zostaną wyświetlone wyniki każdej iteracji identyfikowanej przez indeks wiersza danych. W naszym przykładzie wydaje się, że `AddIntegers` algorytm nie obsługuje poprawnie wartości ujemnych.

 Gdy testowana Metoda jest korygowana, a test zostanie uruchomiony ponownie, pasek wyników zmieni kolor na zielony, a metoda testowa zostanie przeniesiona do grupy **testów zakończonych** .

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
 [Instrukcje: Tworzenie i uruchamianie](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48) [testu](../test/unit-test-your-code.md) jednostkowego testów jednostkowych [Uruchom testy jednostkowe w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md) [, pisząc testy jednostkowe dla .NET Framework za pomocą struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)
