---
title: Stosowanie wycinków kodu do izolowania poszczególnych części aplikacji od siebie nawzajem testów jednostkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 73519dd9-f3d5-49b6-a634-38881b459ea4
caps.latest.revision: 19
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7d0165c0a774ba53e5ce4798cdcd4bc4755d1ebd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145164"
---
# <a name="using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Stosowanie wycinków kodu do izolowania od siebie poszczególnych części aplikacji w celu przeprowadzania testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy wycinka * są jedną z dwóch technologii, które zapewnia Microsoft Fakes framework, które ułatwiają izolowanie testowanego od innych składników, które wywołuje składnik. Odcinek jest niewielkim fragmentem kodu, który zajmuje miejsce innego składnika podczas testu. Korzyścią wynikającą z zastosowania wycinka są spójne wyniki, co ułatwia tworzenie testów. Testy można będzie uruchomić, nawet jeśli inne składniki jeszcze nie działają.  
  
 Aby uzyskać omówienie i szybki start do środowiska Fakes, zobacz [izolując kod w ramach testu, with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
 Aby użyć wycinków, trzeba napisać składnik w taki sposób, aby korzystał tylko z interfejsów, a nie z klas, i odwoływał się do innych części aplikacji. To dobra praktyka tworzenia projektów, ponieważ zmiany są wprowadzane tylko w jednej części i jest mniej prawdopodobne, że inne również będą wymagać zmian. Do celów testowych pozwala zastąpić wycinkiem rzeczywisty składnik.  
  
 Na diagramie składnikiem StockAnalyzer jest ten, który chcemy przetestować. Zwykle używa on innego składnika RealStockFeed. RealStockFeed zwraca jednak różne wyniki przy każdym wywołaniu jego metod, co utrudnia test StockAnalyzer.  Podczas testowania można zastąpić go inną klasą StubStockFeed.  
  
 ![Real a klasy wycinka jest zgodna z jednego interfejsu. ](../test/media/fakesinterfaces.png "FakesInterfaces")  
  
 Wycinki opierają się w ten sposób na swoich możliwościach bycia strukturą kodu, dlatego zwykle są one używane w celu wyizolowania jednej strony aplikacji z innej. Aby odłączyć je od innych zestawów niebędących pod kontrolą, takich jak System.dll, normalnie zostałyby użyte podkładki. Zobacz [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  
  
 **Wymagania**  
  
-   Visual Studio Enterprise
  
##  <a name="How"></a> Jak używać wycinków  
  
###  <a name="Dependency"></a> Zaprojektowane do wstrzykiwania zależności  
 Aby korzystać z wycinków, aplikacja musi być tak zaprojektowana, aby różne składniki nie były zależne od siebie, ale tylko od definicji interfejsu. Zamiast być połączone w czasie kompilacji, składniki są połączone w czasie wykonywania. Ten wzór pomaga stworzyć oprogramowanie, które będzie niezawodne i łatwe do zaktualizowania, ponieważ zmiany zwykle nie są propagowane przez granice składnika. Zalecamy następujące działanie, nawet jeśli użytkownik nie używa wycinków. Jeśli piszesz nowy kod jest łatwe naśladowanie [wstrzykiwanie zależności](http://en.wikipedia.org/wiki/Dependency_injection) wzorca. Jeśli piszesz testy dla istniejącego oprogramowania, możliwe, że trzeba będzie je refraktoryzować. Jeżeli byłoby to niepraktyczne, można rozważyć użycie zamiast niego podkładki.  
  
 Zacznijmy tę dyskusję od motywującego przykładu, takiego jak ten na diagramie. Klasa, którą odczytuje StockAnalyzer, udostępnia ceny i generuje interesujące wyniki. Obejmuje ona niektóre metody publiczne, które chcemy sprawdzić. Aby zachować ich prostotę, po prostu przyjrzyjmy się jednej z tych metod — bardzo prostej — która zgłasza aktualną cenę udziału. Chcemy napisać test jednostkowy tej metody. Oto pierwszy projekt testu:  
  
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
  
 Innym problemem może być to, że składnik StockFeed, który jest używany przez StockAnalyzer, jest wciąż w fazie opracowywania. Oto pierwszy projekt kodu testowanej metody:  
  
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
  
 W obecnym stanie metoda ta nie może kompilować lub może zgłosić wyjątek, ponieważ praca w klasie StockFeed nie została jeszcze zakończona.  
  
 Wstrzyknięcie interfejsu rozwiązuje oba te problemy.  
  
 Wstrzyknięcie interfejsu wykorzystuje następującą regułę:  
  
- Kod jakiegokolwiek składnika aplikacji nigdy w sposób jawny powinni zapoznać się z klasą w innym składniku, deklaracji lub w `new` instrukcji. Zamiast tego zmienne i parametry powinny być zadeklarowane razem z interfejsami. Wystąpienia składnika powinny być tworzone tylko przez kontener składnika.  
  
   Przez „składnik” w tym przypadku rozumie się klasę lub grupę klas, które można dopracowywać i aktualizować łącznie. Składnikiem jest zazwyczaj kod w jednym projekcie programu Visual Studio. Rozdzielenie klas w obrębie jednego składnika nie jest zbyt ważne, ponieważ są one aktualizowane w tym samym czasie.  
  
   Oddzielenie składników od klas stosunkowo stabilnej platformy, takiej jak System.dll, również nie jest zbyt istotne. Pisanie interfejsów dla wszystkich tych klas spowodowałoby zaśmiecenie kodu.  
  
  Kod StockAnalyzer można zatem poprawić przez oddzielenie go od StockFeed przy użyciu interfejsu, takiego jak:  
  
```csharp  
public interface IStockFeed  
{  
    int GetSharePrice(string company);  
}  
  
public class StockAnalyzer  
{  
    private IStockFeed stockFeed;  
    public Analyzer(IStockFeed feed)  
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
  
```  
analyzer = new StockAnalyzer(new StockFeed())  
```  
  
 Istnieją bardziej elastyczne sposoby wykonywania tego połączenia. Na przykład StockAnalyzer może zaakceptować obiekt fabryki, który może utworzyć wystąpienie różnych implementacji IStockFeed w różnych warunkach.  
  
###  <a name="GeneratingStubs"></a> Generuj szablony  
 Klasa, którą chcesz przetestować, została odłączona od innych składników, z których korzysta. Oddzielenie powoduje, że aplikacja staje się bardziej solidna i elastyczna, a ponadto pozwala połączyć składnik testu z implementacją wycinka w ramach testowania interfejsów.  
  
 Można po prostu zwyczajnie napisać wycinki jako klasy. Jednak środowisko Microsoft Fakes zapewnia bardziej dynamiczny sposób tworzenia najodpowiedniejszych wycinków dla każdego testu.  
  
 Aby użyć wycinków, należy najpierw wygenerować typy wycinków z definicji interfejsu.  
  
##### <a name="adding-a-fakes-assembly"></a>Dodawanie podrobionych zestawów  
  
1.  W Eksploratorze rozwiązań rozwiń projekt testów jednostkowych **odwołania**.  
  
    -   Jeśli pracujesz w języku Visual Basic, musisz wybrać **Pokaż wszystkie pliki** na pasku narzędzi Eksploratora rozwiązań, aby zobaczyć listę odwołań.  
  
2.  Wybierz zestaw zawierający definicje interfejsu, dla których chcesz utworzyć wycinki.  
  
3.  W menu skrótów wybierz **Dodaj zestawy Substytuowane**.  
  
###  <a name="WriteTest"></a> Napisz test z wycinkami  
  
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
  
 Specjalną funkcję PE łni tutaj jest klasą `StubIStockFeed`. Dla każdego typu publicznego w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę wycinków. Nazwa klasy wycinka jest tworzona od nazwy interfejsu, z "`Fakes.Stub`" jako prefiksem i dołączonymi nazwami typu parametru.  
  
 Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych.  
  
###  <a name="mocks"></a> Weryfikowanie wartości parametrów  
 Można zweryfikować, że jeżeli składnik wywołuje inny składnik, przekazuje poprawne wartości. Teraz można umieścić potwierdzenie w wycinku lub przechowywać wartość i weryfikować ją w głównej części testu. Na przykład:  
  
```csharp  
[TestClass]  
class TestMyComponent  
{  
  
    [TestMethod]  
    public void TestVariableContosoPrice()  
    {  
     // Arrange:  
        int priceToReturn;  
        string companyCodeUsed;  
        var componentUnderTest = new StockAnalyzer(new StubIStockFeed()  
            {  
               GetSharePriceString = (company) =>   
                  {   
                     // Store the parameter value:  
                     companyCodeUsed = company;  
                     // Return the value prescribed by this test:  
                     return priceToReturn;  
                  };  
            };  
        // Set the value that will be returned by the stub:  
        priceToReturn = 345;  
  
     // Act:  
        int actualResult = componentUnderTest.GetContosoPrice();  
  
     // Assert:  
        // Verify the correct result in the usual way:  
        Assert.AreEqual(priceToReturn, actualResult);  
  
        // Verify that the component made the correct call:  
        Assert.AreEqual("COOO", companyCodeUsed);  
    }  
...}  
  
```  
  
```vb  
<TestClass()> _  
Class TestMyComponent  
    <TestMethod()> _  
    Public Sub TestVariableContosoPrice()  
        ' Arrange:  
        Dim priceToReturn As Integer  
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
        ' Set the value that will be returned by the stub:  
        priceToReturn = 345  
  
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
  
##  <a name="BKMK_Stub_basics"></a> Wycinki dla różnych rodzajów elementów członkowskich typu  
  
###  <a name="BKMK_Methods"></a> Metody  
 Jak opisano w przykładzie, metody można dzielić na wycinki, dołączając delegata do instancji klasy wycinka. Nazwa typu wycinka pochodzi od nazwy metody i parametrów. Na przykład, biorąc pod uwagę następujące `IMyInterface` interfejsu i metoda `MyMethod`:  
  
```csharp  
// application under test  
interface IMyInterface   
{  
    int MyMethod(string value);  
}  
```  
  
 Dołączamy odcinek do `MyMethod` zawsze zwraca 1:  
  
```csharp  
// unit test code  
  var stub = new StubIMyInterface ();  
  stub.MyMethodString = (value) => 1;  
  
```  
  
 Jeśli nie podano wycinka dla funkcji, środowisko Fakes wygeneruje funkcję zwracającą wartość domyślną typu zwracanego. W przypadku liczb, wartością domyślną jest 0, a dla typów klasy jest `null` (C#) lub `Nothing` (Visual Basic).  
  
###  <a name="BKMK_Properties"></a> Właściwości  
 Metody pobierające i ustawiające są widoczne jako oddzielne delegaty i mogą tworzyć poszczególne wycinki. Na przykład, rozważmy `Value` właściwość `IMyInterface`:  
  
```csharp  
// code under test  
interface IMyInterface   
{  
    int Value { get; set; }  
}  
  
```  
  
 Dołączyć delegaty do metod pobierających i ustawiających `Value` aby symulować auto właściwości:  
  
```csharp  
// unit test code  
int i = 5;  
var stub = new StubIMyInterface();  
stub.ValueGet = () => i;  
stub.ValueSet = (value) => i = value;  
  
```  
  
 Jeśli nie podano metody zastępczej ani dla metod ustawiających, ani pobierających właściwości, środowisko Fakes wygeneruje odcinek, który przechowuje wartości, tak aby właściwość zastępcza działała jak prosta zmienna.  
  
###  <a name="BKMK_Events"></a> Zdarzenia  
 Zdarzenia są uwidocznione jako pola delegatów. W rezultacie wszystkie zdarzenia przekształcone na wycinki mogą być łatwo wywoływane przez wywołanie zdarzenia pola pomocniczego. Rozważmy następujący interfejs do przekształcenia na wycinki:  
  
```csharp  
// code under test  
interface IWithEvents   
{  
    event EventHandler Changed;  
}  
```  
  
 Aby podnieść `Changed` zdarzenie, po prostu wywołać pomocniczego delegata:  
  
```csharp  
// unit test code  
  var withEvents = new StubIWithEvents();  
  // raising Changed  
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);  
  
```  
  
###  <a name="BKMK_Generic_methods"></a> Metody ogólne  
 Istnieje możliwość tworzenia wycinków dla metod ogólnych poprzez dostarczenie delegata dla każdego żądanego wystąpienia metody. Na przykład, biorąc pod uwagę następujący interfejs, zawierający metodę ogólną:  
  
```csharp  
// code under test  
interface IGenericMethod   
{  
    T GetValue<T>();  
}  
```  
  
 Można napisać test, który tworzy wycinki `GetValue<int>` podczas tworzenia wystąpienia:  
  
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
  
 Jeśli w kodzie nastąpi wywołanie `GetValue<T>` z jakimkolwiek innym wystąpieniem wycinka po prostu wywoła dane zachowanie.  
  
###  <a name="BKMK_Partial_stubs"></a> Wycinki wirtualnych klas  
 W poprzednich przykładach wycinki zostały wygenerowane z interfejsów. Można również wygenerować wycinki z klasy, która ma składowe virtual lub abstract. Na przykład:  
  
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
  
 W wycinku wygenerowanym z tej klasy można ustawić metody delegowane dla DoAbstract() i DoVirtual(), ale nie DoConcrete().  
  
```csharp  
// unit test  
  var stub = new Fakes.MyClass();  
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };  
  stub.DoVirtualInt32 = (n) => 10 ;  
  
```  
  
 Jeśli nie podasz delegata dla metody wirtualnej, środowisko Fakes może zapewnić zachowanie domyślne albo wywoływać metodę w klasie bazowej. Aby mieć podstawowej metody nazwanej, należy ustawić `CallBase` właściwości:  
  
```csharp  
// unit test code  
var stub = new Fakes.MyClass();  
stub.CallBase = false;  
// No delegate set – default delegate:  
Assert.AreEqual(0, stub.DoVirtual(1));  
  
stub.CallBase = true;  
//No delegate set - calls the base:  
Assert.AreEqual(43,stub.DoVirtual(1));  
```  
  
##  <a name="BKMK_Debugging_stubs"></a> Debugowanie wycinków  
 Typy wycinków zostały tak zaprojektowane, aby zapewniać płynność debugowania. Domyślnie debuger pomija kod generowany, powinien więc wejść bezpośrednio do niestandardowych implementacji elementu członkowskiego, które zostały dołączone do wycinka.  
  
##  <a name="BKMK_Stub_limitation"></a> Ograniczenia dotyczące wycinka  
  
1.  Podpisy metod ze wskaźnikami nie są obsługiwane.  
  
2.  Zapieczętowane klasy lub metody statyczne nie mogą zostać przekształcone na wycinki, ponieważ typy wycinka opierają się na wysyłaniu wirtualnej metody. W takich przypadkach używać typów podkładek, zgodnie z opisem w [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
##  <a name="BKMK_Changing_the_default_behavior_of_stubs"></a> Zmiana domyślnego zachowania wycinków  
 Każdy wygenerowany typ wycinka posiada wystąpienie `IStubBehavior` interfejsu (za pośrednictwem `IStub.InstanceBehavior` właściwości). Zachowanie jest wywoływane za każdym razem, gdy klient wywołuje element członkowski, który nie ma dołączonego niestandardowego delegata. Jeśli nie ustawiono zachowania, zostanie użyty wystąpienie zwrócone przez `StubsBehaviors.Current` właściwości. Domyślnie właściwość ta zwraca zachowanie, które zgłasza `NotImplementedException` wyjątku.  
  
 To zachowanie można zmienić w dowolnym momencie przez ustawienie `InstanceBehavior` właściwości na dowolnym wystąpieniu wycinka. Na przykład poniższa Wstawka kodu zmienia zachowanie, które nie działa lub zwraca wartość domyślną typu zwracanego: `default(T)`:  
  
```csharp  
// unit test code  
var stub = new StubIFileSystem();  
// return default(T) or do nothing  
stub.InstanceBehavior = StubsBehaviors.DefaultValue;  
```  
  
 To zachowanie można także zmienić globalnie dla wszystkich obiektów, dla których zachowanie nie zostało ustawione przez ustawienie zastąpić klasą zastępczą `StubsBehaviors.Current` właściwości:  
  
```csharp  
// unit test code  
//change default behavior for all stub instances  
//where the behavior has not been set  
StubBehaviors.Current =   
    BehavedBehaviors.DefaultValue;  
```  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
