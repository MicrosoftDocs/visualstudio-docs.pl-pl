---
title: Definiowanie źródła danych za pomocą pliku konfiguracyjnego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a4f5731a828eb04e57f56a46fe399125b5ded2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75776153"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Przewodnik: Definiowanie źródła danych za pomocą pliku konfiguracyjnego

W tym przewodniku pokazano, jak używać źródła danych zdefiniowanego w pliku *app.config* do testowania jednostkowego. Dowiesz się, jak utworzyć plik *app.config,* który definiuje źródło <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> danych, które mogą być używane przez klasę. Zadania przedstawione w tym instruktażu są następujące:

- Tworzenie pliku *app.config.*

- Definiowanie sekcji konfiguracji niestandardowej.

- Definiowanie ciągów połączeń.

- Definiowanie źródeł danych.

- Uzyskiwanie dostępu do źródeł <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> danych przy użyciu klasy.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebne są:

- Visual Studio Enterprise

- Program Microsoft Access lub Microsoft Excel w celu dostarczenia danych dla co najmniej jednej z metod testowych.

- Rozwiązanie programu Visual Studio, które zawiera projekt testowy.

## <a name="add-an-appconfig-file-to-the-project"></a>Dodawanie pliku app.config do projektu

1. Jeśli projekt testowy ma już plik *app.config,* przejdź do [sekcji Definiowanie konfiguracji niestandardowej](#define-a-custom-configuration-section).

2. Kliknij prawym przyciskiem myszy projekt testowy w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Dodaj** > **nowy element**.

     Zostanie otwarte okno **Dodaj nowy element.**

3. Wybierz szablon **Pliku konfiguracji aplikacji** i kliknij przycisk **Dodaj**.

## <a name="define-a-custom-configuration-section"></a>Definiowanie sekcji konfiguracji niestandardowej

Sprawdź plik *app.config.* Zawiera co najmniej deklarację XML i element główny.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać sekcję konfiguracji niestandardowej do pliku app.config

1. Głównym elementem *app.config* powinien być element **konfiguracji.** Utwórz element **configSeks** w elemencie **konfiguracji.** **ConfigSeks** powinny być pierwszym elementem w pliku *app.config.*

2. W obrębie elementu **configSections** utwórz element **przekroju.**

3. W elemencie **sekcji** dodaj `name` atrybut o nazwie `microsoft.visualstudio.testtools`i przypisz mu wartość . Dodaj inny atrybut `type` wywołany i `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`przypisz mu wartość .

Element **sekcji** powinien wyglądać podobnie do tego:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Nazwa zestawu musi być zgodna z używana wersja.

## <a name="define-connection-strings"></a>Definiowanie ciągów połączeń

Parametry połączenia definiują informacje specyficzne dla dostawcy w celu uzyskania dostępu do źródeł danych. Parametry połączenia zdefiniowane w plikach konfiguracyjnych zapewniają informacje o dostawcy danych wielokrotnego dostępu w aplikacji. W tej sekcji utworzysz dwa parametry połączenia, które będą używane przez źródła danych, które są zdefiniowane w sekcji Konfiguracja niestandardowa.

### <a name="to-define-connection-strings"></a>Aby zdefiniować parametry połączenia

1. Po **configSections** element, utwórz **connectionStrings** element.

2. W ramach **connectionStrings** element, utworzyć dwa **dodać** elementy.

3. W pierwszym **elemencie dodawania** utwórz następujące atrybuty i wartości połączenia z bazą danych programu Microsoft Access:

|Atrybut|Wartości|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

W drugim **elemencie dodawania** utwórz następujące atrybuty i wartości połączenia z arkuszem kalkulacyjnym programu Microsoft Excel:

|Atrybut|Wartości|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** element powinien wyglądać podobnie do tego:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definiowanie źródeł danych

Sekcja źródła danych zawiera cztery atrybuty, które są używane przez aparat testowy do pobierania danych ze źródła danych.

- `name`definiuje tożsamość używaną <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> przez do określenia źródła danych, którego użyć.

- `connectionString`identyfikuje parametry połączenia utworzone w poprzedniej sekcji Definiuj parametry połączenia.

- `dataTableName`definiuje tabelę lub arkusz zawierający dane do użycia w teście.

- `dataAccessMethod`definiuje technikę uzyskiwania dostępu do wartości danych w źródle danych.

W tej sekcji zdefiniujesz dwa źródła danych do użycia w teście jednostkowym.

### <a name="to-define-data-sources"></a>Aby zdefiniować źródła danych

1. Po **connectionStrings** element, utwórz **microsoft.visualstudio.testtools** element. Ta sekcja została utworzona w sekcji Definiuj konfigurację niestandardową.

2. W ramach **elementu microsoft.visualstudio.testtools** utwórz element **dataSources.**

3. W ramach **elementu dataSources** utwórz dwa **elementy dodawania.**

4. W pierwszym **elemencie dodawania** utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Access:

|Atrybut|Wartości|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

W drugim **elemencie dodawania** utwórz następujące atrybuty i wartości źródła danych programu Microsoft Excel:

|Atrybut|Wartości|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

Element **microsoft.visualstudio.testtools** powinien wyglądać podobnie do tego:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Ostateczny plik *app.config* powinien wyglądać podobnie do tego:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego, który używa źródeł danych zdefiniowanych w pliku app.config

Teraz, gdy plik *app.config* został zdefiniowany, utworzysz test jednostkowy, który używa danych znajdujących się w źródłach danych zdefiniowanych w pliku *app.config.* W tej sekcji:

- Utwórz źródła danych znalezione w pliku *app.config.*

- Użyj źródeł danych w dwóch metodach testowych, które porównują wartości w każdym źródle danych.

### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych programu Microsoft Access

1. Utwórz bazę danych programu Microsoft Access o nazwie *testdatasource.accdb*.

2. Utwórz tabelę `MyDataTable` i nadaj jej nazwę w *pliku testdatasource.accdb*.

3. Utwórz dwa `MyDataTable` `Arg1` pola `Arg2` o `Number` nazwie i przy użyciu typu danych.

4. Dodaj pięć encji `MyDataTable` z następującymi wartościami dla `Arg1` i `Arg2`, odpowiednio: (10,50), (3,2), (6,0), (0,8) i (12312,1000).

5. Zapisz i zamknij bazę danych.

6. Zmień parametry połączenia, aby wskazać lokalizację bazy danych. Zmień `Data Source` wartość, aby odzwierciedlić lokalizację bazy danych.

### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel

1. Tworzenie arkusza kalkulacyjnego programu Microsoft Excel o nazwie *data.xlsx*.

2. Utwórz arkusz `Sheet1` o nazwie, jeśli nie istnieje jeszcze w *pliku data.xlsx*.

3. Utwórz dwa nagłówki kolumn `Val1` `Val2` i `Sheet1`nazwij je i w pliku .

4. Dodaj pięć jednostek z `Sheet1` następującymi wartościami dla `Val1` i `Val2`, odpowiednio: (1,1), (2,2), (3,3), (4,4) i (5,0).

5. Zapisz i zamknij arkusz kalkulacyjny.

6. Zmień ciąg połączenia, aby wskazywał lokalizację arkusza kalkulacyjnego. Zmień wartość, `dbq` aby odzwierciedlić lokalizację arkusza kalkulacyjnego.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć test jednostkowy przy użyciu źródeł danych app.config

1. Dodaj test jednostkowy do projektu testowego.

2. Zastąp automatycznie wygenerowaną zawartość testu jednostkowego następującym kodem:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. Sprawdź atrybuty DataSource. Zwróć uwagę na nazwy ustawień z pliku *app.config.*

4. Skompiluj swoje rozwiązanie i uruchom testy MyTestMethod i MyTestMethod2.

> [!IMPORTANT]
> Wdrażanie elementów, takich jak źródła danych, tak aby były dostępne dla testu w katalogu wdrażania.

## <a name="see-also"></a>Zobacz też

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
- [Jak: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)
