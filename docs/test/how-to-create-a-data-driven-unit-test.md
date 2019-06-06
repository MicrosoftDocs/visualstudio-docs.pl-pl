---
title: Tworzenie testów jednostkowych opartych na danych
ms.date: 05/08/2019
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5960c84e2cb389580f2d7b0f476da2a456e62585
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745868"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Instrukcje: Tworzenie testu jednostkowego opartego na danych

Aby skonfigurować metodę testu jednostkowego, można pobrać wartości ze źródła danych, można użyć środowisko testów jednostkowych Microsoft dla kodu zarządzanego. Metoda jest uruchamiane kolejno dla każdego wiersza w źródle danych, dzięki czemu można łatwo przetestować różne dane wejściowe, korzystając z jednej metody.

Tworzenie testu jednostkowego opartego na danych obejmuje następujące czynności:

1. Utwórz źródło danych, który zawiera wartości, których używasz w metodzie testowej. Źródła danych mogą być dowolnego typu, który jest zarejestrowany na komputerze, na którym uruchamiany jest test.

2. Dodaj prywatnej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pola i publiczny `TestContext` właściwości klasy testowej.

3. Utwórz metodę testu jednostkowego i Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> atrybutu do niego.

4. Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> właściwość indeksatora można pobrać wartości, których używasz w teście.

## <a name="the-method-under-test"></a>Testowaną metodę

Na przykład załóżmy, że masz:

1. To rozwiązanie o nazwie `MyBank` , akceptuje i przetwarzania transakcji dla różnych typów kont.

2. Projekt w `MyBank` o nazwie `BankDb` który zarządza transakcji dla kont.

3. Klasa o nazwie `Maths` w `BankDb` projektu, który wykonuje funkcje matematyczne w celu zapewnienia korzystne bank każdej transakcji.

4. To test jednostkowy projekt o nazwie `BankDbTests` się testowanie zachowania `BankDb` składnika.

5. To test jednostkowy klasę o nazwie `MathsTests` Aby sprawdzić zachowanie `Maths` klasy.

Następnym krokiem jest przetestowanie metody w `Maths` , dodanie dwóch liczb całkowitych, za pomocą pętli:

```csharp
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

## <a name="create-a-data-source"></a>Utwórz źródło danych

Aby przetestować `AddIntegers` metody, Utwórz źródło danych, która określa zakres wartości dla parametrów i sum, którzy mają być zwracane. W tym przykładzie utworzymy o nazwie bazy danych Sql Compact `MathsData` i tabelę o nazwie `AddIntegersData` zawierający następujące kolumny nazwy i wartości

|Pierwszaliczba|SecondNumber|Suma|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Dodaj TestContext do klasy testowej

Tworzy środowiska testów jednostkowych `TestContext` obiekt, aby zapisać informacje o źródle danych dla testów opartych na danych. Następnie ustawia ten obiekt jako wartość w ramach `TestContext` właściwość, którą tworzysz.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

W metodzie testowej, uzyskujesz dostęp do danych za pośrednictwem `DataRow` właściwości indeksatora `TestContext`.

> [!NOTE]
> .NET core nie obsługuje [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) atrybutu. Jeśli spróbujesz uzyskać dostęp do danych testowych w ten sposób w .NET Core i platformy uniwersalnej systemu Windows projektu testu jednostkowego, zobaczysz błąd podobny do **""TestContext"nie zawiera definicji"DataRow"i żadna metoda dostępne rozszerzenia"DataRow"przyjmującej pierwszy argument typu" TestContext "znaleziono (czy nie brakuje przy użyciu dyrektywy lub odwołania do zestawu?)"** .

## <a name="write-the-test-method"></a>Pisanie metody testowej

Metodę testową dla `AddIntegers` jest dość prosta. Dla każdego wiersza w źródle danych, należy wywołać `AddIntegers` z **Pierwszaliczba** i **Drugaliczba** kolumny wartości jako parametry i sprawdź wartość zwracaną względem **suma** wartość kolumny:

```csharp
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

`Assert` Metoda zawiera komunikat, który wyświetla `x` i `y` wartości iteracji nie powiodło się. Domyślnie wartości potwierdzone — `expected` i `actual` — znajdują się już w szczegółach testów zakończonych niepowodzeniem.

### <a name="specify-the-datasourceattribute"></a>Określ DataSourceAttribute

`DataSource` Atrybut określa parametry połączenia dla źródła danych i nazwę tabeli, którego używasz w metodzie testowej. Konkretne informacje w parametrach połączenia różni się w zależności od tego, jakiego rodzaju źródła danych, którego używasz. W tym przykładzie użyliśmy SqlServerCe bazy danych.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atrybut źródła danych ma trzy konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor z jednym parametrem używa informacji o połączeniu, która jest przechowywana w *app.config* pliku rozwiązania. *DataSourceSettingsName* jest nazwa elementu Xml w pliku konfiguracji, który określa informacje o połączeniu.

Za pomocą *app.config* plików umożliwia zmianę lokalizacji źródła danych bez wprowadzania zmian w same testy jednostek. Aby uzyskać informacje dotyczące tworzenia i używania *app.config* plików, zobacz [instruktażu: definiowanie źródła danych przy użyciu pliku konfiguracji](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource` Konstruktor z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli, która zawiera dane dla metody testowej.

Parametry połączenia są zależne od rodzaju typu źródła danych, ale musi on zawierać element dostawcy, który określa nazwę niezmienną dostawcy danych.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Użyj TestContext.DataRow, aby uzyskać dostęp do danych

Aby uzyskać dostęp do danych `AddIntegersData` tabeli, użyj `TestContext.DataRow` indeksatora. `DataRow` jest <xref:System.Data.DataRow> obiektów, więc pobrać wartości w kolumnie według nazwy indeksu lub kolumn. Ponieważ wartości są zwracane jako obiekty, należy przekonwertować je na odpowiedni typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Uruchom test, aby wyświetlić wyniki

Po zakończeniu pisania metody testowej, skompiluj projekt testu. Metoda testowa jest wyświetlana w **Eksploratora testów** w **testy nieuruchamiane** grupy. Jak uruchomić, zapisać i ponownie uruchomić testy, **Eksplorator testów** wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, i **testy nieuruchamiane**. Możesz wybrać **Uruchom wszystkie** Aby uruchomić wszystkie testy, lub wybierz **Uruchom** wybranie podzestawu testów do uruchomienia.

Paski wyników testów w górnej części **Eksploratora testów** jest animowany podczas działania testu. Na końcu przebiegu testowego pasek będzie zielony, jeśli wszystkie testy zostały przekazane lub czerwony Jeśli którykolwiek z testów nie powiodło się. Podsumowanie przebiegu testu jest wyświetlana w okienku szczegółów u dołu **Eksploratora testów** okna. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.

> [!NOTE]
> Brak wyników dla każdego wiersza danych, a także jeden wynik podsumowania. Jeśli test zakończył się powodzeniem w każdym wierszu danych, uruchom w podsumowaniu jako **zakończone powodzeniem**. W przypadku niepowodzenia testu na każdy wiersz danych podsumowanie uruchomienia jest wyświetlany jako **niepowodzenie**.

Po przeprowadzeniu `AddIntegers_FromDataSourceTest` metody w naszym przykładzie paski wyników zmieni kolor na czerwony, i metoda testowa jest przenoszona do **testy zakończone niepomyślnie**. Test opartych na danych zakończy się niepowodzeniem, jeśli iterowany metod ze źródła danych nie powiedzie się. Po wybraniu nieudanego testu opartego na danych w **Eksploratora testów** okna, w okienku szczegółów są wyświetlane wyniki każdej iteracji, która jest identyfikowana przez indeks wiersza danych. W tym przykładzie wydaje się, że `AddIntegers` algorytm poprawnie nie obsługuje wartości ujemnych.

Po poprawieniu testowaną metodę test, uruchom ponownie, paski wyników zmieni kolor na zielony i metoda testowa jest przenoszona do **przekazywane Test** grupy.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Pisanie testów jednostkowych dla platformy .NET przy użyciu frameworka testów jednostkowych firmy Microsoft](../test/unit-test-your-code.md)
