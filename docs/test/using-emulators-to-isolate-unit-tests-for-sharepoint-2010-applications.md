---
title: Izolowanie testów jednostkowych aplikacji SharePoint 2010 przy użyciu emulatorów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: baa1ebbc63f0e9649e1601bbcb6220ef8bc5f5b5
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296063"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Izolowanie testów jednostkowych aplikacji SharePoint 2010 przy użyciu emulatorów

Pakiet Microsoft.SharePoint.Emulators zawiera zbiór bibliotek, które ułatwiają tworzenie izolowanych testów jednostkowych dla aplikacji programu Microsoft SharePoint 2010. Emulatory używają [podkładki](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) z [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) izolacji platformę, by tworzyć lekkie obiekty w pamięci, umożliwiających naśladowanie najczęściej używanych obiektów i metod interfejsu API programu SharePoint. Gdy metodę programu SharePoint nie jest emulowana, lub gdy chcesz zmienić zachowanie domyślne emulatora, możesz utworzyć podkładki substytutów zapewniające wyniki, które chcesz.

Istniejące metody i klasy testowe można łatwo przekształcić do uruchamiania w kontekście emulatora. Ta funkcja pozwala utworzyć testy podwójnego zastosowania. Test podwójnego zastosowania można przełączać się między testami integracji dla prawdziwego interfejsu API programu SharePoint i testów jednostkowych, które korzystają z emulatorów.

##  <a name="BKMK_Requirements"></a> Wymagania

-   Program Microsoft SharePoint 2010 (SharePoint 2010 Server lub SharePoint 2010 Foundation)

-   Microsoft Visual Studio Enterprise

-   Pakiet NuGet emulatorów programu Microsoft SharePoint

Należy także zapoznać się z [podstawy testów jednostkowych w programie Visual Studio](../test/unit-test-basics.md) i pewną wiedzę na temat [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

##  <a name="BKMK_The_AppointmentsWebPart_example"></a> Przykład AppointmentsWebPart

AppointmentsWebPart pozwala na wyświetlanie i zarządzanie nimi terminów listą programu SharePoint.

![Składnik Web Part terminów](../test/media/ut_emulators_appointmentswebpart.png)

Przetestujemy dwie metody części sieci web w tym przykładzie:

-   `ScheduleAppointment` Metoda sprawdza poprawność wartości elementu listy, które są przekazywane do metody i tworzy nowy wpis na liście w określonej sieci web programu SharePoint.

-   `GetAppointmentsForToday` Metoda zwraca szczegóły dzisiejszych terminów.

##  <a name="convert-an-existing-test"></a>Konwertowanie istniejącego testu

W typowym teście metody w składniku programu SharePoint metoda testowa tworzy tymczasową witrynę w programie SharePoint Foundation i dodaje składniki programu SharePoint do witryny, której wymaga testowany kod. Metoda testowa następnie tworzy i instancję składnika. Na koniec badania witryna zostaje rozłączona.

`ScheduleAppointment` Metoda naszego kodu poddawanego testom jest prawdopodobnie jedną z pierwszych metod napisanych dla składnika:

```csharp
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

Pierwsze badanie funkcjonalności w `ScheduleAppointment` metoda może wyglądać następująco:

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

Chociaż niniejsza metoda badania sprawdza, czy `ScheduleAppointment` metoda poprawnie dodaje nowy wpis do listy, jest to raczej test integracji składnika web part, niż test określonego zachowania kodu. Zależności zewnętrzne w SharePoint i interfejsu API programu SharePoint może spowodować, że test zakończył się niepowodzeniem z powodów innych niż kod użytkownika w `ScheduleAppointment` metody. Obciążenie związane z tworzeniem i likwidowaniem witryny programu SharePoint można również ustawić test będzie zbyt wolny był uruchamiany jako normalna część procesu kodowania. Wykonywanie konfiguracji i niszczenia witryny dla każdej metody testowej tylko powiększa problem stworzenia wydajne dla deweloperów testy jednostkowe.

Emulatorów Microsoft SharePoint dają zestaw obiektów i metod "sobowtórów", które naśladują zachowanie najczęściej interfejsów API programu SharePoint. Emulowane metody to lekkie implementacje interfejsu API programu SharePoint, które nie wymagają uruchamiania programu SharePoint. Używając Microsoft Fakes do ominięcia wywołań interfejsu API programu SharePoint, do metody emulatorów programu SharePoint funkcji, możesz izolować testy i upewnij się, że testujesz kodu, który ma. Po wywołaniu metod SharePoint, które nie są emulowane, można użyć elementów sztucznych bezpośrednio do tworzenia pożądanego zachowania.

###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Dodawanie pakietu emulatorów do projektu testowego

Aby dodać emulatory programu SharePoint do projektu testowego:

1.  Wybierz projekt testowy w **Eksploratora rozwiązań**.

2.  Wybierz **Zarządzaj pakietami NuGet** w menu skrótów.

3.  Wyszukiwanie **Online** kategorię `Microsoft.SharePoint.Emulators`, a następnie wybierz **zainstalować**.

![Pakiet NuGet emulatorów programu SharePoint](../test/media/ut_emulators_nuget.png)

###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Uruchamianie metody testowej z emulacją

Instalowanie pakietu dodaje odwołania do bibliotek wymaganych do swoich projektów. Aby umożliwić obsługę emulatorów w istniejącej klasie testu, Dodaj przestrzenie nazw `Microsoft.SharePoint.Emulators` i `Microsoft.QualityTools.Testing.Emulators`.

Aby umożliwić emulację w metodach testów, zawiń treści metody w `using` instrukcję, która tworzy `SharePointEmulationScope` obiektu. Na przykład:

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

Po wykonaniu metody testowej, środowisko uruchomieniowe emulatora wywołuje Microsoft Fakes aby dynamicznie wstrzykiwać kod w metody programu SharePoint, aby przekierować wywołania tych metod do delegatów zadeklarowanych w *Microsoft.SharePoint.Fakes.dll* . *Biblioteka Microsoft.SharePoint.Emulators.dll* implementuje delegatów dla emulowanych metod, ściśle naśladując rzeczywiste zachowanie programu SharePoint. Gdy metoda testowa lub składnik poddawany testom wywołuje metodę programu SharePoint, wynikające zachowanie jest emulacją.

![Przepływ wykonania emulatora](../test/media/ut_emulators_flowchart.png)

##  <a name="create-dual-use-classes-and-methods"></a>Tworzenie klasy produktów podwójnego zastosowania i metod

Aby utworzyć metody, które mogą być używane dla badań integracji dla prawdziwego interfejsu API programu SharePoint oraz testów jednostkowych, które używają emulatorów, użyj przeciążonego konstruktora `SharePointEmulationScope(EmulationMode)` opakowywać kodu metody testowej. Dwie wartości `EmulationMode` wyliczenia Określ, czy zakres używa emulatorów (`EmulationMode.Enabled`) lub czy zakres używa interfejsu API programu SharePoint (`EmulationMode.Passthrough`).

Na przykład Oto jak można zmodyfikować poprzedni test, aby miał podwójne zastosowanie:

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

## <a name="use-testinitialize-and-testcleanup-attributes-to-create-a-dual-use-test-class"></a>Użyj TestInitialize i TestCleanup atrybutów do tworzenia produktów podwójnego zastosowania przetestowania klasy

Po uruchomieniu wszystkich lub większości testów w klasie za pomocą `SharePointEmulationScope`, możesz skorzystać z technik poziomie klasy, aby ustawić tryb emulacji.

-   Testowanie metody klasy, które przypisane z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> można tworzyć i niszczyć zakres.

-   Ustawienie `EmulationMode` w klasie poziomu może umożliwić automatyzację zmiany trybu między `EmulationMode.Enabled` i `EmulationMode.Passthrough`.

Metoda klasy, która jest związana z `[TestInitialize]` jest uruchamiany na początku każdej metody testowej, a metoda, która jest związana z `[TestCleanup]` działa na końcu każdej metody testowej. Można deklarować pole prywatne dla `SharePointEmulationScope` obiektów na poziomie klasy, zainicjować go w `TestInitialize` przypisanej metody, a następnie usunąć obiekt w `TestCleanup` przypisanej metodzie.

Można użyć dowolnej metody wybranej do zautomatyzowania wyboru `EmulationMode`. Jednym ze sposobów jest do sprawdzania istnienia symbolu za pomocą dyrektywy preprocesora. Na przykład, aby uruchomić metody testowe w klasie przy użyciu emulatorów, można zdefiniować symbol taki jak `USE_EMULATION` w pliku projektu testu lub w wierszu polecenia kompilacji. Jeśli zdefiniowano symbol, poziomu klasy `EmulationMode` stała jest zadeklarowana i ustawiana na `Enabled`. W przeciwnym wypadku stała jest ustawiona na `Passthrough`.

Oto przykład klasy testowej, który demonstruje, jak użyć dyrektywy preprocesora oraz `TestInitialize` i `TestCleanup` opartego na atrybutach metody, aby ustawić tryb emulacji.

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

##  <a name="handle-non-emulated-sharepoint-methods"></a>Obsługa nieemulowanych metod programu SharePoint

Nie wszystkie typy programu SharePoint są emulowane i nie wszystkie metody w niektórych typach emulowanych są emulowane. Jeśli testowany kod wywołuje metodę programu SharePoint, która nie jest emulowana, metoda zgłasza `NotSupportedException` wyjątku. Gdy wystąpi wyjątek, dodajesz podkładkę substytut dla metody programu SharePoint.

**Konfigurowanie substytutów programu Sharepoint**

Aby jawnie wywołać podkładki Microsoft Fakes:

1.  Jeśli chcesz utworzyć podkładkę dla klasy programu SharePoint, która nie jest emulowana, Edytuj *Microsoft.SharePoint.fakes* plik i dodać klasę do listy klas typu shim. Zobacz [Konfigurowanie generowania kodu odcinków](code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md#configure-code-generation-of-stubs) części [generowanie kodu, kompilacji i konwencje nazewnictwa w Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).

     ![Substytuty folder w Eksploratorze rozwiązań](../test/media/ut_emulators_fakesfilefolder.png)

2.  Ponownie skompiluj projekt testowy co najmniej raz po zainstalowaniu pakietu emulatorów Microsoft SharePoint i jeśli edytowano *Microsoft.SharePoint.Fakes* pliku. Kompilowanie projektu tworzy i wypełnia **FakesAssembly** folderu w folderze głównym projektu na dysku.

     ![FakesAssembly folder](../test/media/ut_emulators_fakesassemblyfolder.png)

3.  Dodaj odwołanie do **Microsoft.SharePoint.14.0.0.0.Fakes.dll** zestawu, który znajduje się w **FakesAssembly** folderu.

4.  (Opcjonalnie) Dodaj dyrektywę przestrzeni nazw dla klasy testu dla `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` i wszelkie zagnieżdżone przestrzenie nazw `Microsoft.SharePoint.Fakes`, którego chcesz użyć.

**Implementowanie delegata obiektu podkładkowego dla metody programu SharePoint**

W naszym przykładowym projekcie `GetAppointmentsForToday` wywołania metody [SPList.GetItems(SPQuery)](xref:Microsoft.SharePoint.SPList.GetItems%2A) metody interfejsu API programu SharePoint.

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

`SPList.GetItems(SPQuery)` Wersji przeciążonej `GetItems` metoda nie jest emulowana. W związku z tym, zawijanie istniejącego testu dla `GetAppointmentsForToday` w `SharePoint.Emulation.Scope` może zakończyć się niepowodzeniem. Aby utworzyć test pracy, musisz napisać implementację delegata substytuty `ShimSPList.GetItemsSPQuery` zwracającego wyniki, które mają zostać przetestowane.

Oto modyfikacja istniejącej metody testowej, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, która implementuje delegata substytuty. Wymagane zmiany są wywoływane w komentarzach:

> [!IMPORTANT]
> Metody testowe, które jawnie tworzą podkładki substytutów wyrzucają `ShimNotSupported` wyjątku, gdy test jest wykonywany w `EmulationMode.Passthrough` kontekstu. Aby uniknąć tego problemu, należy użyć zmiennej do ustawiania `EmulationMode` wartości i zawijania kodu substytutów w `if` instrukcji, która sprawdza wartość.

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

W tej metodzie najpierw przetestujemy czy włączono emulację. Jeśli tak jest, utworzymy obiekt podkładkowy substytut dla naszych `SPList` listy, a następnie utwórz i przypiszemy metodę do jego `GetItemsSPQuery` delegować. Delegat używa Fakes `Bind` metody dodawania poprawnych elementów listy do `ShimSPListItemCollection` zwracanej do obiektu wywołującego.

##  <a name="write-emulation-tests-from-scratch-and-a-summary"></a>Zapis testy emulacji od nowa i podsumowanie

Mimo że techniki służące do tworzenia emulacji i testy produktów podwójnego zastosowania, które są opisane w poprzedniej sekcji przyjęto założenie, że Konwertowanie istniejących testów, możesz również użyć techniki do pisania testów od podstaw. Na poniższej liście podsumowano te techniki:

-   Aby użyć emulatorów w projekcie testowym, Dodaj pakiet Microsoft.SharePoint.Emulators NuGet do projektu.

-   Aby użyć emulatorów w metodzie testowej, Utwórz `SharePointEmulationScope` obiektu na początku metody. Wszystkie obsługiwane interfejsy API programu SharePoint będą emulowane aż jego usunięciu.

-   Zapisz swój kod testu tak, jakby jakbyś Pisał go dla prawdziwego interfejsu API programu SharePoint. Kontekst emulacji automatycznie przekierowuje wywołania metod programu SharePoint do ich emulatorów.

-   Nie wszystkie obiekty programu SharePoint są emulowane i nie wszystkie metody niektórych obiektów emulowanych są emulowane. Element `NotSupportedException` jest wyjątek podczas korzystania z nieemulowanego obiektu lub metody. W takim przypadku jawnie Utwórz delegata podkładki substytutu dla metody, aby zwracane było wymagane zachowanie.

-   Aby utworzyć testy podwójnego zastosowania, użyj `SharePointEmulationScope(EmulationMode)` konstruktora, aby utworzyć obiekt zakresu emulacji. `EmulationMode` Wartość określa, czy wywołania programu SharePoint są emulowane czy wykonywane z rzeczywistą witryną SharePoint.

-   Jeśli wszystkie lub większość metod testowych w klasie testowej są wykonywane w kontekście emulacji, można użyć poziomu klasy `TestInitialize` przypisanej metody, aby utworzyć `SharePointEmulationScope` obiektu i pola na poziomie klasy, aby ustawić tryb emulacji. To pomoże Ci to w zautomatyzowaniu zmiany trybu emulacji. Następnie użyj `TestCleanup` przypisanej metody do usuwania obiektu zakres.

##  <a name="BKMK_Example"></a> Przykład

Poniżej przedstawiono końcowy przykład, która łączy techniki emulatora programu SharePoint, które są opisane powyżej:

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

##  <a name="BKMK_Emulated_SharePoint_types"></a> Emulowane typy programu SharePoint

 <xref:Microsoft.SharePoint.SPField?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldIndex?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldIndexCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldLink?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldLinkCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldUrlValue?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFile?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFileCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFolder?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFolderCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItem?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItemEventDataCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItemEventProperties?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPList?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListEventProperties?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListItem?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListItemCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPQuery?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPRoleAssignment?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPRoleAssignmentCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSecurableObject?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSecurity?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSite?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPUser?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPUserCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPView?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPViewCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPViewContext?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPWeb?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPWebCollection?displayProperty=nameWithType>

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
