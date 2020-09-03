---
title: Tworzenie kodowanego testu interfejsu użytkownika opartego na danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1db35e1eb98ad23a4414a48389092a3b05485527
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851856"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika opartego na danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby przetestować inne warunki, można uruchomić testy wiele razy z różnymi wartościami parametrów. Kodowane testy interfejsu użytkownika obsługujące dane są wygodnym sposobem wykonania tej czynności. Możesz definiować wartości parametrów w źródle danych, a każdy wiersz w źródle danych jest iteracją kodowanego testu interfejsu użytkownika. Ogólny wynik testu będzie oparty na wynikach dla wszystkich iteracji. Na przykład jeśli jedna iteracja testu nie powiedzie się, ogólny wynik testu to niepowodzenie.

 **Wymagania**

- Visual Studio Enterprise

## <a name="create-a-data-driven-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika opartego na danych
 Ten przykład tworzy kodowany test interfejsu użytkownika, który jest uruchamiany w aplikacji kalkulatora systemu Windows. Dodaje dwa liczby jednocześnie i używa potwierdzenia do sprawdzenia, czy suma jest poprawna. Następnie potwierdzenie i wartości parametrów dla dwóch liczb są kodowane jako dane i przechowywane w pliku z wartościami rozdzielanymi przecinkami (CSV).

#### <a name="step-1---create-a-coded-ui-test"></a>Krok 1. Tworzenie kodowanego testu interfejsu użytkownika

1. Utwórz projekt.

     ![Utwórz projekt kodowanego testu interfejsu użytkownika](../test/media/cuit-datadriven.png "CUIT_dataDriven_")

2. Wybierz, aby zarejestrować akcje.

     ![Wybierz, aby zarejestrować akcje](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")

3. Otwórz aplikację Kalkulator i Rozpocznij nagrywanie testu.

     ![Rejestruj akcje](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")

4. Dodaj 1 plus 2, Wstrzymaj Rejestrator i Wygeneruj metodę testową. Później zamienimy wartości tych danych wejściowych użytkownika na wartości z pliku danych.

     ![Generuj metodę testową](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")

     Zamknij Konstruktor testów. Metoda jest dodawana do testu:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();

    }
    ```

5. Użyj `AddNumbers()` metody, aby sprawdzić, czy testy są wykonywane. Umieść kursor w pokazanej powyżej metodzie testowej, otwórz menu kontekstowe i wybierz polecenie **Uruchom testy**. (Skrót klawiaturowy: Ctrl + R, T).

     Wynik testu, który pokazuje, czy w oknie Eksplorator testów jest wyświetlany test zakończony powodzeniem lub niepowodzeniem. Aby otworzyć okno Eksplorator testów, z menu **test** wybierz pozycję **Windows** , a następnie wybierz **Eksplorator testów**.

6. Ze względu na to, że źródło danych może być również używane dla wartości parametrów potwierdzenia — które są używane przez test w celu sprawdzenia oczekiwanych wartości — Dodajmy potwierdzenie, aby sprawdzić, czy suma dwóch numerów jest poprawna. Umieść kursor w pokazanej powyżej metodzie testowej, otwórz menu kontekstowe i wybierz polecenie **Generuj kod dla kodowanego testu interfejsu**użytkownika, a następnie **Użyj konstruktora KODOWANEGO testu interfejsu użytkownika**.

     Mapuj kontrolkę tekstową na Kalkulator, który wyświetla sumę.

     ![Mapowanie kontrolki tekstowej interfejsu użytkownika](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")

7. Dodaj potwierdzenie, które sprawdza, czy wartość sumy jest poprawna. Wybierz właściwość **DisplayText** , która ma wartość **3** , a następnie wybierz pozycję **Dodaj potwierdzenie**. Użyj **AreEqual** komparator i sprawdź, czy wartość porównania to **3**.

     ![Skonfiguruj potwierdzenie](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")

8. Po skonfigurowaniu potwierdzenia Wygeneruj ponownie kod z konstruktora. Spowoduje to utworzenie nowej metody weryfikacji.

     ![Generowanie metody potwierdzenia](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")

     Ponieważ `ValidateSum` metoda weryfikuje wyniki `AddNumbers` metody, przenieś ją na dół bloku kodu.

    ```csharp
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }
    ```

9. Sprawdź, czy test jest uruchamiany przy użyciu `ValidateSum()` metody. Umieść kursor w pokazanej powyżej metodzie testowej, otwórz menu kontekstowe i wybierz polecenie **Uruchom testy**. (Skrót klawiaturowy: Ctrl + R, T).

     W tym momencie wszystkie wartości parametrów są zdefiniowane w metodach jako stałe. Następnie Utwórzmy zestaw danych, aby umożliwić nasze testy oparte na danych.

#### <a name="step-2---create-a-data-set"></a>Krok 2. Tworzenie zestawu danych

1. Dodaj plik tekstowy do projektu dataDrivenSample o nazwie `data.csv` .

     ![Dodawanie pliku wartości rozdzielanych przecinkami do projektu](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")

2. Wypełnij plik CSV następującymi danymi:

    |Num1|Num2|Suma|
    |----------|----------|---------|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Po dodaniu danych plik powinien wyglądać następująco:

     ![Wypełnij. Plik CSV z danymi](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")

3. Ważne jest, aby zapisać plik CSV przy użyciu poprawnego kodowania. W menu **plik** wybierz pozycję **Zaawansowane opcje zapisywania** i wybierz pozycję **Unicode (UTF-8 bez podpisu) — strona kodowa 65001** jako kodowanie.

4. Plik CSV musi być skopiowany do katalogu wyjściowego lub test nie może zostać uruchomiony. Użyj okno Właściwości, aby je skopiować.

     ![Wdróż. Plik CSV](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")

     Teraz, po utworzeniu zestawu danych, powiążemy dane z testem.

#### <a name="step-3--add-data-source-binding"></a>Krok 3 — Dodawanie powiązania źródła danych

1. Aby powiązać źródło danych, Dodaj `DataSource` atrybut w istniejącym `[TestMethod]` atrybucie, który jest bezpośrednio powyżej metody testowej.

    ```
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();

    }

    ```

     Źródło danych jest teraz dostępne do użycia w tej metodzie testowej.

    > [!TIP]
    > Zobacz [Przykłady atrybutów źródła danych](#CreateDataDrivenCUIT_QA_DataSourceAttributes) w sekcji Q & sekcję, aby poznać przykłady użycia innych typów źródeł danych, takich jak XML, SQL Express i Excel.

2. Uruchom test.

     Zwróć uwagę, że test jest wykonywany przez trzy iteracje. Wynika to z faktu, że powiązane źródło danych zawiera trzy wiersze danych. Należy jednak zauważyć, że test nadal używa wartości parametrów stałych i dodaje 1 + 2 z sumą wartości 3 za każdym razem.

     Następnie skonfigurujemy test tak, aby korzystał z wartości w pliku źródła danych.

#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>Krok 4 — Używanie danych w kodowanym teście interfejsu użytkownika

1. Dodaj `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` na początku pliku CodedUITest.cs:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2. Dodaj `TestContext.DataRow[]` w `CodedUITestMethod1()` metodzie, która będzie stosować wartości ze źródła danych. Wartości źródła danych zastępują stałe przypisane do kontrolek UIMap przy użyciu kontrolek `SearchProperties` :

    ```
    public void CodedUITestMethod1()
    {

        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();
        this.UIMap.ValidateSum();

    }
    ```

     Aby ustalić, które właściwości wyszukiwania mają być używane do kodowania danych, użyj edytora kodowanego testu interfejsu użytkownika.

    - Otwórz plik UIMap. UITest.

         ![Otwórz Edytor kodowanego testu interfejsu użytkownika](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")

    - Wybierz akcję interfejsu użytkownika i obserwuj odpowiednie mapowanie formantów interfejsu użytkownika. Zwróć uwagę, jak mapowanie odpowiada kodowi, na przykład `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button` .

         ![Użyj edytora kodowanego testu interfejsu użytkownika, aby pomóc w kodzie](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")

    - W oknie Właściwości Otwórz **Właściwości wyszukiwania**. Wartość **nazwy** właściwości wyszukiwania to to, co jest manipulowane w kodzie przy użyciu źródła danych. Na przykład, `SearchProperties` jest przypisywanych wartości w pierwszej kolumnie każdego wiersza danych: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();` . Dla trzech iteracji ten test zmieni wartość **Nazwa** dla właściwości Wyszukaj na 3, a następnie 5 i finally 6.

         ![Użyj właściwości wyszukiwania, aby pomóc w kodowaniu](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")

3. Zapisz rozwiązanie.

#### <a name="step-5--run-the-data-driven-test"></a>Krok 5 — Uruchamianie testu opartego na danych

1. Sprawdź, czy test jest teraz sterowany danymi, ponownie uruchamiając test.

    Należy sprawdzić przebieg testu przez trzy iteracje przy użyciu wartości z pliku CSV. Walidacja powinna również być poprawna, a test powinien być wyświetlany jako zakończono w Eksploratorze testów.

   **Wskazówki**

   Aby uzyskać dodatkowe informacje, zobacz [testowanie ciągłego dostarczania za pomocą programu Visual studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx) i [testowanie ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 5: Automatyzowanie testów systemowych](https://msdn.microsoft.com/library/jj159335.aspx)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> Jakie są atrybuty źródła danych dla innych typów źródeł danych, takich jak SQL Express czy XML?
 W poniższej tabeli można użyć ciągów przykładowego źródła danych, kopiując je do kodu i wprowadzając niezbędne dostosowania.

 **Typy i atrybuty źródła danych**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Przypadek testowy w Team Foundation Server

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>P: Czy można używać testów opartych na danych w mojej aplikacji Windows Phone?
 **Odpowiedź:** tak. Kodowane testy interfejsu użytkownika oparte na danych dla Windows Phone są definiowane przy użyciu atrybutu DataRow dla metody testowej. W poniższym przykładzie x i y używają wartości 1 i 2 dla pierwszej iteracji i-1 i-2 dla drugiej iteracji testu.

```
[DataRow(1, 2, DisplayName = "Add positive numbers")]
[DataRow(-1, -2, DisplayName = "Add negative numbers")]
[TestMethod]
public void DataDrivingDemo_MyTestMethod(int x, int y)

```

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap. Designer?
 Odp **.:** Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną nadpisywane przy każdym wygenerowaniu kodu za pomocą konstruktora kodowanego testu interfejsu użytkownika UIMap. W tym przykładzie i w większości przypadków zmiany kodu są konieczne, aby umożliwić testowi użycie źródła danych do pliku kodu źródłowego testu (czyli CodedUITest1.cs).

 Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.

## <a name="see-also"></a>Zobacz też

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
