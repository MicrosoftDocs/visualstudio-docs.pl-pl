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
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f50dad637d9efa2db347ff9f1b4828abf8c733af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589191"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Jak: Tworzenie testu jednostkowego opartego na danych

Za pomocą struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego można skonfigurować metodę testu jednostkowego w celu pobrania wartości ze źródła danych. Metoda jest uruchamiana kolejno dla każdego wiersza w źródle danych, co ułatwia testowanie różnych danych wejściowych przy użyciu jednej metody.

Tworzenie testu jednostkowego opartego na danych obejmuje następujące kroki:

1. Utwórz źródło danych, które zawiera wartości używane w metodzie testowej. Źródłem danych może być dowolny typ, który jest zarejestrowany na komputerze, który uruchamia test.

2. Dodaj pole <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> prywatne i `TestContext` właściwość publiczną do klasy testowej.

3. Utwórz metodę testu jednostkowego i dodaj do niej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> atrybut.

4. Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> właściwości indeksatora, aby pobrać wartości, które są używane w teście.

## <a name="the-method-under-test"></a>Metoda, o która 2015

Na przykład załóżmy, że masz:

1. Rozwiązanie o `MyBank` nazwie, które akceptuje i przetwarza transakcje dla różnych typów kont.

2. Projekt o `MyBank` `BankDb` nazwie, który zarządza transakcjami dla kont.

3. Klasa wywoływana `Maths` `BankDb` w projekcie, która wykonuje funkcje matematyczne, aby upewnić się, że każda transakcja jest korzystna dla banku.

4. Projekt testu jednostkowego wywoływany `BankDbTests` w `BankDb` celu przetestowania zachowania składnika.

5. Klasa testu jednostkowego wywoływana `MathsTests` w `Maths` celu sprawdzenia zachowania klasy.

Przetestujemy metodę, `Maths` która dodaje dwie liczby całkowite przy użyciu pętli:

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

## <a name="create-a-data-source"></a>Tworzenie źródła danych

Aby przetestować `AddIntegers` metodę, należy utworzyć źródło danych, które określa zakres wartości dla parametrów i sumy, która ma zostać zwrócona. W tym przykładzie utworzymy bazę `MathsData` danych Sql `AddIntegersData` Compact o nazwie i tabelę o nazwie, która zawiera następujące nazwy kolumn i wartości

|PierwszyLiczba|Drugi Numer|Suma|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Dodawanie testcontext do klasy testowej

Struktura testów jednostkowych `TestContext` tworzy obiekt do przechowywania informacji o źródle danych dla testu opartego na danych. Struktura następnie ustawia ten obiekt jako `TestContext` wartość właściwości, które można utworzyć.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

W metodzie testowej można uzyskać `DataRow` dostęp do `TestContext`danych za pośrednictwem właściwości indeksatora .

> [!NOTE]
> Program .NET Core nie obsługuje atrybutu [DataSource.](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) Jeśli spróbujesz uzyskać dostęp do danych testowych w ten sposób w projekcie testowym jednostkowym .NET Core lub PLATFORMY UNIWERSALNEJ systemu Operacyjnego,zobaczysz błąd podobny do **"TestContext" nie zawiera definicji dla 'DataRow' i nie ma dostępnej metody rozszerzenia "DataRow" akceptującej pierwszy argument typu 'TestContext' można znaleźć (czy brakuje ci using dyrektywy lub odwołania do zestawu?)"**.

## <a name="write-the-test-method"></a>Napisz metodę testową

Metoda badania `AddIntegers` jest dość prosta. Dla każdego wiersza w `AddIntegers` źródle danych wywołaj z wartościami kolumn **FirstNumber** i **SecondNumber** jako parametry i sprawdź zwracaną wartość względem wartości kolumny **Suma:**

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

Metoda `Assert` zawiera komunikat, który `x` `y` wyświetla i wartości nieudanej iteracji. Domyślnie potwierdzone wartości — `expected` `actual` i — są już uwzględnione w szczegółach testu nie powiodło się.

### <a name="specify-the-datasourceattribute"></a>Określ atrybut DataSourceAttribute

Atrybut `DataSource` określa ciąg połączenia dla źródła danych i nazwę tabeli, która jest używana w metodzie testowej. Dokładne informacje w ciągu połączenia różnią się w zależności od rodzaju źródła danych, którego używasz. W tym przykładzie użyliśmy bazy danych SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atrybut DataSource ma trzy konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor z jednym parametrem używa informacji o połączeniu, który jest przechowywany w pliku *app.config* dla rozwiązania. *DataSourceSettingsName* jest nazwą elementu Xml w pliku konfiguracyjnym, który określa informacje o połączeniu.

Za pomocą pliku *app.config* pozwala zmienić lokalizację źródła danych bez wprowadzania zmian w samym teście jednostkowym. Aby uzyskać informacje dotyczące tworzenia i używania pliku *app.config,* zobacz [Przewodnik: Definiowanie źródła danych za pomocą pliku konfiguracyjnego](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource` Konstruktor z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli zawierającej dane dla metody testowej.

Parametry połączenia zależą od typu typu źródła danych, ale powinny zawierać Provider element, który określa niezmienną nazwę dostawcy danych.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Użyj TestContext.DataRow, aby uzyskać dostęp do danych

Aby uzyskać dostęp `AddIntegersData` do danych `TestContext.DataRow` w tabeli, użyj indeksatora. `DataRow`jest <xref:System.Data.DataRow> obiektem, więc pobieraj wartości kolumn według nazw indeksów lub kolumn. Ponieważ wartości są zwracane jako obiekty, przekonwertuj je na odpowiedni typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Uruchamianie wyników testu i wyświetlanie

Po zakończeniu pisania metody testowej skompiluj projekt testowy. Metoda testowa pojawia się w **Eksploratorze testów** w grupie **Nie uruchamiaj testów.** Podczas uruchamiania, zapisywania i ponownego uruchamiania testów **Eksplorator testów** wyświetla wyniki w grupach **testów nieudanych,** **testów przeszłych**i **nie uruchamianych testów.** Można wybrać **uruchom wszystkie** testy, lub **wybierz** uruchom, aby wybrać podzbiór testów do uruchomienia.

Pasek wyników testu w górnej części **Eksploratora testów** jest animowany podczas przebiegu testu. Po zakończeniu testu pasek będzie zielony, jeśli wszystkie testy zostały zdadzą lub czerwony, jeśli którykolwiek z testów nie powiodło się. Podsumowanie przebiegu testu pojawia się w okienku szczegółów u dołu okna **Eksploratora testów.** Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.

> [!NOTE]
> Jest wynik dla każdego wiersza danych, a także jeden wynik podsumowania. Jeśli test przeszedł na każdy wiersz danych, przebieg podsumowania jest wyświetlany jako **Przekazany**. Jeśli test nie powiódł się w dowolnym wierszu danych, przebieg podsumowania jest wyświetlany jako **nieudany**.

Jeśli uruchomiono `AddIntegers_FromDataSourceTest` metodę w naszym przykładzie, pasek wyników zmieni kolor na czerwony, a metoda testowa zostanie przeniesiona do **testów nieudanych.** Test oparty na danych kończy się niepowodzeniem, jeśli którakolwiek z iteracyjnych metod ze źródła danych nie powiedzie się. Po wybraniu testu opartego na danych nie powiodło się w oknie **Eksploratora testów,** okienko szczegółów wyświetla wyniki każdej iteracji, która jest identyfikowana przez indeks wiersza danych. W naszym przykładzie wydaje `AddIntegers` się, że algorytm nie obsługuje poprawnie wartości ujemnych.

Gdy testowana metoda jest korygowana i test ponownie uruchomić, pasek wyników zmienia kolor na zielony i metoda testowa jest przenoszona do grupy **Testów przeszłych.**

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Pisanie testów jednostkowych dla platformy .NET za pomocą struktury testów jednostkowych firmy Microsoft](../test/unit-test-your-code.md)
