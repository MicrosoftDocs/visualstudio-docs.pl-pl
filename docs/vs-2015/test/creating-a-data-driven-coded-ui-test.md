---
title: Tworzenie na podstawie danych kodowanego testu interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: 58
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 71c08c78d67f65ec69a982ce431a64ec1c620d27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755373"
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika opartego na danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na potrzeby testowania różnych warunków, można uruchomić testy wiele razy z wartościami różnych parametrów. Oparte na danych coded UI testy są wygodny sposób, aby to zrobić. Określ wartości parametrów w źródle danych, a każdy wiersz w źródle danych jest iteracji kodowanego testu interfejsu użytkownika. Ogólny wynik testu będzie zależeć od wyniku dla wszystkich iteracji. Na przykład w przypadku niepowodzenia jednej iteracji testu, ogólny wynik testu jest błąd.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="create-a-data-driven-coded-ui-test"></a>Tworzenie opartych na danych kodowanego testu interfejsu użytkownika  
 Ten przykład umożliwia utworzenie kodowanego testu interfejsu użytkownika, uruchamiane w aplikacji Windows kalkulatora. Je ze sobą dodaje dwie liczby i używa potwierdzenie, aby sprawdzić, czy suma jest poprawna. Następnie potwierdzenie i wartości parametrów dla dwóch liczb są kodowane staje się opartych na danych i przechowywane w pliku wartości rozdzielanych przecinkami (CSV).  
  
#### <a name="step-1---create-a-coded-ui-test"></a>Krok 1 — Tworzenie kodowanego testu interfejsu użytkownika  
  
1.  Utwórz projekt.  
  
     ![Utwórz projekt kodowanego testu interfejsu użytkownika](../test/media/cuit-datadriven.png "CUIT_dataDriven_")  
  
2.  Możliwość rejestrowania akcji.  
  
     ![Wybierz do rejestrowania akcji](../test/media/cuit-datadriven-generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")  
  
3.  Otwórz aplikację Kalkulator i Rozpocznij nagrywanie testu.  
  
     ![Rejestruj akcje](../test/media/cuit-datadriven-cuitbuilder.png "CUIT_dataDriven_CUITBuilder")  
  
4.  Dodaj 1 i 2, Wstrzymaj Rejestrator i generować metodę testową. Firma Microsoft będzie później zastąpić wartości tych danych wejściowych użytkownika przy użyciu wartości z pliku danych.  
  
     ![Metoda testowa Genetate](../test/media/cuit-datadriven-cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")  
  
     Zamknąć Konstruktora testu. Metoda jest dodawana do testu:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
  
    }  
    ```  
  
5.  Użyj `AddNumbers()` metodę, aby sprawdzić, że test jest uruchamiany. Umieść kursor w metodzie testowej, pokazanych powyżej, otwórz menu kontekstowe i wybierz **Uruchom testy**. (Skrót klawiaturowy: Ctrl + R, T).  
  
     Wynik testu, który pokazuje, jeśli test zakończony powodzeniem lub niepowodzeniem są wyświetlane w oknie Eksploratora testów. Aby otworzyć okno Eksploratora testów z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksplorator testów**.  
  
6.  Ponieważ źródła danych można również o wprowadzenie wartości parametrów potwierdzenie — które są używane przez test, aby zweryfikować oczekiwane wartości — Dodajmy potwierdzenie można zweryfikować, czy sumę dwóch liczb jest poprawna. Umieść kursor w metodzie testowej, pokazanych powyżej, otwórz menu kontekstowe i wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**, a następnie **Użyj Konstruktor kodowanego testu IU**.  
  
     Mapowanie kontrolki tekstu w kalkulatorze, który wyświetla sumę.  
  
     ![Mapowanie interfejsu użytkownika kontrolki tekstu](../test/media/cuit-datadriven-addassertion.png "CUIT_dataDriven_AddAssertion")  
  
7.  Dodaj potwierdzenie, która weryfikuje, czy wartość sumy jest poprawna. Wybierz **Wyświetlany_tekst** właściwość, która ma wartość **3** , a następnie wybierz **Dodaj potwierdzenie**. Użyj **AreEqual** komparator i sprawdź, czy jest porównywana wartość **3**.  
  
     ![Konfigurowanie potwierdzenia](../test/media/cuit-datadriven-builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")  
  
8.  Po skonfigurowaniu potwierdzenie, ponownie generuje kod z konstruktora. Spowoduje to utworzenie nowej metody dla weryfikacji.  
  
     ![Generowanie metody asercji](../test/media/cuit-datadriven-assertiongencode.png "CUIT_dataDriven_AssertionGenCode")  
  
     Ponieważ `ValidateSum` metoda sprawdza wyniki `AddNumbers` metody, przenieś go do dolnej części bloku kodu.  
  
    ```csharp  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
9. Sprawdź, czy test działa przy użyciu `ValidateSum()` metody. Umieść kursor w metodzie testowej, pokazanych powyżej, otwórz menu kontekstowe i wybierz **Uruchom testy**. (Keyboard shortcut:Ctrl + R, T).  
  
     W tym momencie wszystkich wartości parametrów są definiowane w ich metod jako stałe. Następnie utworzymy zestaw danych umożliwiają naszym teście opartych na danych.  
  
#### <a name="step-2---create-a-data-set"></a>Krok 2 — Tworzenie zestawu danych  
  
1.  Dodaj plik tekstowy do projektu dataDrivenSample o nazwie `data.csv`.  
  
     ![Dodaj z pliku wartości rozdzielonych przecinkami do projektu](../test/media/cuit-datadriven-addcsvfile.png "CUIT_dataDriven_AddCSVFile")  
  
2.  Wypełnij pliku CSV przy użyciu następujących danych:  
  
    |Num1|Num2|Suma|  
    |----------|----------|---------|  
    |3|4|7|  
    |5|6|11|  
    |6|8|14|  
  
     Po dodaniu danych, plik powinien wyglądać następująco:  
  
     ![Wypełnij. Plik CSV z danymi](../test/media/cuit-datadriven-adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")  
  
3.  Należy zapisać plik CSV przy użyciu kodowania poprawne. Na **pliku** menu, wybierz **zaawansowane opcje zapisywania** i wybierz polecenie **Unicode (UTF-8 bez podpisu)-strona kodowa 65001** jako kodowania.  
  
4.  Plik CSV, muszą zostać skopiowane do katalogu wyjściowego lub nie można uruchomić testu. Użyj okna właściwości, aby go skopiować.  
  
     ![Wdrażanie. Plik CSV](../test/media/cuit-datadriven-deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")  
  
     Teraz, gdy zestaw danych utworzony, powiążmy danych do testu.  
  
#### <a name="step-3--add-data-source-binding"></a>Krok 3 — Dodawanie powiązania źródła danych  
  
1.  Aby powiązać ze źródłem danych, należy dodać `DataSource` atrybut wewnątrz istniejącego `[TestMethod]` atrybut, który jest od razu powyżej metody testowej.  
  
    ```  
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
  
    ```  
  
     Źródło danych jest teraz dostępna do użycia w tej metodzie testowej.  
  
    > [!TIP]
    >  Zobacz [przykłady atrybut źródła danych](#CreateDataDrivenCUIT_QA_DataSourceAttributes) w funkcji pytań i odpowiedzi dotyczącej przykłady użycia innych typów źródeł danych, takich jak XML, SQL Express i programu Excel.  
  
2.  Uruchom test.  
  
     Należy zauważyć, że test jest uruchamiany za pomocą trzech iteracji. Jest to spowodowane źródło danych, który był powiązany zawiera trzy wiersze danych. Jednak zauważysz również, że test jest nadal przy użyciu wartości parametru o stałej i polega na dodaniu 1 + 2 z sumą 3 każdorazowo.  
  
     Następnie skonfigurujemy test, aby użyć wartości z pliku źródła danych.  
  
#### <a name="step-4--use-the-data-in-the-coded-ui-test"></a>Krok 4 — użyć danych w kodowanym teście interfejsu użytkownika  
  
1.  Dodaj `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` na początku pliku CodedUITest.cs:  
  
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
  
2.  Dodaj `TestContext.DataRow[]` w `CodedUITestMethod1()` metody, które będą miały zastosowanie wartości ze źródła danych. Wartości źródła danych Zastąp stałe przypisany do kontrolki do UIMap za pomocą kontrolek na `SearchProperties`:  
  
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
  
     Aby ustalić właściwości wyszukiwania, które o kodowaniu dane, użyj edytora kodowanego testu interfejsu użytkownika.  
  
    -   Otwórz plik UIMap.uitest.  
  
         ![Otwórz Edytor testu kodowanego interfejsu użytkownika](../test/media/cuit-datadriven-opentesteditor.png "CUIT_dataDriven_OpenTestEditor")  
  
    -   Wybierz akcję interfejsu użytkownika i sprawdź odpowiednie mapowanie kontrolek interfejsu użytkownika. Zwróć uwagę, jak mapowanie odnosi się do kodu, na przykład `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.  
  
         ![Użyj edytora kodowanego testu interfejsu użytkownika, aby uzyskać pomoc przy użyciu kodu](../test/media/cuit-datadriven-testeditor.png "CUIT_dataDriven_TestEditor")  
  
    -   W oknie dialogowym właściwości Otwórz **wyszukującą**. Właściwości wyszukiwania **nazwa** wartość to, co jest podlegający manipulowaniu w kodzie przy użyciu źródła danych. Na przykład `SearchProperties` trwa przypisywanie wartości w pierwszej kolumnie każdy wiersz danych: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Dla trzech iteracji tego testu spowoduje zmianę **nazwa** wartości dla właściwości wyszukiwania, aby 3, a następnie 5 i na koniec 6.  
  
         ![Użyj właściwości wyszukiwania, aby uzyskać pomoc w kodowaniu](../test/media/cuit-datadriven-searchproperties.png "CUIT_dataDriven_SearchProperties")  
  
3.  Zapisywanie rozwiązania.  
  
#### <a name="step-5--run-the-data-driven-test"></a>Krok 5 — Uruchamianie testu opartego na danych  
  
1. Sprawdź, czy test jest teraz opartych na danych, ponownie uruchamiając test.  
  
    Powinien zostać wyświetlony testu za pomocą trzech iteracji, używając wartości z pliku CSV. Sprawdzanie poprawności powinno działać tak dobrze w i testu powinien być wyświetlany jako zakończony powodzeniem w Eksploratorze testów.  
  
   **Wskazówki**  
  
   Aby uzyskać więcej informacji, zobacz [testowanie dostarczania ciągłego w programie Visual Studio 2012 – rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188) i [testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
###  <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> Co to są atrybuty źródła danych dla innych typów źródła danych, takich jak program SQL Express lub XML?  
 W poniższej tabeli można użyć parametry źródła danych przykładowych, kopiując je do kodu i dokonując wymaganych dostosowaniach.  
  
 **Typy źródeł danych i atrybuty**  
  
-   CSV  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`  
  
-   Excel  
  
     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`  
  
-   Przypadek testowy w programie Team Foundation Server  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`  
  
-   XML  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`  
  
-   SQL Express  
  
     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`  
  
### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>PYT.: W mojej aplikacji Windows Phone można używać testów opartych na danych?  
 **ODP.:** Tak. Oparte na danych kodowanych testów interfejsu użytkownika dla Windows Phone są definiowane dla metody testowej przy użyciu atrybutu wiersza danych. W poniższym przykładzie, x i y Użyj wartości 1 i 2 dla pierwszej iteracji i -1 -2 dla drugiego iteracji testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>PYT.: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?  
 **ODP.:** Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. W tym przykładzie i w większości przypadków zmiany kodu wymaganego do włączenia testów korzystających ze źródła danych może przyjąć pliku z kodem źródłowym testu (czyli CodedUITest1.cs).  
  
 Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
