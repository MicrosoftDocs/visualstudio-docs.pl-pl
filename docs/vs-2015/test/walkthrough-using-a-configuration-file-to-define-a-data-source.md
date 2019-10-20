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
ms.openlocfilehash: 64ac9835a085908645713f95f1f07c283d807852
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657056"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Wskazówki: korzystanie z pliku konfiguracji do określania źródła danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak używać źródła danych zdefiniowanego w pliku App. config do testowania jednostkowego. Dowiesz się, jak utworzyć plik App. config, który definiuje źródło danych, które może być używane przez klasę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>. Zadania przedstawione w tym instruktażu obejmują następujące elementy:

- Tworzenie pliku App. config.

- Definiowanie sekcji konfiguracji niestandardowej.

- Definiowanie parametrów połączenia.

- Definiowanie źródeł danych.

- Uzyskiwanie dostępu do źródeł danych przy użyciu klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

## <a name="prerequisites"></a>Wymagania wstępne
 W celu wykonania instrukcji w tym przewodniku potrzebne są następujące elementy:

- Visual Studio Enterprise

- Microsoft Access lub Microsoft Excel, aby dostarczyć dane dla co najmniej jednej z metod testowych.

- Rozwiązanie programu Visual Studio, które zawiera projekt testowy.

## <a name="create-the-appconfig-file"></a>Utwórz plik App. config

#### <a name="to-add-an-appconfig-file-to-the-project"></a>Aby dodać plik App. config do projektu

1. Jeśli projekt testowy zawiera już plik App. config, przejdź do [sekcji Definiowanie konfiguracji niestandardowej](#DefineCustomConfigurationSection).

2. Kliknij prawym przyciskiem myszy projekt testowy w **Eksplorator rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

     Zostanie otwarte okno **Dodaj nowy element** .

3. Wybierz szablon **pliku konfiguracji aplikacji** , a następnie kliknij przycisk **Dodaj**.

## <a name="DefineCustomConfigurationSection"></a>Definiowanie sekcji konfiguracji niestandardowej
 Zapoznaj się z plikiem app. config. Zawiera co najmniej deklarację XML i element główny.

#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać sekcję Konfiguracja niestandardowa do pliku App. config

1. Element główny pliku App. config powinien być elementem `configuration`. Utwórz element `configSections` w elemencie `configuration`. @No__t_0 powinien być pierwszym elementem w pliku App. config.

2. W elemencie `configSections` Utwórz element `section`.

3. W `section` elementu Dodaj atrybut o nazwie `name` i przypisz go `microsoft.visualstudio.testtools` wartości równej. Dodaj inny atrybut o nazwie `type` i przypisz mu wartość równą `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

   Element `section` powinien wyglądać podobnie do tego:

```
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Nazwa zestawu musi być zgodna z Microsoft Visual Studio .NET Framework kompilacją, która jest używana. Ustaw wersję na 9.0.0.0, jeśli używasz programu Visual Studio .NET Framework 3,5. Jeśli używasz programu Visual Studio .NET Framework 2,0, ustaw wersję na 8.0.0.0.

## <a name="define-connection-strings"></a>Definiowanie parametrów połączenia
 Parametry połączenia definiują informacje specyficzne dla dostawcy na potrzeby uzyskiwania dostępu do źródeł danych. Parametry połączenia zdefiniowane w plikach konfiguracji zapewniają informacje o dostawcy danych wielokrotnego użytku w aplikacji. W tej sekcji utworzysz dwa parametry połączenia, które będą używane przez źródła danych, które są zdefiniowane w sekcji Konfiguracja niestandardowa.

#### <a name="to-define-connection-strings"></a>Aby zdefiniować parametry połączenia

1. Po elemencie `configSections` Utwórz element `connectionStrings`.

2. W elemencie `connectionStrings` Utwórz dwa `add` elementy.

3. W pierwszym `add` elementu Utwórz następujące atrybuty i wartości dla połączenia z bazą danych programu Microsoft Access:

|Atrybut|Wartości|
|---------------|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

 W drugim elemencie `add` Utwórz następujące atrybuty i wartości dla połączenia z arkuszem kalkulacyjnym programu Microsoft Excel:

|||
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

 Element `connectionStrings` powinien wyglądać podobnie do tego:

```
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definiowanie źródeł danych
 Sekcja źródła danych zawiera cztery atrybuty, które są używane przez aparat testowy do pobierania danych ze źródła danych.

- `name` definiuje tożsamość używaną przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do określenia źródła danych, które ma być używane.

- `connectionString` identyfikuje parametry połączenia utworzone w poprzedniej sekcji Definiowanie parametrów połączenia.

- `dataTableName` definiuje tabelę lub arkusz, który przechowuje dane do użycia w teście.

- `dataAccessMethod` definiuje technikę uzyskiwania dostępu do wartości danych w źródle danych.

  W tej sekcji zdefiniujesz dwa źródła danych, które zostaną użyte w teście jednostkowym.

#### <a name="to-define-data-sources"></a>Aby zdefiniować źródła danych

1. Po elemencie `connectionStrings` Utwórz element `microsoft.visualstudio.testtools`. Ta sekcja została utworzona w sekcji Definiowanie konfiguracji niestandardowej.

2. W elemencie `microsoft.visualstudio.testtools` Utwórz element `dataSources`.

3. W elemencie `dataSources` Utwórz dwa `add` elementy.

4. W pierwszym `add` elementu Utwórz następujące atrybuty i wartości dla źródła danych Microsoft Access:

|Atrybut|Wartości|
|---------------|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

 W drugim elemencie `add` Utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Excel:

|||
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

 Element `microsoft.visualstudio.testtools` powinien wyglądać podobnie do tego:

```
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

 Końcowy plik App. config powinien wyglądać podobnie do tego:

```
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

## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego przy użyciu źródeł danych zdefiniowanych w pliku App. config
 Teraz, gdy został zdefiniowany plik App. config, utworzysz test jednostkowy, który używa danych znajdujących się w źródłach danych, które są zdefiniowane w pliku App. config. W tej sekcji będziemy:

- Utwórz źródła danych znajdujące się w pliku App. config.

- Użyj źródeł danych w dwóch metodach testowych, które porównują wartości w każdym źródle danych.

#### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych programu Microsoft Access

1. Utwórz bazę danych programu Microsoft Access o nazwie `testdatasource.accdb`.

2. Utwórz tabelę i nadaj jej nazwę `MyDataTable` w `testdatasource.accdb`.

3. Utwórz dwa pola w `MyDataTable` o nazwie `Arg1` i `Arg2` przy użyciu `Number` typu danych.

4. Dodaj pięć jednostek do `MyDataTable` z następującymi wartościami dla `Arg1` i `Arg2` odpowiednio: (10, 50), (3, 2), (6, 0), (0, 8) i (12312, 1000).

5. Zapisz i Zamknij bazę danych.

6. Zmień parametry połączenia tak, aby wskazywały lokalizację bazy danych. Zmień wartość `Data Source`, aby odzwierciedlić lokalizację bazy danych.

#### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel

1. Utwórz arkusz kalkulacyjny programu Microsoft Excel o nazwie `data.xlsx`.

2. Utwórz arkusz o nazwie `Sheet1`, jeśli jeszcze nie istnieje w `data.xlsx`.

3. Utwórz dwa nagłówki kolumn i nadaj im nazwę `Val1` i `Val2` w `Sheet1`.

4. Dodaj pięć jednostek do `Sheet1` z następującymi wartościami dla `Val1` i `Val2` odpowiednio: (1, 1), (2, 2), (3, 3), (4, 4) i (5, 0).

5. Zapisz i zamknij arkusz kalkulacyjny.

6. Zmień parametry połączenia tak, aby wskazywały lokalizację arkusza kalkulacyjnego. Zmień wartość `dbq`, aby odzwierciedlała lokalizację arkusza kalkulacyjnego.

#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć test jednostkowy przy użyciu źródeł danych App. config

1. Dodaj test jednostkowy do projektu testowego.

     Aby uzyskać więcej informacji, zobacz [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).

2. Zastąp automatycznie wygenerowaną zawartość testu jednostkowego następującym kodem:

    ```
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

3. Przejrzyj atrybuty DataSource. Zwróć uwagę na nazwy ustawień z pliku App. config.

4. Kompiluj swoje rozwiązanie i uruchamiaj testy MyTestMethod i MyTestMethod2.

> [!IMPORTANT]
> Wdróż elementy, takie jak źródła danych, aby były dostępne dla testu w katalogu wdrożenia.

## <a name="see-also"></a>Zobacz też
 [Testowanie jednostkowe kodu](../test/unit-test-your-code.md) [tworzenia i uruchamiania testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [instrukcje: Tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)
