---
title: 'Wskazówki: korzystanie z pliku konfiguracji do określania źródła danych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d329e1aedb5b81c2be2d52614e4c540ecb8ef8aa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066996"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Wskazówki: Korzystanie z pliku konfiguracji do określania źródła danych

Ten instruktaż ilustruje sposób użycia źródła danych, zdefiniowanego w *app.config* pliku dla testów jednostkowych. Przedstawiono sposób tworzenia *app.config* pliku, który definiuje źródła danych, które mogą być używane przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy. Zadania przedstawione w tym przewodniku są następujące:

- Tworzenie *app.config* pliku.

- Definiowanie sekcji niestandardowej konfiguracji.

- Definiowanie parametrów połączenia.

- Definiowanie źródeł danych.

- Dostęp do danych ze źródłami <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebne są:

- Visual Studio Enterprise

- Program Microsoft Access albo programu Microsoft Excel do dostarczania danych dla co najmniej jednej z metod testowych.

- Rozwiązania programu Visual Studio, która zawiera projekt testowy.

## <a name="add-an-appconfig-file-to-the-project"></a>Dodawanie pliku app.config w projekcie

1. Jeśli projekt testu już *app.config* pliku, przejdź do [zdefiniować sekcję Konfiguracja niestandardowa](#define-a-custom-configuration-section).

2. Kliknij prawym przyciskiem myszy projekt testu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj** > **nowy element**.

     **Dodaj nowy element** zostanie otwarte okno.

3. Wybierz **pliku konfiguracji aplikacji** szablon i kliknij przycisk **Dodaj**.

##  <a name="define-a-custom-configuration-section"></a>Zdefiniuj sekcji niestandardowej konfiguracji

Sprawdź *app.config* pliku. Zawiera on co najmniej deklaracji XML i elementu głównego.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać do pliku app.config sekcję Konfiguracja niestandardowa

1. Element główny *app.config* powinien być **konfiguracji** elementu. Tworzenie **configSections** elemencie **konfiguracji** elementu. **ConfigSections** powinien być pierwszym elementem w *app.config* pliku.

2. W ramach **configSections** elementu, Utwórz **sekcji** elementu.

3. W **sekcji** elementu Dodawanie atrybutu o nazwie `name` i przypisz jej wartość `microsoft.visualstudio.testtools`. Dodaj inny atrybut o nazwie `type` i przypisz jej wartość `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`.

**Sekcji** element powinien wyglądać mniej więcej tak:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Nazwa zestawu musi odpowiadać kompilacji programu Microsoft Visual Studio .NET Framework, którego używasz. Wybierz wersję odpowiadającą 9.0.0.0 korzystania z programu Visual Studio .NET Framework 3.5. Jeśli używasz programu Visual Studio .NET Framework 2.0, wybierz wersję odpowiadającą 8.0.0.0.

## <a name="define-connection-strings"></a>Zdefiniuj parametry połączenia

Parametry połączenia definiują informacje specyficzne dla dostawcy do uzyskiwania dostępu do źródła danych. Parametry połączenia określone w plikach konfiguracji udostępnianie informacji o dostawcy danych wielokrotnego użytku w aplikacji. W tej sekcji utworzysz dwa ciągi połączeń, które będą używane przez źródła danych, które są zdefiniowane w sekcji Konfiguracja niestandardowa.

### <a name="to-define-connection-strings"></a>Aby zdefiniować parametry połączenia

1. Po **configSections** elementu, Utwórz **connectionStrings** elementu.

2. W ramach **connectionStrings** elementu, utworzysz dwa **Dodaj** elementów.

3. W pierwszym **Dodaj** elementu, utwórz następujące atrybuty i wartości dla połączenia z bazą danych programu Microsoft Access:

|Atrybut|Wartości|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

W drugim **Dodaj** elementu, utwórz następujące atrybuty i wartości dla połączenia do arkusza kalkulacyjnego programu Microsoft Excel:

|Atrybut|Wartości|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** element powinien wyglądać mniej więcej tak:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definiowanie źródeł danych

Sekcja źródła danych zawiera cztery atrybuty, które są używane przez silnik testowy można pobrać danych ze źródła danych.

- `name` Określa tożsamość używana przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do określenia danych, które źródło do użycia.

- `connectionString` Określa parametry połączenia, utworzony w poprzedniej sekcji zdefiniować parametry połączenia.

- `dataTableName` Definiuje tabeli lub arkusza, która przechowuje dane do użycia w teście.

- `dataAccessMethod` Definiuje technik do uzyskania dostępu do wartości danych w źródle danych.

W tej sekcji zdefiniujesz dwóch źródeł danych do użycia podczas testów jednostkowych.

### <a name="to-define-data-sources"></a>Aby zdefiniować źródła danych

1. Po **connectionStrings** elementu, Utwórz **microsoft.visualstudio.testtools** elementu. W tej sekcji został utworzony w Definiuj sekcji konfiguracji niestandardowych.

2. W ramach **microsoft.visualstudio.testtools** elementu, Utwórz **źródeł danych** elementu.

3. W ramach **źródeł danych** elementu, utworzysz dwa **Dodaj** elementów.

4. W pierwszym **Dodaj** elementu, utwórz następujące atrybuty i wartości dla źródła danych Microsoft Access:

|Atrybut|Wartości|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

W drugim **Dodaj** elementu, utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Excel:

|Atrybut|Wartości|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**Microsoft.visualstudio.testtools** element powinien wyglądać mniej więcej tak:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Końcowe *app.config* plik powinien wyglądać mniej więcej tak:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
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

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego, który używa źródłami danych zdefiniowanymi w pliku app.config

Teraz, gdy *app.config* pliku została zdefiniowana, utworzy test jednostkowy, który korzysta z danych znajdujących się w źródłach danych, które są zdefiniowane w *app.config* pliku. W tej sekcji obejmuje następujące czynności:

- Tworzenie z danych źródeł *app.config* pliku.

- Używanie źródeł danych, w dwie metody testowe są porównywane wartości w poszczególnych źródeł danych.

### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych Microsoft Access

1. Utwórz bazę danych Microsoft Access o nazwie *testdatasource.accdb*.

2. Utwórz tabelę i nadaj mu nazwę `MyDataTable` w *testdatasource.accdb*.

3. Utwórz dwa pola w `MyDataTable` o nazwie `Arg1` i `Arg2` przy użyciu `Number` typu danych.

4. Dodawanie pięć jednostek do `MyDataTable` z następującymi wartościami dla `Arg1` i `Arg2`odpowiednio: (10,50), (3,2) (6,0) (0,8) i (12312,1000).

5. Zapisz i zamknij bazy danych.

6. Zmień parametry połączenia, aby wskazać lokalizację bazy danych. Zmień wartość właściwości `Data Source` uwzględnienie lokalizacji bazy danych.

### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel

1. Utwórz arkusz kalkulacyjny programu Excel o nazwie *PowerPivot.xlsx*.

2. Utwórz arkusz o nazwie `Sheet1` Jeśli go jeszcze nie istnieje w *PowerPivot.xlsx*.

3. Utwórz dwa nagłówki kolumn i nazwij je `Val1` i `Val2` w `Sheet1`.

4. Dodawanie pięć jednostek do `Sheet1` z następującymi wartościami dla `Val1` i `Val2`odpowiednio: (1,1), (2, 2,) (3,3) (4,4) i (5,0).

5. Zapisz i zamknij arkusza kalkulacyjnego.

6. Zmień parametry połączenia, aby wskazać lokalizację arkusza kalkulacyjnego. Zmień wartość właściwości `dbq` do uwzględnienia lokalizacji w arkuszu kalkulacyjnym.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć test jednostki za pomocą źródeł danych w pliku app.config

1. Dodaj test jednostkowy do projektu testowego.

2. Zastąp zawartość automatycznego generowania testu jednostkowego z następującym kodem:

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

3. Sprawdź atrybutów elementu DataSource. Zwróć uwagę, nazwy ustawień z *app.config* pliku.

4. Skompiluj rozwiązanie i uruchomić testy MyTestMethod i MyTestMethod2.

> [!IMPORTANT]
> Wdróż elementy, takie jak źródła danych, tak aby były dostępne dla testów w katalogu wdrożenia.

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Instrukcje: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)