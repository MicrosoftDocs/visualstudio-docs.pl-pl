---
title: Izolowanie testów jednostkowych dla aplikacji programu SharePoint 2010 przy użyciu emulatorów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cc3560c1cbcebea9f61465240cd4e2c7a0f811f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667467"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Izolowanie testów jednostkowych aplikacji SharePoint 2010 przy użyciu emulatorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakiet Microsoft. SharePoint. Emulators udostępnia zestaw bibliotek, które ułatwiają tworzenie izolowanych testów jednostkowych dla aplikacji programu Microsoft SharePoint 2010. Emulatory używają [podkładek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) z [firmy Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) dla sztucznej struktury izolacji, aby utworzyć lekkie obiekty w pamięci, które są śladować najpopularniejszych obiektów i metod interfejsu API programu SharePoint. Gdy metoda programu SharePoint nie jest emulowana lub jeśli chcesz zmienić domyślne zachowanie emulatora, możesz utworzyć podklasy podkładek w celu zapewnienia żądanych wyników.

 Istniejące metody i klasy testowe można łatwo skonwertować do uruchamiania w kontekście emulatora. Ta funkcja umożliwia tworzenie testów podwójnego zastosowania. Test dwukrotnego zastosowania umożliwia przełączenie między testami integracji z rzeczywistym interfejsem API programu SharePoint i izolowanych testów jednostkowych, które używają emulatorów.

## <a name="BKMK_In_this_topic"></a>W tym temacie
 [Requirements](#BKMK_Requirements)

 [Przykład AppointmentsWebPart](#BKMK_The_AppointmentsWebPart_example)

 [Konwertowanie istniejącego testu](#BKMK_Converting_an_existing_test)

- [Dodawanie pakietu emulatorów do projektu testowego](#BKMK_Adding_the_Emulators_package_to_a_test_project)

- [Uruchamianie metody testowej przy użyciu emulacji](#BKMK__Running_a_test_method_in_the_emulation_context)

  [Tworzenie klas i metod podwójnego zastosowania](#BKMK_Creating_dual_use_classes_and_methods)

  [Używanie atrybutów TestInitialize i TestCleanup do tworzenia klasy testu podwójnego użycia](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)

  [Obsługa nieemulowanych metod programu SharePoint](#BKMK_Handling_non_emulated_SharePoint_methods)

  [Pisanie testów emulacji od podstaw oraz podsumowanie](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)

  [Przykład](#BKMK_Example)

  [Emulowane typy programu SharePoint](#BKMK_Emulated_SharePoint_types)

## <a name="BKMK_Requirements"></a>Wymagania

- Microsoft SharePoint 2010 (SharePoint 2010 Server lub SharePoint 2010 Foundation)

- Microsoft Visual Studio Enterprise

- Pakiet NuGet emulatorów programu Microsoft SharePoint

  Należy również zapoznać się z [podstawą testów jednostkowych w programie Visual Studio](../test/unit-test-basics.md) i pewną wiedzę na temat sztucznych [firmy Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md).

## <a name="BKMK_The_AppointmentsWebPart_example"></a>Przykład AppointmentsWebPart
 AppointmentsWebPart umożliwia wyświetlenie listy programu SharePoint i zarządzanie nimi.

 ![Składnik Web Part terminów](../test/media/ut-emulators-appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")

 Będziemy testować dwie metody części sieci Web w tym przykładzie:

- Metoda `ScheduleAppointment` sprawdza poprawność wartości elementów listy przesłanych do metody i tworzy nowy wpis na liście w określonym sieci Web programu SharePoint.

- Metoda `GetAppointmentsForToday` zwraca szczegóły dzisiejszych terminów.

  [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Converting_an_existing_test"></a>Konwertowanie istniejącego testu
 W typowym teście metody w składniku programu SharePoint metoda testowa tworzy tymczasową lokację w programie SharePoint Foundation i dodaje do niej składniki programu SharePoint. Następnie metoda testowa tworzy i wykonuje wystąpienie składnika. Po zakończeniu testu lokacja zostanie rozłączona.

 Metoda `ScheduleAppointment` naszego testowanego kodu jest prawdopodobnie jedną z pierwszych metod zapisanych dla składnika:

```
// method under test
public bool ScheduleAppointment(SPWeb web, string listName, string name,
    string phone, string email, string age, DateTime date, out string errorMsg)
{
    errorMsg = string.Empty;
    var badFormat = this.checkInput(name, phone, email, age);
    if (badFormat)
    {
        errorMsg = "Bad Format";
        return false;
    }
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);
    if (exists)
    {
        errorMsg = "Item already exists";
        return false;
    }
    SPListItemCollection items = web.Lists[listName].Items;
    // create item and populate fields
    SPListItem item = items.Add();
    item["Name"] = name;
    item["Phone"] = phone;
    item["Email"] = email;
    item["Age"] = age;
    item["Date"] = date.ToString("D");
    item.Update();
    return true;
}

```

 Pierwszy test funkcjonalności w `ScheduleAppointment` metodzie może wyglądać następująco:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 Chociaż ta metoda testowa sprawdza, czy metoda `ScheduleAppointment` prawidłowo dodaje nowy wpis do listy, jest to bardziej test integracji części sieci Web niż test określonego zachowania kodu. Zależności zewnętrzne do programu SharePoint i interfejsu API programu SharePoint mogą spowodować niepowodzenie testu z przyczyn innych niż kod użytkownika w metodzie `ScheduleAppointment`. Narzuty w trakcie tworzenia i niszczenia witryny programu SharePoint może również sprawić, że test będzie zbyt wolny do uruchamiania jako zwykła część procesu kodowania. Przeprowadzenie instalacji i zniszczenia lokacji dla każdej metody testowej tylko związków problemu tworzenia wydajnych testów jednostkowych dla deweloperów.

 Emulatory programu Microsoft SharePoint dają zestaw obiektów i metod "podwaja", które naśladuje zachowanie najczęstszych interfejsów API programu SharePoint. Emulowane metody to lekkie implementacje interfejsu API programu SharePoint, które nie wymagają uruchamiania programu SharePoint. Dzięki użyciu sztucznych firmy Microsoft do rozdzielania wywołań interfejsu API programu SharePoint do metody Podwajaj emulatory programu SharePoint, można izolować testy i upewnić się, że testujesz odpowiedni kod. Po wywołaniu metod programu SharePoint, które nie są emulowane, można użyć elementów sztucznych bezpośrednio do utworzenia żądanego zachowania.

 [W tym temacie](#BKMK_In_this_topic)

### <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a>Dodawanie pakietu emulatorów do projektu testowego
 Aby dodać emulatory programu SharePoint do projektu testowego:

1. Wybierz projekt testowy w Eksplorator rozwiązań.

2. Wybierz pozycję **Zarządzaj pakietami NuGet...** w menu skrótów.

3. Wyszukaj `Microsoft.SharePoint.Emulators` kategorii **online** , a następnie wybierz **Zainstaluj**.

   ![Pakiet NuGet emulatorów programu SharePoint](../test/media/ut-emulators-nuget.png "UT_EMULATORS_Nuget")

   [W tym temacie](#BKMK_In_this_topic)

### <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a>Uruchamianie metody testowej przy użyciu emulacji
 Zainstalowanie pakietu dodaje odwołania do wymaganych bibliotek do Twoich projektów. Aby ułatwić korzystanie z emulatorów w istniejącej klasie testowej, Dodaj obszary nazw `Microsoft.SharePoint.Emulators` i `Microsoft.QualityTools.Testing.Emulators`.

 Aby włączyć emulację w metodach testowych, zawiń treść metody w instrukcji `using`, która tworzy obiekt `SharePointEmulationScope`. Na przykład:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // create the emulation scope with a using statement
    using (new SharePointEmulationScope())
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}

```

 Gdy metoda testowa jest wykonywana, środowisko uruchomieniowe emulatora wywołuje sztuczne firmy Microsoft, aby dynamicznie wstrzyknąć kod do metod programu SharePoint w celu przełączenia wywołań tych metod do delegatów, które są zadeklarowane w Microsoft. SharePoint. sztuczne. dll. Microsoft. SharePoint. Emulators. dll implementuje delegatów dla emulowanych metod, ściśle naśladując rzeczywiste zachowanie programu SharePoint. Gdy metoda testowa lub składnik objęty testami wywołuje metodę programu SharePoint, zachowanie, które jest wynikiem emulacji.

 ![Przepływ wykonywania emulatora](../test/media/ut-emulators-flowchart.png "UT_EMULATORS_FlowChart")

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Creating_dual_use_classes_and_methods"></a>Tworzenie klas i metod podwójnego zastosowania
 Aby utworzyć metody, które mogą być używane do obu testów integracji względem rzeczywistego interfejsu API programu SharePoint i izolowanych testów jednostkowych, które używają emulatorów, użyj przeciążonego konstruktora `SharePointEmulationScope(EmulationMode)`, aby otoczyć kod metody testowej. Dwie wartości wyliczenia `EmulationMode` określają, czy zakres używa emulatorów (`EmulationMode.Enabled`), czy zakres używa interfejsu API programu SharePoint (`EmulationMode.Passthrough`).

 Na przykład poniżej przedstawiono, jak można zmodyfikować poprzedni test, aby był dwukrotnie używany:

```csharp

// class level field specifies emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled;

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // emulation scope determined by emulatorMode
    using( SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a>Używanie atrybutów TestInitialize i TestCleanup do tworzenia klasy testu podwójnego użycia
 Jeśli uruchamiasz wszystkie lub większość testów w klasie przy użyciu `SharePointEmulationScope`, możesz skorzystać z technik na poziomie klasy, aby ustawić tryb emulacji.

- Metody klasy testowej, które są przypisane do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> mogą utworzyć i zniszczyć zakres.

- Ustawienie `EmulationMode` na poziomie klasy może umożliwić automatyzację zmiany trybu między `EmulationMode.Enabled` i `EmulationMode.Passthrough`.

  Metoda klasy, która jest przypisana `[TestInitialize]` jest uruchamiana na początku każdej metody testowej, a metoda, która jest przypisana do `[TestCleanup]` uruchamiana na końcu każdej metody testowej. Można zadeklarować pole prywatne dla obiektu `SharePointEmulationScope` na poziomie klasy, zainicjować go w metodzie `TestInitialize` z atrybutem, a następnie usunąć obiekt w `TestCleanup` Metoda z atrybutem.

  Możesz użyć dowolnej metody, która pozwala zautomatyzować wybór `EmulationMode`. Jednym ze sposobów jest sprawdzenie istnienia symbolu przy użyciu dyrektyw preprocesora. Na przykład, aby uruchomić metody testowe w klasie przy użyciu emulatorów, można zdefiniować symbol, taki jak `USE_EMULATION` w pliku projektu testowego lub w wierszu polecenia kompilacji. Jeśli symbol jest zdefiniowany, na poziomie klasy `EmulationMode` stała jest zadeklarowana i ustawiona na `Enabled`. W przeciwnym razie stała jest ustawiona na `Passthrough`.

  Oto przykład klasy testowej, która pokazuje, jak używać dyrektyw preprocesora oraz metod `TestInitialize` i `TestCleanup` z atrybutami, aby ustawić tryb emulacji.

```csharp
//namespace declarations
...

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        ...// More tests

    }
}

```

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a>Obsługa nieemulowanych metod programu SharePoint
 Nie wszystkie typy programu SharePoint są emulowane i nie wszystkie metody w niektórych typach emulowanych są emulowane. Jeśli testowa kod wywołuje metodę programu SharePoint, która nie jest emulowana, metoda zgłasza wyjątek `NotSupportedException`. Gdy wystąpi wyjątek, dodawana jest podkładka dotycząca sfałszowania dla metody programu SharePoint.

 **Konfigurowanie elementów sztucznych programu SharePoint**

 Aby jawnie wywołać podkładki dla sztucznych elementów firmy Microsoft:

1. Jeśli chcesz utworzyć podkładkę dla klasy programu SharePoint, która nie jest emulowana, edytuj plik Microsoft. SharePoint. sztuczne i Dodaj klasę do listy klas zastąpionym podkładką. Zapoznaj się z sekcją [Konfigurowanie generowania kodu wycinków i podkładek](https://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) [w ramach Konwencji generowania kodu, kompilacji i nazewnictwa w](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)przypadku sztucznych firmy Microsoft.

    ![Folder sztuczny w Eksplorator rozwiązań](../test/media/ut-emulators-fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")

2. Kompiluj ponownie projekt testowy co najmniej raz po zainstalowaniu pakietu emulatorów programu Microsoft SharePoint i edytowania pliku Microsoft. SharePoint. repliks. Kompilowanie projektu powoduje utworzenie i wypełnienie folderu **FakesAssembly** w folderze głównym projektu na dysku.

    ![Folder FakesAssembly](../test/media/ut-emulators-fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")

3. Dodaj odwołanie do zestawu **Microsoft. SharePoint. 14.0.0.0. repliks. dll** , który znajduje się w folderze **FakesAssembly** .

4. Obowiązkowe Dodaj dyrektywę Namespace do klasy testowej dla `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` i wszelkiej zagnieżdżonej przestrzeni nazw `Microsoft.SharePoint.Fakes`that, której chcesz użyć.

   **Implementowanie delegata podkładki dla metody programu SharePoint**

   W naszym przykładowym projekcie Metoda `GetAppointmentsForToday` wywołuje metodę interfejsu API programu SharePoint [SPList. GetItems (SPQuery)](https://msdn.microsoft.com/library/ms457534.aspx) .

```csharp
// method under test
public string GetAppointmentsForToday(string listName, SPWeb web)
{
    SPList list = web.Lists[listName];
    DateTime today = DateTime.Now;
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};
    var result = new System.Text.StringBuilder();
    foreach (SPListItem item in list.GetItems(listQuery))
    {
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);
    }
    return result.ToString();
}

```

 @No__t_0 wersja przeciążonej metody `GetItems` nie jest emulowana. W związku z tym po prostu Zawijanie istniejącego testu dla `GetAppointmentsForToday` w `SharePoint.Emulation.Scope` może zakończyć się niepowodzeniem. Aby utworzyć test roboczy, należy napisać implementację delegatów sztucznych `ShimSPList.GetItemsSPQuery`, która zwraca wyniki, które mają zostać przetestowane.

 Poniżej przedstawiono modyfikację istniejącej metody testowej, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, która implementuje delegata elementów sztucznych. Wymagane zmiany są wywoływane w komentarzach:

> [!IMPORTANT]
> Metody testowe, które jawnie tworzą podkładki z elementami zastępczymi, zgłaszają wyjątek `ShimNotSupported`, gdy test jest uruchamiany w kontekście `EmulationMode.Passthrough`. Aby uniknąć tego problemu, użyj zmiennej, aby ustawić wartość `EmulationMode` i otoczyć każdy kod sztuczny w instrukcji `if`, która testuje wartość.

```csharp
// class level field to set emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled

[TestMethod]
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
{

    // create the emulation scope with a using statement
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);
        // insert 2 items into list
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
            "raisa@outlook.com", "55", date.ToString("D") });
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

        // use Fakes shims only if emulation is enabled
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}

        // Act
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
        list.Delete();

        // Assert
        Assert.IsTrue(result.Contains(String.Format(
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
            "Age: 55, Date: {0}", date.ToString("D"))));
        Assert.IsFalse(result.Contains("Name: Francis Totten"));
    }
}

```

 W tej metodzie najpierw Sprawdzamy, czy emulacja jest włączona. Jeśli tak jest, utworzymy obiekt podkładki dla naszej listy `SPList`, a następnie utworzysz i przypiszesz metodę do jej delegata `GetItemsSPQuery`. Delegat używa metody sztuczne `Bind` do dodania poprawnego elementu listy do `ShimSPListItemCollection`, który jest zwracany do obiektu wywołującego.

 [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a>Pisanie testów emulacji od podstaw oraz podsumowanie
 Mimo że techniki tworzenia emulacji i podwójnego zastosowania, które są opisane w poprzednich sekcjach założono, że konwertujesz istniejące testy, możesz również użyć technik do pisania testów od podstaw. Poniższa lista zawiera podsumowanie tych technik:

- Aby użyć emulatorów w projekcie testowym, Dodaj pakiet NuGet Microsoft. SharePoint. Emulators do projektu.

- Aby użyć emulatorów w metodzie testowej, Utwórz obiekt `SharePointEmulationScope` na początku metody. Wszystkie obsługiwane interfejsy API programu SharePoint będą emulowane do momentu usunięcia zakresu.

- Napisz kod testowy tak, jakby był zapisywany w rzeczywistym interfejsie API programu SharePoint. Kontekst emulacji automatycznie rozpoznaje wywołania metod programu SharePoint z ich emulatorami.

- Nie wszystkie obiekty programu SharePoint są emulowane i nie wszystkie metody niektórych obiektów emulowanych są emulowane. Wyjątek `NotSupportedException` jest generowany, gdy jest używany nieemulowany obiekt lub metoda. W takim przypadku należy jawnie utworzyć delegata podkładki dla metody, aby zwracał wymagane zachowanie.

- Aby utworzyć testy podwójnego zastosowania, użyj konstruktora `SharePointEmulationScope(EmulationMode)`, aby utworzyć obiekt zakresu emulacji. Wartość `EmulationMode` określa, czy wywołania programu SharePoint są emulowane lub wykonywane względem rzeczywistej witryny programu SharePoint.

- Jeśli wszystkie lub większość metod testowych w klasie testowej wykonuje się w kontekście emulacji, można użyć metody z atrybutem `TestInitialize` na poziomie klasy do utworzenia obiektu `SharePointEmulationScope` i pola na poziomie klasy, aby ustawić tryb emulacji. Pomoże to zautomatyzować zmianę trybu emulacji. Następnie użyj `TestCleanup` przypisanej metody do usuwania obiektu Scope.

  [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Example"></a>Przyklad
 Oto ostatni przykład obejmujący opisane powyżej techniki emulatora programu SharePoint:

```csharp
using System;
//other namespace declarations
...
// code under test
using MySPApps;
using Microsoft.SharePoint;
// unit testing and emulators
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.QualityTools.Testing.Emulators;
using Microsoft.SharePoint.Emulators;
// explicit Fakes shims
using Microsoft.QualityTools.Testing.Fakes;
using Microsoft.SharePoint.Fakes

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATION
            private const EmulationMode emulatorMode = EmulationMode.Enabled;
        #else
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;
        #endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]
        public void InitializeTest()
        {
            this.emulationScope = new SharePointEmulationScope(emulatorMode);
        }

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]
        public void Cleanup()
        {
            this.emulationScope.Dispose();
        }

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        [TestMethod]
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
        {

            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);
                // insert 2 items into list
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
                    "raisa@outlook.com", "55", date.ToString("D") });
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

                // use Fakes shims only if emulation is enabled
                if (emulatorMode == EmulationMode.Enabled)
                {
                    var sList = new ShimSPList(list);

                    sList.GetItemsSPQuery = (query) =>
                    {
                        var shim = new ShimSPListItemCollection();
                        shim.Bind(new[] { list.Items[0] });
                        return shim.Instance;
                    }
                }

                // Act
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
                list.Delete();

                // Assert
                Assert.IsTrue(result.Contains(String.Format(
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
                    "Age: 55, Date: {0}", date.ToString("D"))));
                Assert.IsFalse(result.Contains("Name: Francis Totten"));
            }
        }

        ...// More tests

    }
}

```

## <a name="BKMK_Emulated_SharePoint_types"></a>Emulowane typy programu SharePoint
 [Microsoft. SharePoint. SPField](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)

 [Microsoft. SharePoint. SPFieldIndex](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)

 [Microsoft. SharePoint. SPFieldIndexCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)

 [Microsoft. SharePoint. SPFieldLink](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)

 [Microsoft. SharePoint. SPFieldLinkCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)

 [Microsoft. SharePoint. SPFieldUrlValue](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)

 [Microsoft. SharePoint. SPFile](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)

 [Microsoft. SharePoint. SPFileCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)

 [Microsoft. SharePoint. SPFolder](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)

 [Microsoft. SharePoint. SPFolderCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)

 [Microsoft. SharePoint. SPItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)

 [Microsoft. SharePoint. SPItemEventDataCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)

 [Microsoft. SharePoint. SPItemEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)

 [Microsoft. SharePoint. SPList](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)

 [Microsoft. SharePoint. SPListCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)

 [Microsoft. SharePoint. SPListEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)

 [Microsoft. SharePoint. SPListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)

 [Microsoft. SharePoint. SPListItemCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)

 [Microsoft. SharePoint. SPQuery](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)

 [Microsoft. SharePoint. SPRoleAssignment](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)

 [Microsoft. SharePoint. SPRoleAssignmentCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)

 [Microsoft. SharePoint. SPSecurableObject](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)

 [Microsoft. SharePoint. SPSecurity](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)

 [Microsoft. SharePoint. SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)

 [Microsoft. SharePoint. SPUser](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)

 [Microsoft. SharePoint. SPUserCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)

 [Microsoft. SharePoint. SPView](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)

 [Microsoft. SharePoint. SPViewCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)

 [Microsoft. SharePoint. SPViewContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)

 [Microsoft. SharePoint. SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)

 [Microsoft. SharePoint. SPWebcollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)

 [W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
 [Testowanie jednostkowe kodu testowego](../test/unit-test-your-code.md) [aplikacji programu SharePoint 2010 z kodowanymi testami interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md) [testowanie wydajności sieci Web i obciążenia aplikacji SharePoint 2010 i 2013,](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [opracowywanie rozwiązań SharePoint](https://msdn.microsoft.com/library/059bce0f-c301-4234-a0b4-9c14b7cdfa3e)
