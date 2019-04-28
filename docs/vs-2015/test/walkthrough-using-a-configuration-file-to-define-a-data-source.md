---
title: 'Przewodnik: Korzystanie z pliku konfiguracji do określania źródła danych | Dokumentacja firmy Microsoft'
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7dde910c5622a67ad002a085ace746ebc68e8857
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439229"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Przewodnik: Korzystanie z pliku konfiguracji do określania źródła danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak korzystających ze źródła danych, zdefiniowane w pliku app.config dla testów jednostkowych. Przedstawiono sposób tworzenia pliku app.config, który definiuje źródła danych, które mogą być używane przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy. Zadania przedstawione w tym przewodniku są następujące:  
  
- Tworzenie pliku app.config.  
  
- Definiowanie sekcji niestandardowej konfiguracji.  
  
- Definiowanie parametrów połączenia.  
  
- Definiowanie źródeł danych.  
  
- Dostęp do danych ze źródłami <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu wykonania instrukcji w tym przewodniku potrzebne są następujące elementy:  
  
- Visual Studio Enterprise  
  
- Program Microsoft Access albo programu Microsoft Excel do dostarczania danych dla co najmniej jednej z metod testowych.  
  
- Rozwiązania programu Visual Studio, która zawiera projekt testowy.  
  
## <a name="create-the-appconfig-file"></a>Tworzenie pliku App.config  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>Aby dodać plik app.config do projektu  
  
1. Jeśli projekt testu zawiera już plik app.config, przejdź do strony [zdefiniować sekcję Konfiguracja niestandardowa](#DefineCustomConfigurationSection).  
  
2. Kliknij prawym przyciskiem myszy projekt testu w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno.  
  
3. Wybierz **pliku konfiguracji aplikacji** szablon i kliknij przycisk **Dodaj**.  
  
## <a name="DefineCustomConfigurationSection"></a> Zdefiniuj sekcji niestandardowej konfiguracji  
 Zapoznaj się z plikiem app.config. Zawiera on co najmniej deklaracji XML i elementu głównego.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać do pliku app.config sekcję Konfiguracja niestandardowa  
  
1. Element główny pliku app.config powinny być `configuration` elementu. Tworzenie `configSections` elemencie `configuration` elementu. `configSections` Powinien być pierwszym elementem w pliku app.config.  
  
2. W ramach `configSections` elementu, Utwórz `section` elementu.  
  
3. W `section` elementu Dodawanie atrybutu o nazwie `name` i przypisać jej wartość równą `microsoft.visualstudio.testtools`. Dodaj inny atrybut o nazwie `type` i przypisać jej wartość równą `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
   `section` Element powinien wyglądać mniej więcej tak:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
> Nazwa zestawu musi odpowiadać kompilacji programu Microsoft Visual Studio .NET Framework, którego używasz. Wybierz wersję odpowiadającą 9.0.0.0 korzystania z programu Visual Studio .NET Framework 3.5. Jeśli używasz programu Visual Studio .NET Framework 2.0, wybierz wersję odpowiadającą 8.0.0.0.  
  
## <a name="define-connection-strings"></a>Zdefiniuj parametry połączenia  
 Parametry połączenia zdefiniować określonych informacji o dostawcy do uzyskiwania dostępu do źródła danych. Parametry połączenia określone w plikach konfiguracji udostępnianie informacji o dostawcy danych wielokrotnego użytku w aplikacji. W tej sekcji utworzysz dwa ciągi połączeń, które będą używane przez źródła danych, które są zdefiniowane w sekcji Konfiguracja niestandardowa.  
  
#### <a name="to-define-connection-strings"></a>Aby zdefiniować parametry połączenia  
  
1. Po `configSections` elementu, Utwórz `connectionStrings` elementu.  
  
2. W ramach `connectionStrings` elementu, utworzysz dwa `add` elementów.  
  
3. W pierwszym `add` elementu, utwórz następujące atrybuty i wartości dla połączenia z bazą danych programu Microsoft Access:  
  
|Atrybut|Wartości|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 W drugim `add` elementu, utwórz następujące atrybuty i wartości dla połączenia do arkusza kalkulacyjnego programu Microsoft Excel:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 `connectionStrings` Element powinien wyglądać mniej więcej tak:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Definiowanie źródeł danych  
 Sekcja źródła danych zawiera cztery atrybuty, które są używane przez silnik testowy można pobrać danych ze źródła danych.  
  
- `name` Określa tożsamość używana przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do określenia danych, które źródło do użycia.  
  
- `connectionString` Określa parametry połączenia, utworzony w poprzedniej sekcji zdefiniować parametry połączenia.  
  
- `dataTableName` Definiuje tabeli lub arkusza, która przechowuje dane do użycia w teście.  
  
- `dataAccessMethod` Definiuje technik do uzyskania dostępu do wartości danych w źródle danych.  
  
  W tej sekcji omówiono definiowanie dwóch źródeł danych do użycia podczas testów jednostkowych.  
  
#### <a name="to-define-data-sources"></a>Aby zdefiniować źródła danych  
  
1. Po `connectionStrings` elementu, Utwórz `microsoft.visualstudio.testtools` elementu. W tej sekcji został utworzony w Definiuj sekcji konfiguracji niestandardowych.  
  
2. W ramach `microsoft.visualstudio.testtools` elementu, Utwórz `dataSources` elementu.  
  
3. W ramach `dataSources` elementu, utworzysz dwa `add` elementów.  
  
4. W pierwszym `add` elementu, utwórz następujące atrybuty i wartości dla źródła danych Microsoft Access:  
  
|Atrybut|Wartości|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 W drugim `add` elementu, utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Excel:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 `microsoft.visualstudio.testtools` Element powinien wyglądać mniej więcej tak:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Plik app.config końcowy powinien wyglądać mniej więcej tak:  
  
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
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego za pomocą źródeł danych, zdefiniowane w pliku app.config  
 Skoro zdefiniowano pliku app.config, utworzysz test jednostkowy, który korzysta z danych znajdujących się w źródłach danych, które są zdefiniowane w pliku app.config. W tej sekcji obejmuje następujące czynności:  
  
- Tworzenie źródła danych znaleziona w pliku app.config.  
  
- Używanie źródeł danych, w dwie metody testowe są porównywane wartości w poszczególnych źródeł danych.  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych Microsoft Access  
  
1. Utwórz bazę danych Microsoft Access o nazwie `testdatasource.accdb`.  
  
2. Utwórz tabelę i nadaj mu nazwę `MyDataTable` w `testdatasource.accdb`.  
  
3. Utwórz dwa pola w `MyDataTable` o nazwie `Arg1` i `Arg2` przy użyciu `Number` typu danych.  
  
4. Dodaj jednostki pięć `MyDataTable` z następującymi wartościami dla `Arg1` i `Arg2`odpowiednio: (10,50), (3,2) (6,0) (0,8) i (12312,1000).  
  
5. Zapisz i zamknij bazy danych.  
  
6. Zmień parametry połączenia, aby wskazać lokalizację bazy danych. Zmień wartość właściwości `Data Source` uwzględnienie lokalizacji bazy danych.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel  
  
1. Utwórz arkusz kalkulacyjny programu Excel o nazwie `data.xlsx`.  
  
2. Utwórz arkusz o nazwie `Sheet1` Jeśli go jeszcze nie istnieje w `data.xlsx`.  
  
3. Utwórz dwa nagłówki kolumn i nazwij je `Val1` i `Val2` w `Sheet1`.  
  
4. Dodaj jednostki pięć `Sheet1` z następującymi wartościami dla `Val1` i `Val2`odpowiednio: (1,1), (2, 2,) (3,3) (4,4) i (5,0).  
  
5. Zapisz i zamknij arkusza kalkulacyjnego.  
  
6. Zmień parametry połączenia, aby wskazać lokalizację arkusza kalkulacyjnego. Zmień wartość właściwości `dbq` do uwzględnienia lokalizacji w arkuszu kalkulacyjnym.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć test jednostki za pomocą źródeł danych w pliku app.config  
  
1. Dodaj test jednostkowy do projektu testowego.  
  
     Aby uzyskać więcej informacji, zobacz [tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2. Zastąp zawartość automatycznego generowania testu jednostkowego z następującym kodem:  
  
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
  
3. Sprawdź atrybutów elementu DataSource. Zwróć uwagę, nazwy ustawień z pliku app.config.  
  
4. Skompiluj rozwiązanie i uruchomić testy MyTestMethod i MyTestMethod2.  
  
> [!IMPORTANT]
> Wdróż elementy, takie jak źródła danych, tak aby były dostępne dla testów w katalogu wdrożenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)   
 [Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Instrukcje: tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)
