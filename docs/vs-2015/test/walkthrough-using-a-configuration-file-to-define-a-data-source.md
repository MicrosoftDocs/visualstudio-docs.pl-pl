---
title: 'Wskazówki: korzystanie z pliku konfiguracji w celu zdefiniowania źródła danych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f669c4dcfb91579ac50270914112cd6388e2743
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547982"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Wskazówki: korzystanie z pliku konfiguracji do określania źródła danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak używać źródła danych zdefiniowanego w pliku app.config do testowania jednostkowego. Dowiesz się, jak utworzyć plik app.config, który definiuje źródło danych, które może być używane przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasę. Zadania przedstawione w tym instruktażu obejmują następujące elementy:

- Tworzenie pliku app.config.

- Definiowanie sekcji konfiguracji niestandardowej.

- Definiowanie parametrów połączenia.

- Definiowanie źródeł danych.

- Uzyskiwanie dostępu do źródeł danych przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy.

## <a name="prerequisites"></a>Wymagania wstępne
 W celu wykonania instrukcji w tym przewodniku potrzebne są następujące elementy:

- Visual Studio Enterprise

- Microsoft Access lub Microsoft Excel, aby dostarczyć dane dla co najmniej jednej z metod testowych.

- Rozwiązanie programu Visual Studio, które zawiera projekt testowy.

## <a name="create-the-appconfig-file"></a>Utwórz plik App.config

#### <a name="to-add-an-appconfig-file-to-the-project"></a>Aby dodać plik app.config do projektu

1. Jeśli projekt testowy ma już plik app.config, przejdź do [sekcji Definiowanie konfiguracji niestandardowej](#DefineCustomConfigurationSection).

2. Kliknij prawym przyciskiem myszy projekt testowy w **Eksplorator rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

     Zostanie otwarte okno **Dodaj nowy element** .

3. Wybierz szablon **pliku konfiguracji aplikacji** , a następnie kliknij przycisk **Dodaj**.

## <a name="define-a-custom-configuration-section"></a><a name="DefineCustomConfigurationSection"></a> Definiowanie sekcji konfiguracji niestandardowej
 Zapoznaj się z plikiem app.config. Zawiera co najmniej deklarację XML i element główny.

#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać sekcję Konfiguracja niestandardowa do pliku app.config

1. Element główny app.config powinien być `configuration` elementem. Utwórz `configSections` element w obrębie `configuration` elementu. `configSections`Powinien to być pierwszy element w pliku app.config.

2. W `configSections` elemencie Utwórz `section` element.

3. W `section` elemencie Dodaj atrybut o nazwie `name` i przypisz mu wartość równą `microsoft.visualstudio.testtools` . Dodaj inny atrybut o nazwie `type` i przypisz mu wartość równą `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

   `section`Element powinien wyglądać podobnie do tego:

```
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Nazwa zestawu musi być zgodna z Microsoft Visual Studio .NET Framework kompilacją, która jest używana. Ustaw wersję na 9.0.0.0, jeśli używasz programu Visual Studio .NET Framework 3,5. Jeśli używasz programu Visual Studio .NET Framework 2,0, ustaw wersję na 8.0.0.0.

## <a name="define-connection-strings"></a>Definiowanie parametrów połączenia
 Parametry połączenia definiują informacje specyficzne dla dostawcy na potrzeby uzyskiwania dostępu do źródeł danych. Parametry połączenia zdefiniowane w plikach konfiguracji zapewniają informacje o dostawcy danych wielokrotnego użytku w aplikacji. W tej sekcji utworzysz dwa parametry połączenia, które będą używane przez źródła danych, które są zdefiniowane w sekcji Konfiguracja niestandardowa.

#### <a name="to-define-connection-strings"></a>Aby zdefiniować parametry połączenia

1. Po `configSections` elemencie Utwórz `connectionStrings` element.

2. W obrębie `connectionStrings` elementu Utwórz dwa `add` elementy.

3. W pierwszym `add` elemencie Utwórz następujące atrybuty i wartości dla połączenia z bazą danych programu Microsoft Access:

|Atrybut|Wartości|
|---------------|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

 W drugim `add` elemencie Utwórz następujące atrybuty i wartości dla połączenia z arkuszem kalkulacyjnym programu Microsoft Excel:

|Atrybut|Wartości|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

 `connectionStrings`Element powinien wyglądać podobnie do tego:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definiowanie źródeł danych
 Sekcja źródła danych zawiera cztery atrybuty, które są używane przez aparat testowy do pobierania danych ze źródła danych.

- `name` definiuje tożsamość używaną przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> program do określenia źródła danych, które ma być używane.

- `connectionString` Identyfikuje parametry połączenia utworzone w poprzedniej sekcji Definiowanie parametrów połączenia.

- `dataTableName` definiuje tabelę lub arkusz, który przechowuje dane do użycia w teście.

- `dataAccessMethod` definiuje technikę uzyskiwania dostępu do wartości danych w źródle danych.

  W tej sekcji zdefiniujesz dwa źródła danych, które zostaną użyte w teście jednostkowym.

#### <a name="to-define-data-sources"></a>Aby zdefiniować źródła danych

1. Po `connectionStrings` elemencie Utwórz `microsoft.visualstudio.testtools` element. Ta sekcja została utworzona w sekcji Definiowanie konfiguracji niestandardowej.

2. W `microsoft.visualstudio.testtools` elemencie Utwórz `dataSources` element.

3. W obrębie `dataSources` elementu Utwórz dwa `add` elementy.

4. W pierwszym `add` elemencie Utwórz następujące atrybuty i wartości dla źródła danych Microsoft Access:

|Atrybut|Wartość|
|---------------|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

 W drugim `add` elemencie Utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Excel:

|Atrybut|Wartość|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

 `microsoft.visualstudio.testtools`Element powinien wyglądać podobnie do tego:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

 Końcowy plik app.config powinien wyglądać podobnie do tego:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego przy użyciu źródeł danych zdefiniowanych w app.config
 Teraz, gdy został zdefiniowany plik app.config, zostanie utworzony test jednostkowy, który używa danych znajdujących się w źródłach danych, które są zdefiniowane w pliku app.config. W tej sekcji będziemy:

- Utwórz źródła danych znajdujące się w pliku app.config.

- Użyj źródeł danych w dwóch metodach testowych, które porównują wartości w każdym źródle danych.

#### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych programu Microsoft Access

1. Utwórz bazę danych programu Microsoft Access o nazwie `testdatasource.accdb` .

2. Utwórz tabelę i nadaj jej nazwę `MyDataTable` `testdatasource.accdb` .

3. Utwórz dwa pola w `MyDataTable` nazwanych `Arg1` i `Arg2` przy użyciu `Number` typu danych.

4. Dodaj pięć jednostek do `MyDataTable` następujących wartości dla `Arg1` i `Arg2` , odpowiednio: (10, 50), (3, 2), (6, 0), (0, 8) i (12312, 1000).

5. Zapisz i Zamknij bazę danych.

6. Zmień parametry połączenia tak, aby wskazywały lokalizację bazy danych. Zmień wartość, `Data Source` aby odzwierciedlała lokalizację bazy danych.

#### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel

1. Utwórz arkusz kalkulacyjny programu Microsoft Excel o nazwie `data.xlsx` .

2. Utwórz arkusz o nazwie `Sheet1` , jeśli jeszcze nie istnieje w `data.xlsx` .

3. Utwórz dwa nagłówki kolumn i nadaj im nazwę `Val1` i `Val2` w `Sheet1` .

4. Dodaj pięć jednostek do `Sheet1` następujących wartości dla `Val1` i `Val2` , odpowiednio: (1, 1), (2, 2), (3, 3), (4, 4) i (5, 0).

5. Zapisz i zamknij arkusz kalkulacyjny.

6. Zmień parametry połączenia tak, aby wskazywały lokalizację arkusza kalkulacyjnego. Zmień wartość, `dbq` aby odzwierciedlić lokalizację arkusza kalkulacyjnego.

#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć test jednostkowy przy użyciu app.config źródeł danych

1. Dodaj test jednostkowy do projektu testowego.

     Aby uzyskać więcej informacji, zobacz [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).

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

3. Przejrzyj atrybuty DataSource. Zwróć uwagę na nazwy ustawień z pliku app.config.

4. Kompiluj swoje rozwiązanie i uruchamiaj testy MyTestMethod i MyTestMethod2.

> [!IMPORTANT]
> Wdróż elementy, takie jak źródła danych, aby były dostępne dla testu w katalogu wdrożenia.

## <a name="see-also"></a>Zobacz też
 [Testowanie jednostkowe kodu](../test/unit-test-your-code.md) [tworzenia i uruchamiania testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [instrukcje: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)
