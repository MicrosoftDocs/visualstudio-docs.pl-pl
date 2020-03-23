---
title: Używanie wycinków do izolowania części aplikacji do testowania
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 328551a78464c7b682eea6a988c20e742f2797c9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568551"
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Stosowanie wycinków kodu do izolowania od siebie poszczególnych części aplikacji w celu przeprowadzania testów jednostkowych

*Typy skrótowe* są jedną z dwóch technologii, które zapewnia struktura Microsoft Fakes, aby umożliwić łatwe izolowanie składnika, który testujesz od innych składników, które wywołuje. Odcinek jest niewielkim fragmentem kodu, który zajmuje miejsce innego składnika podczas testu. Korzyścią wynikającą z zastosowania wycinka są spójne wyniki, co ułatwia tworzenie testów. Testy można będzie uruchomić, nawet jeśli inne składniki jeszcze nie działają.

Aby uzyskać przegląd i szybki przewodnik po podróbkach, zobacz [Izolowanie kodu w fazie testów z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

Aby użyć wycinków, trzeba napisać składnik w taki sposób, aby korzystał tylko z interfejsów, a nie z klas, i odwoływał się do innych części aplikacji. To dobra praktyka tworzenia projektów, ponieważ zmiany są wprowadzane tylko w jednej części i jest mniej prawdopodobne, że inne również będą wymagać zmian. Do celów testowych pozwala zastąpić wycinkiem rzeczywisty składnik.

Na diagramie składnikiem StockAnalyzer jest ten, który chcemy przetestować. Zwykle używa on innego składnika RealStockFeed. RealStockFeed zwraca jednak różne wyniki przy każdym wywołaniu jego metod, co utrudnia test StockAnalyzer.  Podczas testowania można zastąpić go inną klasą StubStockFeed.

![Klasy rzeczywiste i skrótowe są zgodne z jednym interfejsem.](../test/media/fakesinterfaces.png)

Wycinki opierają się w ten sposób na swoich możliwościach bycia strukturą kodu, dlatego zwykle są one używane w celu wyizolowania jednej strony aplikacji z innej. Aby odizolować go od innych zestawów, które nie są pod kontrolą, takich jak *System.dll*, zwykle należy użyć podkładek. Zobacz [Użyj podkładek do izolowania aplikacji od innych zestawów do testowania jednostkowego.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="how-to-use-stubs"></a>Jak używać wycinków

### <a name="design-for-dependency-injection"></a>Zaprojektowane do wstrzykiwania zależności

Aby korzystać z wycinków, aplikacja musi być tak zaprojektowana, aby różne składniki nie były zależne od siebie, ale tylko od definicji interfejsu. Zamiast być połączone w czasie kompilacji, składniki są połączone w czasie wykonywania. Ten wzór pomaga stworzyć oprogramowanie, które będzie niezawodne i łatwe do zaktualizowania, ponieważ zmiany zwykle nie są propagowane przez granice składnika. Zalecamy jego przestrzeganie, nawet jeśli nie używasz wycinków. Jeśli piszesz nowy kod, łatwo jest śledzić wzorzec [iniekcji zależności.](https://en.wikipedia.org/wiki/Dependency_injection) Jeśli piszesz testy dla istniejącego oprogramowania, możliwe, że trzeba będzie je refraktoryzować. Jeżeli byłoby to niepraktyczne, można rozważyć użycie zamiast niego podkładki.

Zacznijmy tę dyskusję od motywującego przykładu, tego na diagramie. Klasa, którą odczytuje StockAnalyzer, udostępnia ceny i generuje interesujące wyniki. Obejmuje ona niektóre metody publiczne, które chcemy sprawdzić. Aby zachować prostotę, spójrzmy na jedną z tych metod, bardzo prostą, która raportuje aktualną cenę danego udziału. Chcemy napisać test jednostkowy tej metody. Oto pierwszy projekt testu:

```csharp
[TestMethod]
public void TestMethod1()
{
    // Arrange:
    var analyzer = new StockAnalyzer();
    // Act:
    var result = analyzer.GetContosoPrice();
    // Assert:
    Assert.AreEqual(123, result); // Why 123?
}
```

```vb
<TestMethod()> Public Sub TestMethod1()
    ' Arrange:
    Dim analyzer = New StockAnalyzer()
    ' Act:
    Dim result = analyzer.GetContosoPrice()
    ' Assert:
    Assert.AreEqual(123, result) ' Why 123?
End Sub
```

Jeden z problemów z tym testem staje się natychmiast oczywisty: ceny udziału różnią się, więc potwierdzenie zwykle zakończy się niepowodzeniem.

Innym problemem może być to, że składnik StockFeed, który jest używany przez StockAnalyzer, jest wciąż w fazie opracowywania. Oto pierwszy projekt kodu badanej metody:

```csharp
public int GetContosoPrice()
{
    var stockFeed = new StockFeed(); // NOT RECOMMENDED
    return stockFeed.GetSharePrice("COOO");
}
```

```vb
Public Function GetContosoPrice()
    Dim stockFeed = New StockFeed() ' NOT RECOMMENDED
    Return stockFeed.GetSharePrice("COOO")
End Function
```

W obecnym stanie metoda ta nie może kompilować lub może zgłosić wyjątek, ponieważ praca w klasie StockFeed nie została jeszcze zakończona. Wstrzyknięcie interfejsu rozwiązuje oba te problemy. Wstrzyknięcie interfejsu wykorzystuje następującą regułę:

Kod dowolnego składnika aplikacji nigdy nie powinien jawnie odwoływać się do klasy w `new` innym składniku, w deklaracji lub w instrukcji. Zamiast tego zmienne i parametry powinny być zadeklarowane razem z interfejsami. Wystąpienia składników powinny być tworzone tylko przez kontener składnika.

- Przez "składnik", mamy na myśli klasę lub grupę klas, które można rozwijać i aktualizować razem. Składnikiem jest zazwyczaj kod w jednym projekcie programu Visual Studio. Jest mniej ważne, aby oddzielić klasy w ramach jednego składnika, ponieważ są one aktualizowane w tym samym czasie.

- Nie jest również tak ważne, aby oddzielić komponenty od klas stosunkowo stabilnej platformy, takiej jak *System.dll*. Pisanie interfejsów dla wszystkich tych klas spowodowałoby zaśmiecenie kodu.

Kod StockAnalyzer można oddzielić od stockfeed, korzystając z interfejsu następującego:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public StockAnalyzer(IStockFeed feed)
    {
        stockFeed = feed;
    }
    public int GetContosoPrice()
    {
        return stockFeed.GetSharePrice("COOO");
    }
}
```

```vb
Public Interface IStockFeed
    Function GetSharePrice(company As String) As Integer
End Interface

Public Class StockAnalyzer
    ' StockAnalyzer can be connected to any IStockFeed:
    Private stockFeed As IStockFeed
    Public Sub New(feed As IStockFeed)
        stockFeed = feed
    End Sub
    Public Function GetContosoPrice()
        Return stockFeed.GetSharePrice("COOO")
    End Function
End Class
```

W tym przykładzie StockAnalyzer przekazuje implementację IStockFeed podczas konstruowania. W ukończonej aplikacji kod inicjowania może wykonać połączenie:

```csharp
analyzer = new StockAnalyzer(new StockFeed());
```

Istnieją bardziej elastyczne sposoby wykonywania tego połączenia. Na przykład StockAnalyzer może zaakceptować obiekt fabryki, który może utworzyć wystąpienie różnych implementacji IStockFeed w różnych warunkach.

### <a name="generate-stubs"></a>Generowanie wycinków

Klasa, którą chcesz przetestować, została oddzielona od innych składników, których używa. Oddzielenie powoduje, że aplikacja staje się bardziej solidna i elastyczna, a ponadto pozwala połączyć składnik testu z implementacją wycinka w ramach testowania interfejsów.

Można po prostu zwyczajnie napisać wycinki jako klasy. Jednak środowisko Microsoft Fakes zapewnia bardziej dynamiczny sposób tworzenia najodpowiedniejszych wycinków dla każdego testu.

Aby użyć wycinków, należy najpierw wygenerować typy wycinków z definicji interfejsu.

#### <a name="add-a-fakes-assembly"></a>Dodawanie zestawu podróbek

1. W **Eksploratorze rozwiązań**rozwiń odwołania do projektu testowego **jednostki**.

   Jeśli pracujesz w języku Visual Basic, wybierz pozycję **Pokaż wszystkie pliki** na pasku narzędzi **Eksploratora rozwiązań,** aby wyświetlić węzeł **Odwołania.**

2. Wybierz zestaw zawierający definicje interfejsu, dla których chcesz utworzyć wycinki.

3. W menu skrótów wybierz polecenie **Dodaj zestaw podróbek**.

### <a name="write-your-test-with-stubs"></a>Napisz test z wycinkami

```csharp
[TestClass]
class TestStockAnalyzer
{
    [TestMethod]
    public void TestContosoStockPrice()
    {
      // Arrange:

        // Create the fake stockFeed:
        IStockFeed stockFeed =
             new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                 {
                     // Define each method:
                     // Name is original name + parameter types:
                     GetSharePriceString = (company) => { return 1234; }
                 };

        // In the completed application, stockFeed would be a real one:
        var componentUnderTest = new StockAnalyzer(stockFeed);

        // Act:
        int actualValue = componentUnderTest.GetContosoPrice();

        // Assert:
        Assert.AreEqual(1234, actualValue);
    }
    ...
}
```

```vb
<TestClass()> _
Class TestStockAnalyzer

    <TestMethod()> _
    Public Sub TestContosoStockPrice()
        ' Arrange:
        ' Create the fake stockFeed:
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
        With stockFeed
            .GetSharePriceString = Function(company)
                                       Return 1234
                                   End Function
        End With
        ' In the completed application, stockFeed would be a real one:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Act:
        Dim actualValue As Integer = componentUnderTest.GetContosoPrice
        ' Assert:
        Assert.AreEqual(1234, actualValue)
    End Sub
End Class
```

Szczególnym kawałkiem magii jest `StubIStockFeed`tutaj klasa. Dla każdego typu publicznego w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę wycinków. Nazwa klasy skrótowej jest pochodną od nazwy interfejsu,`Fakes.Stub`z " jako prefiksem i nazwami typów parametrów.

Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych.

### <a name="verify-parameter-values"></a>Weryfikowanie wartości parametrów

Można zweryfikować, że jeżeli składnik wywołuje inny składnik, przekazuje poprawne wartości. Teraz można umieścić potwierdzenie w wycinku lub przechowywać wartość i weryfikować ją w głównej części testu. Przykład:

```csharp
[TestClass]
class TestMyComponent
{
    [TestMethod]
    public void TestVariableContosoPrice()
    {
        // Arrange:
        int priceToReturn = 345;
        string companyCodeUsed = "";
        var componentUnderTest = new StockAnalyzer(new StockAnalysis.Fakes.StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };

        // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

        // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...
}
```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer = 345
        Dim companyCodeUsed As String = ""
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed()
        With stockFeed
            ' Implement the interface's method:
            .GetSharePriceString = _
                Function(company)
                    ' Store the parameter value:
                    companyCodeUsed = company
                    ' Return a fixed result:
                    Return priceToReturn
                End Function
        End With
        ' Create an object to test:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)

        ' Act:
        Dim actualResult As Integer = componentUnderTest.GetContosoPrice()

        ' Assert:
        ' Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult)
        ' Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed)
    End Sub
...
End Class
```

## <a name="stubs-for-different-kinds-of-type-members"></a>Wycinki dla różnych rodzajów elementów członkowskich typu

### <a name="methods"></a>Metody

Jak opisano w przykładzie, metody można dzielić na wycinki, dołączając delegata do instancji klasy wycinka. Nazwa typu wycinka pochodzi od nazwy metody i parametrów. Na przykład, biorąc `IMyInterface` pod `MyMethod`uwagę następujący interfejs i metodę:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

Dołączamy wycinek do `MyMethod` tego zawsze zwraca 1:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Jeśli nie podasz skrótu dla funkcji, Fakes generuje funkcję, która zwraca domyślną wartość typu zwracanego. W przypadku liczb wartość domyślna to 0, `null` a dla `Nothing` typów klas jest (C#) lub (Visual Basic).

### <a name="properties"></a>Właściwości

Metody pobierające i ustawiające są widoczne jako oddzielne delegaty i mogą tworzyć poszczególne wycinki. Rozważmy na `Value` przykład `IMyInterface`właściwość:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Dołączamy delegatów do modułu ustawiacza i ustawiacza, `Value` aby symulować automatyczną właściwość:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Jeśli nie podasz metody skrótowe dla ustawiacza lub metody ustawiającej właściwości, fakes generuje skrót, który przechowuje wartości, dzięki czemu właściwość skrótowa działa jak zmienna prosta.

### <a name="events"></a>Zdarzenia

Zdarzenia są uwidocznione jako pola delegatów. W rezultacie wszystkie zdarzenia przekształcone na wycinki mogą być łatwo wywoływane przez wywołanie zdarzenia pola pomocniczego. Rozważmy następujący interfejs do skrótu:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

Aby podnieść `Changed` zdarzenie, po prostu wywołać delegata kopii zapasowej:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Metody ogólne

Jest możliwe do skrótu ogólne metody, zapewniając delegata dla każdego wystąpienia żądanej metody. Na przykład, biorąc pod uwagę następujący interfejs, zawierający metodę ogólną:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

Można napisać test, który `GetValue<int>` wycinki wystąpienia:

```csharp
// unit test code
[TestMethod]
public void TestGetValue()
{
    var stub = new StubIGenericMethod();
    stub.GetValueOf1<int>(() => 5);

    IGenericMethod target = stub;
    Assert.AreEqual(5, target.GetValue<int>());
}
```

Jeśli kod miał `GetValue<T>` wywołać z innym wystąpienia, skrót po prostu wywołać zachowanie.

### <a name="stubs-of-virtual-classes"></a>Wycinki wirtualnych klas

W poprzednich przykładach wycinki zostały wygenerowane z interfejsów. Można również wygenerować wycinki z klasy, która ma składowe virtual lub abstract. Przykład:

```csharp
// Base class in application under test
    public abstract class MyClass
    {
        public abstract void DoAbstract(string x);
        public virtual int DoVirtual(int n)
        { return n + 42; }
        public int DoConcrete()
        { return 1; }
    }
```

W skrótach generowanych przez tę klasę `DoAbstract()` można `DoVirtual()`ustawić `DoConcrete()`metody delegata dla i , ale nie .

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Jeśli nie podasz delegata dla metody wirtualnej, środowisko Fakes może zapewnić zachowanie domyślne albo wywoływać metodę w klasie bazowej. Aby wywołać metodę podstawową, `CallBase` ustaw właściwość:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set - default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
// No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="debug-stubs"></a>Wycinki debugowania

Typy wycinków zostały tak zaprojektowane, aby zapewniać płynność debugowania. Domyślnie debuger pomija kod generowany, powinien więc wejść bezpośrednio do niestandardowych implementacji elementu członkowskiego, które zostały dołączone do wycinka.

## <a name="stub-limitations"></a>Ograniczenia dotyczące wycinka

- Podpisy metod ze wskaźnikami nie są obsługiwane.

- Zapieczętowane klasy lub metody statyczne nie mogą być wycięciami, ponieważ typy skrótowe opierają się na wysyłaniu metod wirtualnych. W takich przypadkach należy użyć typów podkładek, jak opisano w [użyj podkładek, aby odizolować aplikację od innych zestawów do testowania jednostkowego](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="change-the-default-behavior-of-stubs"></a>Zmienianie domyślnego zachowania wycinków

Każdy wygenerowany typ skrótowy `IStubBehavior` zawiera wystąpienie interfejsu (za pośrednictwem `IStub.InstanceBehavior` właściwości). Zachowanie jest wywoływane za każdym razem, gdy klient wywołuje element członkowski, który nie ma dołączonego niestandardowego delegata. Jeśli zachowanie nie zostało ustawione, używa wystąpienia zwróconego `StubsBehaviors.Current` przez właściwość. Domyślnie ta właściwość zwraca zachowanie, `NotImplementedException` które zgłasza wyjątek.

Zachowanie można zmienić w dowolnym `InstanceBehavior` momencie, ustawiając właściwość na dowolnym wystąpieniu skrótu. Na przykład następujący fragment kodu zmienia zachowanie, które nic nie robi lub `default(T)`zwraca domyślną wartość typu zwracanego: :

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Zachowanie można również zmienić globalnie dla wszystkich obiektów skrótowych, `StubsBehaviors.Current` dla których zachowanie nie zostało ustawione przez ustawienie właściwości:

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Zobacz też

- [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
