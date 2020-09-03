---
title: Tworzenie testów jednostkowych opartych na danych
ms.date: 05/08/2019
ms.topic: how-to
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
ms.openlocfilehash: 936c6b2ee9e05d059c09c2aa074829b35b6ca5fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287990"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Instrukcje: Tworzenie testu jednostkowego opartego na danych

Możesz użyć struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego, aby skonfigurować metodę testową jednostkową w celu pobrania wartości ze źródła danych. Metoda jest uruchamiana kolejno dla każdego wiersza w źródle danych, co ułatwia przetestowanie różnych danych wejściowych przy użyciu pojedynczej metody.

Tworzenie testu jednostkowego opartego na danych obejmuje następujące kroki:

1. Utwórz źródło danych zawierające wartości, które są używane w metodzie testowej. Źródło danych może być dowolnego typu, który jest zarejestrowany na komputerze, na którym jest uruchamiany test.

2. Dodaj prywatne <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole i Właściwość publiczną `TestContext` do klasy testowej.

3. Utwórz metodę testową jednostkową i Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do niej atrybut.

4. Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Właściwości indeksator do pobrania wartości używanych w teście.

## <a name="the-method-under-test"></a>Testowana Metoda

Załóżmy na przykład, że masz:

1. Rozwiązanie o nazwie `MyBank` akceptujące i przetwarza transakcje dla różnych typów kont.

2. Projekt w programie `MyBank` o nazwie `BankDb` , który zarządza transakcjami dla kont.

3. Klasa wywoływana `Maths` w `BankDb` projekcie, która wykonuje funkcje matematyczne, aby zapewnić, że każda transakcja jest korzystna dla banku.

4. Projekt testu jednostkowego o nazwie `BankDbTests` do testowania zachowania `BankDb` składnika.

5. Klasa testów jednostkowych wywoływana `MathsTests` w celu zweryfikowania zachowania `Maths` klasy.

Będziemy testować metodę w programie `Maths` , która dodaje dwie liczby całkowite przy użyciu pętli:

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

Aby przetestować `AddIntegers` metodę, Utwórz źródło danych, które określa zakres wartości parametrów i sumę, która powinna zostać zwrócona. W tym przykładzie utworzymy bazę danych SQL Compact o nazwie `MathsData` i tabelę o nazwie `AddIntegersData` , która zawiera następujące nazwy kolumn i wartości

|Pierwszaliczba|Drugaliczba|Suma|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Dodawanie TestContext do klasy testowej

Struktura testów jednostkowych tworzy `TestContext` obiekt do przechowywania informacji o źródle danych dla testu opartego na danych. Następnie struktura ustawia ten obiekt jako wartość `TestContext` właściwości, która została utworzona.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

W metodzie testowej dostęp do danych odbywa się za pomocą `DataRow` Właściwości indeksatora `TestContext` .

> [!NOTE]
> Platforma .NET Core nie obsługuje atrybutu [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) . Jeśli spróbujesz uzyskać dostęp do danych testowych w ten sposób w projekcie testów jednostkowych .NET Core lub platformy UWP, zobaczysz błąd podobny do **"TestContext" nie zawiera definicji dla elementu "DataRow" i nie można znaleźć dostępnej metody rozszerzającej "DataRow" akceptującej pierwszy argument typu "TestContext" (czy nie brakuje dyrektywy using lub odwołania do zestawu?) "**.

## <a name="write-the-test-method"></a>Napisz metodę testową

Metoda testowa dla `AddIntegers` jest dość prosta. Dla każdego wiersza w źródle danych Wywołaj `AddIntegers` wartości kolumny **Pierwszaliczba** i **drugaliczba** jako parametry, a następnie sprawdź wartość zwracaną względem wartości kolumny **sum** :

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

`Assert`Metoda zawiera komunikat, który wyświetla `x` `y` wartości i iteracji zakończonych niepowodzeniem. Domyślnie potwierdzone wartości- `expected` i `actual` -są już zawarte w szczegółach testów zakończonych niepowodzeniem.

### <a name="specify-the-datasourceattribute"></a>Określ wartość DataSourceAttribute

Ten `DataSource` atrybut określa parametry połączenia dla źródła danych oraz nazwę tabeli, która jest używana w metodzie testowej. Dokładne informacje w parametrach połączenia różnią się w zależności od rodzaju źródła danych, z którego korzystasz. W tym przykładzie użyto bazy danych SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atrybut DataSource ma trzy konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor z jednym parametrem używa informacji o połączeniu, które są przechowywane w pliku *app.config* dla rozwiązania. *DataSourceSettingsName* jest nazwą elementu XML w pliku konfiguracji, który określa informacje o połączeniu.

Użycie pliku *app.config* umożliwia zmianę lokalizacji źródła danych bez wprowadzania zmian do samego testu jednostkowego. Aby uzyskać informacje dotyczące sposobu tworzenia i używania pliku *app.config* , zobacz [Przewodnik: używanie pliku konfiguracji do definiowania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource`Konstruktor z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli, która zawiera dane dla metody testowej.

Parametry połączenia zależą od typu źródła danych, ale powinny zawierać element dostawcy, który określa niezmienną nazwę dostawcy danych.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Używanie TestContext. DataRow do uzyskiwania dostępu do danych

Aby uzyskać dostęp do danych w `AddIntegersData` tabeli, użyj `TestContext.DataRow` indeksatora. `DataRow` jest <xref:System.Data.DataRow> obiektem, więc pobiera wartości kolumn według nazw indeksu lub kolumn. Ponieważ wartości są zwracane jako obiekty, przekonwertuj je na odpowiedni typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Uruchom test i Wyświetl wyniki

Po zakończeniu pisania metody testowej Skompiluj projekt testowy. Metoda testowa pojawia się w **Eksploratorze testów** w grupie **nie uruchomiono testów** . Podczas uruchamiania, zapisywania i ponownego uruchamiania testów program **Test Explorer** wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, **testy zakończone pomyślnie**i **nie uruchamiają testów**. Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy, lub wybrać polecenie **Uruchom** , aby wybrać podzbiór testów do uruchomienia.

Pasek wyników testu w górnej części **Eksploratora testów** jest animowany w miarę przebiegu testu. Na końcu przebiegu testu pasek będzie zielony, jeśli wszystkie testy przebiegły lub czerwona, jeśli którykolwiek z testów zakończył się niepowodzeniem. Podsumowanie przebiegu testu pojawia się w okienku szczegółów u dołu okna **Eksplorator testów** . Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.

> [!NOTE]
> Istnieje wynik dla każdego wiersza danych, a także jeden wynik podsumowania. Jeśli test przeszedł na każdy wiersz danych, przebieg podsumowania jest wyświetlany jako **zakończony**. Jeśli test nie powiódł się w żadnym wierszu danych, przebieg podsumowania jest wyświetlany jako **Niepowodzenie**.

Jeśli `AddIntegers_FromDataSourceTest` w naszym przykładzie została uruchomiona Metoda, pasek wyników zmieni kolor na czerwony, a metoda testowa jest przenoszona do **testów zakończonych niepowodzeniem**. Test oparty na danych kończy się niepowodzeniem, jeśli którykolwiek z iteracji metod ze źródła danych zakończy się niepowodzeniem. Po wybraniu w oknie **Eksplorator testów** zakończonego niepowodzeniem testu opartego na danych, w okienku szczegółów zostaną wyświetlone wyniki każdej iteracji identyfikowanej przez indeks wiersza danych. W naszym przykładzie wydaje się, że `AddIntegers` algorytm nie obsługuje poprawnie wartości ujemnych.

Gdy testowana Metoda jest korygowana, a test zostanie uruchomiony ponownie, pasek wyników zmieni kolor na zielony, a metoda testowa zostanie przeniesiona do grupy **testów zakończonych** .

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Napisz testy jednostkowe dla platformy .NET za pomocą struktury testów jednostkowych firmy Microsoft](../test/unit-test-your-code.md)
