---
title: Samouczek testu kodowego interfejsu użytkownika oparty na danych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ada1f297bbb30fbe636042c87aae42849c1b6b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595361"
---
# <a name="create-a-data-driven-coded-ui-test"></a>Tworzenie kodowego testu interfejsu użytkownika opartego na danych

Aby przetestować różne warunki, można uruchomić testy wiele razy z różnymi wartościami parametrów. Oparte na danych kodowane testy interfejsu użytkownika są wygodnym sposobem, aby to zrobić. Definiujesz wartości parametrów w źródle danych, a każdy wiersz w źródle danych jest iteracją kodowany test interfejsu użytkownika. Ogólny wynik testu będzie oparty na wyniku dla wszystkich iteracji. Na przykład jeśli jedna iteracja testu nie powiedzie się, ogólny wynik testu jest niepowodzeniem.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise
- Składnik testu kodowany interfejs użytkownika

## <a name="create-a-test-project"></a>Tworzenie projektu testowego

W tym przykładzie utworzy się kodowany test interfejsu użytkownika, który działa w aplikacji Kalkulator systemu Windows. Dodaje dwie liczby razem i używa potwierdzenia, aby sprawdzić, czy suma jest poprawna. Następnie wartości potwierdzenia i parametrów dla dwóch liczb są kodowane tak, aby stały się oparte na danych i przechowywane w pliku wartości oddzielonej przecinkami (*csv).*

### <a name="step-1---create-a-coded-ui-test"></a>Krok 1 - Tworzenie kodowany test interfejsu użytkownika

1. Tworzenie projektu.

    ![Tworzenie zakodowany projekt testowy interfejsu użytkownika](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **projektu testu kodowany** interfejs użytkownika, musisz [zainstalować zakodowany składnik testu interfejsu użytkownika.](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)

2. Wybierz, aby **zarejestrować akcje**.

    ![Wybierz rejestrowanie akcji](../test/media/cuit_datadriven_generatecodedialog.png)

3. Otwórz aplikację kalkulatora i rozpocznij nagrywanie testu.

    ![Rejestrowanie akcji](../test/media/cuit_datadriven_cuitbuilder.png)

4. Dodaj 1 plus 2, wstrzymaj nagrywarkę i wygeneruj metodę testową. Później zastąpimy wartości tego wkładu użytkownika wartościami z pliku danych.

    ![Generowanie metody testowej](../test/media/cuit_datadriven_cuitbuildergencode.png)

    Zamknij konstruktora testów. Metoda jest dodawana do testu:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. Użyj `AddNumbers()` metody, aby sprawdzić, czy test jest uruchamiany. Umieść kursor w metodzie testowej pokazanej powyżej, otwórz menu po kliknięciu prawym przyciskiem myszy i wybierz polecenie **Uruchom testy**. (Skrót klawiaturowy: **Ctrl**+**R**,**T**).

    Wynik testu, który pokazuje, czy test przeszedł lub nie powiodło się jest wyświetlany w oknie **Eksploratora testów.** Aby otworzyć okno Eksploratora testów, z menu **Testuj** wybierz polecenie **Windows,** a następnie wybierz pozycję **Eksplorator testów**.

6. Ponieważ źródło danych może być również używane dla wartości parametrów asercji , które są używane przez test do weryfikacji oczekiwanych wartości, dodajmy twierdzenie, aby sprawdzić, czy suma dwóch liczb jest poprawna. Umieść kursor w metodzie testowej pokazanej powyżej, otwórz menu prawym przyciskiem myszy i wybierz polecenie **Generuj kod dla kodowanych testów interfejsu użytkownika,** a następnie **użyj konstruktora kodowanych testów interfejsu użytkownika**.

    Zamapuj formant tekstu w kalkulatorze, który wyświetla sumę.

    ![Mapowanie kontrolki tekstu interfejsu użytkownika](../test/media/cuit_datadriven_addassertion.png)

7. Dodaj twierdzenie, które sprawdza, czy wartość sumy jest poprawna. Wybierz właściwość **DisplayText** o wartości **3,** a następnie wybierz pozycję **Dodaj asercja**. Użyj komparatora **AreEqual** i sprawdź, czy wartość porównania wynosi **3**.

    ![Konfigurowanie potwierdzenia](../test/media/cuit_datadriven_builderaddassertion2.png)

8. Po skonfigurowaniu potwierdzenia ponownie wygeneruj kod z konstruktora. Spowoduje to utworzenie nowej metody sprawdzania poprawności.

    ![Generowanie metody potwierdzenia](../test/media/cuit_datadriven_assertiongencode.png)

    Ponieważ `ValidateSum` metoda sprawdza poprawność `AddNumbers` wyników metody, przenieść go na dół bloku kodu.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. Sprawdź, czy test jest `ValidateSum()` uruchamiany przy użyciu metody. Umieść kursor w metodzie testowej pokazanej powyżej, otwórz menu po kliknięciu prawym przyciskiem myszy i wybierz polecenie **Uruchom testy**. (Skrót klawiaturowy: **Ctrl**+**R**,**T**).

     W tym momencie wszystkie wartości parametrów są definiowane w swoich metodach jako stałe. Następnie utwórzmy zestaw danych, aby nasze dane testowe były oparte na danych.

### <a name="step-2---create-a-data-set"></a>Krok 2 - Tworzenie zestawu danych

1. Dodawanie pliku tekstowego do projektu dataDrivenSample o nazwie *data.csv*.

     ![Dodawanie pliku wartości przecinkowej do projektu](../test/media/cuit_datadriven_addcsvfile.png)

2. Wypełnij plik *csv* następującymi danymi:

    |Liczba 1|Liczba 2|Suma|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     Po dodaniu danych plik powinien być wyświetlany w następujący sposób:

     ![Wypełnianie pliku csv danymi](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. Ważne jest, aby zapisać plik *csv* przy użyciu prawidłowego kodowania. W menu **Plik** wybierz polecenie **Zaawansowane opcje zapisywania** i wybierz pozycję **Unicode (UTF-8 bez podpisu) - Codepage 65001** jako kodowanie.

4. Plik *csv* musi zostać skopiowany do katalogu wyjściowego lub nie można uruchomić testu. Użyj okna **Właściwości,** aby go skopiować.

     ![Wdrażanie pliku csv](../test/media/cuit_datadriven_deploycsvfile.png)

     Teraz, gdy mamy utworzony zestaw danych, powiążmy dane z testem.

### <a name="step-3---add-data-source-binding"></a>Krok 3 - Dodawanie powiązania źródła danych

1. Aby powiązać źródło danych, należy dodać `[TestMethod]` atrybut w istniejącym `DataSource` atrybucie, który znajduje się bezpośrednio powyżej metody testowej.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     Źródło danych jest teraz dostępne do użycia w tej metodzie testowej.

    > [!TIP]
    > Zobacz [przykłady atrybutów źródła danych](#CreateDataDrivenCUIT_QA_DataSourceAttributes) w sekcji Q & A, aby uzyskać próbki korzystania z innych typów źródeł danych, takich jak XML, SQL Express i Excel.

2. Uruchom test.

     Należy zauważyć, że test przebiega przez trzy iteracje. Jest to spowodowane źródło danych, który został powiązany zawiera trzy wiersze danych. Jednak można również zauważyć, że test jest nadal przy użyciu wartości parametrów stałych i dodaje 1 + 2 z sumą 3 za każdym razem.

     Następnie skonfigurujemy test tak, aby używał wartości w pliku źródła danych.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>Krok 4 - Użyj danych w kodowanym teście interfejsu użytkownika

1. Dodaj `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` do górnej części *pliku CodedUITest.cs:*

    ```csharp
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

2. Dodaj `TestContext.DataRow[]` w `CodedUITestMethod1()` metodzie, która będzie stosować wartości ze źródła danych. Wartości źródła danych zastępują stałe przypisane do formantów UIMap za pomocą formantów: `SearchProperties`

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();
       this.UIMap.UICalculatorWindow.UIItemWindow2.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSumExpectedValues.UIItem3TextDisplayText = TestContext.DataRow["Sum"].ToString();
       this.UIMap.ValidateSum();
    }
    ```

     Aby dowiedzieć się, które właściwości wyszukiwania do kodu danych, należy użyć Edytora testów kodowany interfejsu użytkownika.

    - Otwórz plik *UIMap.uitest.*

         ![Otwórz edytor kodowanych testów interfejsu użytkownika](../test/media/cuit_datadriven_opentesteditor.png)

    - Wybierz akcję interfejsu użytkownika i obserwuj odpowiednie mapowanie sterowania interfejsu użytkownika. Zwróć uwagę, jak mapowanie odpowiada kodowi, `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`na przykład .

         ![Użyj edytora kodowanych testów interfejsu użytkownika, aby pomóc w kodzie](../test/media/cuit_datadriven_testeditor.png)

    - W oknie **Właściwości** otwórz okno **Właściwości wyszukiwania**. Właściwości wyszukiwania **Nazwa** wartość jest to, co jest manipulowane w kodzie przy użyciu źródła danych. Na przykład `SearchProperties` wartości w pierwszej kolumnie każdego wiersza danych `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`są przypisywane: . Dla trzech iteracji ten test zmieni **Name** wartość dla właściwości wyszukiwania do 3, następnie 5 i wreszcie 6.

         ![Używanie właściwości wyszukiwania do pomocy w kodowaniu](../test/media/cuit_datadriven_searchproperties.png)

3. Zapisz rozwiązanie.

### <a name="step-5---run-the-data-driven-test"></a>Krok 5 - Uruchom test oparty na danych

Sprawdź, czy test jest teraz oparty na danych, uruchamiając ponownie test.

Powinien zostać wyświetlony przebieg testu za pomocą trzech iteracji przy użyciu wartości w pliku *csv.* Sprawdzanie poprawności powinno działać, a test powinien być wyświetlany jako przekazany w Eksploratorze testów.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>Jakie są atrybuty źródła danych dla innych typów źródeł danych, takich jak SQL Express lub XML?

**Odp.:** Przykładowe ciągi źródłowe danych w poniższej tabeli można użyć, kopiując je do kodu i dokonując niezbędnych dostosowań.

**Typy i atrybuty źródła danych**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Przypadek testowy w team foundation server

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap.Designer?

**Odp.:** Wszelkie zmiany kodu wprowadzone w pliku *UIMapDesigner.cs* zostaną zastąpione za każdym razem, gdy wygenerujesz kod przy użyciu konstruktora testów interfejsu użytkownika kodu — kodowany. W tym przykładzie, a w większości przypadków zmiany kodu potrzebne do umożliwienia testowi użycia źródła danych można wnieść do pliku kodu źródłowego testu (czyli *CodedUITest1.cs*).

Jeśli trzeba zmodyfikować zarejestrowaną metodę, należy ją skopiować, aby *UIMap.cs* plik i zmienić jego nazwę. UIMap.cs *UIMap.cs* plik może służyć do zastępowania metod i właściwości w pliku *UIMapDesigner.cs.* Należy usunąć odwołanie do oryginalnej metody w pliku *kodowanego UITest.cs* i zastąpić go nazwą metody o zmienionej nazwie.

## <a name="see-also"></a>Zobacz też

- [Uimap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
