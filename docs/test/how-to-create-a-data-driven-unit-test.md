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
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0a3162dcbbd041a7d2f540a335bd95854afd87d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643479"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Instrukcje: Tworzenie testu jednostkowego opartego na danych

Możesz użyć struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego, aby skonfigurować metodę testową jednostkową w celu pobrania wartości ze źródła danych. Metoda jest uruchamiana kolejno dla każdego wiersza w źródle danych, co ułatwia przetestowanie różnych danych wejściowych przy użyciu pojedynczej metody.

Tworzenie testu jednostkowego opartego na danych obejmuje następujące kroki:

1. Utwórz źródło danych zawierające wartości, które są używane w metodzie testowej. Źródło danych może być dowolnego typu, który jest zarejestrowany na komputerze, na którym jest uruchamiany test.

2. Dodaj prywatne pole <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> i publiczną właściwość `TestContext` do klasy testowej.

3. Utwórz metodę testową jednostkową i Dodaj do niej atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

4. Użyj właściwości <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> Indexer, aby pobrać wartości, które są używane w teście.

## <a name="the-method-under-test"></a>Testowana Metoda

Załóżmy na przykład, że masz:

1. Rozwiązanie o nazwie `MyBank`, które akceptuje i przetwarza transakcje dla różnych typów kont.

2. Projekt w `MyBank` nazywany `BankDb`, który zarządza transakcjami dla kont.

3. Klasa o nazwie `Maths` w projekcie `BankDb`, która wykonuje funkcje matematyczne w celu zapewnienia, że każda transakcja jest korzystna dla banku.

4. Projekt testu jednostkowego o nazwie `BankDbTests`, aby przetestować zachowanie składnika `BankDb`.

5. Klasa testów jednostkowych o nazwie `MathsTests`, aby zweryfikować zachowanie klasy `Maths`.

Będziemy testować metodę w `Maths`, która dodaje dwie liczby całkowite przy użyciu pętli:

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

Aby przetestować metodę `AddIntegers`, Utwórz źródło danych określające zakres wartości parametrów i sumę, która ma zostać zwrócona. W tym przykładzie utworzymy bazę danych SQL Compact o nazwie `MathsData` i tabelę o nazwie `AddIntegersData`, która zawiera następujące nazwy kolumn i wartości

|Pierwszaliczba|Drugaliczba|Należności|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Dodawanie TestContext do klasy testowej

Struktura testów jednostkowych tworzy obiekt `TestContext` do przechowywania informacji o źródle danych dla testu opartego na danych. Następnie struktura ustawia ten obiekt jako wartość właściwości `TestContext`, która została utworzona.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

W metodzie testowej dostęp do danych odbywa się za pomocą właściwości `DataRow` Indexer `TestContext`.

> [!NOTE]
> Platforma .NET Core nie obsługuje atrybutu [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) . Jeśli spróbujesz uzyskać dostęp do danych testowych w ten sposób w projekcie testów jednostkowych .NET Core lub platformy UWP, zobaczysz błąd podobny do **"TestContext" nie zawiera definicji dla elementu "DataRow" i żadna dostępna metoda rozszerzająca "DataRow" nie akceptuje pierwszego argumentu typu " TestContext "można znaleźć (brak dyrektywy using lub odwołania do zestawu?)"** .

## <a name="write-the-test-method"></a>Napisz metodę testową

Metoda testowa dla `AddIntegers` jest dość prosta. Dla każdego wiersza w źródle danych Wywołaj `AddIntegers` z wartościami kolumn **pierwszaliczba** i **drugaliczba** jako parametry, a następnie sprawdź wartość zwracaną względem wartości kolumny **sum** :

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

Metoda `Assert` zawiera komunikat, który wyświetla `x` i `y` wartości iteracji zakończonych niepowodzeniem. Domyślnie potwierdzone wartości-`expected` i `actual` — są już zawarte w szczegółach testu zakończonego niepowodzeniem.

### <a name="specify-the-datasourceattribute"></a>Określ wartość DataSourceAttribute

Atrybut `DataSource` określa parametry połączenia dla źródła danych oraz nazwę tabeli, która jest używana w metodzie testowej. Dokładne informacje w parametrach połączenia różnią się w zależności od rodzaju źródła danych, z którego korzystasz. W tym przykładzie użyto bazy danych SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atrybut DataSource ma trzy konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor z jednym parametrem używa informacji o połączeniu, które są przechowywane w pliku *App. config* dla rozwiązania. *DataSourceSettingsName* jest nazwą elementu XML w pliku konfiguracji, który określa informacje o połączeniu.

Użycie pliku *App. config* pozwala zmienić lokalizację źródła danych bez wprowadzania zmian do samego testu jednostkowego. Aby uzyskać informacje na temat tworzenia i używania pliku *App. config* , zobacz [Przewodnik: używanie pliku konfiguracji do definiowania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

Konstruktor `DataSource` z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli, która zawiera dane dla metody testowej.

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

Aby uzyskać dostęp do danych w tabeli `AddIntegersData`, użyj indeksatora `TestContext.DataRow`. `DataRow` jest obiektem <xref:System.Data.DataRow>, więc pobiera wartości kolumn według nazw indeksu lub kolumn. Ponieważ wartości są zwracane jako obiekty, przekonwertuj je na odpowiedni typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Uruchom test i Wyświetl wyniki

Po zakończeniu pisania metody testowej Skompiluj projekt testowy. Metoda testowa pojawia się w **Eksploratorze testów** w grupie **nie uruchomiono testów** . Podczas uruchamiania, zapisywania i ponownego uruchamiania testów program **Test Explorer** wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, **testy zakończone pomyślnie**i **nie uruchamiają testów**. Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy, lub wybrać polecenie **Uruchom** , aby wybrać podzbiór testów do uruchomienia.

Pasek wyników testu w górnej części **Eksploratora testów** jest animowany w miarę przebiegu testu. Na końcu przebiegu testu pasek będzie zielony, jeśli wszystkie testy przebiegły lub czerwona, jeśli którykolwiek z testów zakończył się niepowodzeniem. Podsumowanie przebiegu testu pojawia się w okienku szczegółów u dołu okna **Eksplorator testów** . Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.

> [!NOTE]
> Istnieje wynik dla każdego wiersza danych, a także jeden wynik podsumowania. Jeśli test przeszedł na każdy wiersz danych, przebieg podsumowania jest wyświetlany jako **zakończony**. Jeśli test nie powiódł się w żadnym wierszu danych, przebieg podsumowania jest wyświetlany jako **Niepowodzenie**.

Jeśli w naszym przykładzie uruchomiono metodę `AddIntegers_FromDataSourceTest`, pasek wyników zmieni kolor na czerwony, a metoda testowa jest przenoszona do **testów zakończonych niepowodzeniem**. Test oparty na danych kończy się niepowodzeniem, jeśli którykolwiek z iteracji metod ze źródła danych zakończy się niepowodzeniem. Po wybraniu w oknie **Eksplorator testów** zakończonego niepowodzeniem testu opartego na danych, w okienku szczegółów zostaną wyświetlone wyniki każdej iteracji identyfikowanej przez indeks wiersza danych. W naszym przykładzie wydaje się, że algorytm `AddIntegers` nie obsługuje poprawnych wartości ujemnych.

Gdy testowana Metoda jest korygowana, a test zostanie uruchomiony ponownie, pasek wyników zmieni kolor na zielony, a metoda testowa zostanie przeniesiona do grupy **testów zakończonych** .

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Napisz testy jednostkowe dla platformy .NET za pomocą struktury testów jednostkowych firmy Microsoft](../test/unit-test-your-code.md)
