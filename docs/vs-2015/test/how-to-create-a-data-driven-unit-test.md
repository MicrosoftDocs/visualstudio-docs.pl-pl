---
title: 'Instrukcje: Tworzenie testu jednostkowego opartego na danych | Dokumentacja firmy Microsoft'
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02f55f39a045dcc0cc0b8eddf46134d4a380c9f1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779165"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Instrukcje: Tworzenie testu jednostkowego opartego na danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą środowiska testów jednostkowych Microsoft dla kodu zarządzanego, możesz skonfigurować metodę testu jednostkowego można pobrać wartości używanych w metodzie testowej, ze źródła danych. Metoda jest uruchamiane kolejno dla każdego wiersza w źródle danych, dzięki czemu można łatwo przetestować różne dane wejściowe, korzystając z jednej metody.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Testowaną metodę](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
- [Tworzenie źródła danych](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
- [Dodawanie TestContext do klasy testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
- [Pisanie metody testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
  -   [Określanie DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
  -   [Aby uzyskać dostęp do danych za pomocą TestContext.DataRow](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
- [Uruchamianie testu i wyświetlania wyników](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
  Tworzenie testu jednostkowego opartego na danych obejmuje następujące czynności:  
  
1.  Utwórz źródło danych, który zawiera wartości, których używasz w metodzie testowej. Źródła danych mogą być dowolnego typu, który jest zarejestrowany na komputerze, na którym uruchamiany jest test.  
  
2.  Dodaj prywatnej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pola i publiczny `TestContext` właściwości klasy testowej.  
  
3.  Utwórz metodę testu jednostkowego i Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> atrybutu do niego.  
  
4.  Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> właściwość indeksatora można pobrać wartości, których używasz w teście.  
  
##  <a name="BKMK_The_method_under_test"></a> Testowaną metodę  
 Na przykład załóżmy, że utworzono:  
  
1. To rozwiązanie o nazwie `MyBank` , akceptuje i przetwarzania transakcji dla różnych typów kont.  
  
2. Projekt w `MyBank` o nazwie `BankDb` który zarządza transakcji dla kont.  
  
3. Klasa o nazwie `Maths` w `DbBank` projektu, który wykonuje funkcje matematyczne w celu zapewnienia korzystne bank każdej transakcji.  
  
4. To test jednostkowy projekt o nazwie `BankDbTests` się testowanie zachowania `BankDb` składnika.  
  
5. To test jednostkowy klasę o nazwie `MathsTests` Aby sprawdzić zachowanie `Maths` klasy.  
  
   Testujemy metody w `Maths` , dodanie dwóch liczb całkowitych, za pomocą pętli:  
  
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
  
##  <a name="BKMK_Creating_a_data_source"></a> Tworzenie źródła danych  
 Aby przetestować `AddIntegers` metody, możemy utworzyć źródło danych, która określa zakres wartości dla parametrów i sum, którzy mają być zwracane. W tym przykładzie tworzymy bazę danych Sql Compact o nazwie `MathsData` i tabelę o nazwie `AddIntegersData` zawierający następujące kolumny nazwy i wartości  
  
|Pierwszaliczba|SecondNumber|Suma|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Dodawanie TestContext do klasy testowej  
 Tworzy środowiska testów jednostkowych `TestContext` obiekt, aby zapisać informacje o źródle danych dla testów opartych na danych. Następnie ustawia ten obiekt jako wartość w ramach `TestContext` właściwość, która zostanie utworzona.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 W metodzie testowej, uzyskujesz dostęp do danych za pośrednictwem `DataRow` właściwości indeksatora `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Pisanie metody testowej  
 Metodę testową dla `AddIntegers` jest dość prosta. Dla każdego wiersza w źródle danych nazywanej `AddIntegers` z **Pierwszaliczba** i **Drugaliczba** wartości kolumny jako parametry i zweryfikujemy wartość zwracaną względem **suma**wartości w kolumnie:  
  
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
  
 Należy pamiętać, że `Assert` metoda zawiera komunikat, który wyświetla `x` i `y` wartości iteracji nie powiodło się. Domyślnie wartość potwierdzone `expected` i `actual`, znajdują się już w szczegółach testów zakończonych niepowodzeniem.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Określanie DataSourceAttribute  
 `DataSource` Atrybut określa parametry połączenia dla źródła danych i nazwę tabeli, którego używasz w metodzie testowej. Konkretne informacje w parametrach połączenia różni się w zależności od tego, jakiego rodzaju źródła danych, którego używasz. W tym przykładzie użyliśmy SqlServerCe bazy danych.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Atrybut źródła danych ma trzy konstruktory.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Konstruktor z jednym parametrem używa informacji o połączeniu, który jest przechowywany w pliku app.config dla rozwiązania. *DataSourceSettingsName* jest nazwa elementu Xml w pliku konfiguracji, który określa informacje o połączeniu.  
  
 Przy użyciu pliku app.config umożliwia zmianę lokalizacji źródła danych bez wprowadzania zmian w same testy jednostek. Aby uzyskać informacje o sposobie tworzenia i używania pliku app.config, zobacz [instruktażu: Korzystanie z pliku konfiguracji do określania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 `DataSource` Konstruktor z dwoma parametrami określa parametry połączenia dla źródła danych i nazwę tabeli, która zawiera dane dla metody testowej.  
  
 Parametry połączenia są zależne od rodzaju typu źródła danych, ale musi on zawierać element dostawcy, który określa nazwę niezmienną dostawcy danych.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Aby uzyskać dostęp do danych za pomocą TestContext.DataRow  
 Aby uzyskać dostęp do danych `AddIntegersData` tabeli, użyj `TestContext.DataRow` indeksatora. `DataRow` jest <xref:System.Data.DataRow> obiektu, aby pobranie wartości w kolumnie według nazwy indeksu lub kolumn. Wartości są zwracane jako obiekty, musimy przekonwertować je na odpowiedni typ:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Uruchamianie testu i wyświetlania wyników  
 Po zakończeniu pisania metody testowej kompilacji projektu testowego. Metoda testowa pojawia się w oknie Eksploratora testów w **testy nieuruchamiane** grupy. Podczas przeprowadzania, zapisywania i ponownego przeprowadzania testów Test Explorer wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, i **testy nieuruchamiane**. Możesz wybrać **Uruchom wszystkie** Aby uruchomić wszystkie testy, lub wybierz **uruchamianie...**  wybranie podzestawu testów do uruchomienia.  
  
 Paski wyników testów w górnej części Eksploratora jest animowany podczas działania testu. Na końcu przebiegu testowego pasek będzie zielony, jeśli wszystkie testy zostały przekazane lub czerwony Jeśli którykolwiek z testów nie powiodło się. Podsumowanie przebiegu testu zostanie wyświetlony w okienku szczegółów u dołu okna Eksploratora testów. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.  
  
 Po przeprowadzeniu `AddIntegers_FromDataSourceTest` metody w naszym przykładzie paski wyników zmieni kolor na czerwony, i metoda testowa jest przenoszona do **testy zakończone niepomyślnie** testu opartego na danych zakończy się niepowodzeniem, jeśli źródło iterowany metod z danych kończy się niepowodzeniem. W przypadku nieudanego testu opartego na danych w oknie Eksploratora testów, w okienku szczegółów zostaną wyświetlone wyniki każdej iteracji, która jest identyfikowana przez indeks wiersza danych. W tym przykładzie wydaje się, że `AddIntegers` algorytm poprawnie nie obsługuje wartości ujemnych.  
  
 Po poprawieniu testowaną metodę test, uruchom ponownie, paski wyników zmieni kolor na zielony i metoda testowa jest przenoszona do **przekazywane Test** grupy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Instrukcje: Tworzenie i uruchamianie testu jednostkowego](http://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)   
 [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md)   
 [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)
