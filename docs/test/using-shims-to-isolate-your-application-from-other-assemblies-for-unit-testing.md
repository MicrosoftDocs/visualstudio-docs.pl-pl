---
title: Używanie podkładek do izolowania aplikacji do testowania jednostkowego
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 480283b4f86f28fdedfb38687682fcee4e67646e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585538"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Używanie podkładek do izolowania aplikacji do testowania jednostek

**Typy podkładek** są jedną z dwóch technologii, które microsoft fakes framework używa do umożliwienia izolowania składników w fazie testów ze środowiska. Podkładki przekierowują wywołania do określonych metod do kodu, który piszesz w ramach testu. Wiele metod zwraca różne wyniki w zależności od warunków zewnętrznych, ale podkładka jest pod kontrolą testu i może zwracać spójne wyniki przy każdym wywołaniu. Ułatwia to pisanie testów.

Użyj *podkładek,* aby wyizolować kod od zestawów, które nie są częścią rozwiązania. Aby odizolować składniki rozwiązania od siebie, należy użyć *wycinków*.

Aby uzyskać omówienie i wskazówki dotyczące "szybkiego startu", zobacz [Izolowanie kodu w fazie testów za pomocą microsoft fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework

> [!NOTE]
> Projekty .NET Standard nie są obsługiwane.

## <a name="example-the-y2k-bug"></a>Przykład: błąd Y2K

Należy wziąć pod uwagę metodę, która zgłasza wyjątek w dniu 1 stycznia 2000 r.:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testowanie tej metody jest problematyczne, ponieważ program zależy `DateTime.Now`od metody, która zależy od zegara komputera, metody nieokreślajnej zależnej od środowiska. Ponadto `DateTime.Now` jest właściwością statyczną, więc typ skrótowy nie może być w tym miejscu używany. Ten problem jest objawem problemu izolacji w testowaniu jednostkowym: programy, które bezpośrednio wywołują interfejsy API bazy danych, komunikują się z usługami sieci web i tak dalej, są trudne do przetestowania jednostkowego, ponieważ ich logika zależy od środowiska.

W tym miejscu należy stosować typy podkładek. Typy podkładek zapewniają mechanizm do objazdu dowolnej metody .NET do delegata zdefiniowanego przez użytkownika. Typy podkładek są generowane przez generator fakes i używają delegatów, które nazywamy typami podkładek, aby określić nowe implementacje metody.

Poniższy test pokazuje, jak używać `ShimDateTime`typu podkładki, aby zapewnić niestandardową implementację DateTime.Now:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>Jak używać podkładek regulacyjnych

Najpierw dodaj zestaw Podróbek:

1. W **Eksploratorze rozwiązań**rozwiń węzeł **Odwołania** projektu testowego.

   - Jeśli pracujesz w języku Visual Basic, wybierz pozycję **Pokaż wszystkie pliki** na pasku narzędzi **Eksploratora rozwiązań,** aby wyświetlić węzeł **Odwołania.**

2. Wybierz zestaw zawierający definicje klas, dla których chcesz utworzyć podkładki. Na przykład, jeśli chcesz podkładać **DateTime,** wybierz **system.dll**.

3. W menu skrótów wybierz polecenie **Dodaj zestaw podróbek**.

### <a name="use-shimscontext"></a>Użyj podkładki ShimsContext

Podczas korzystania z typów podkładki w ramach testów `ShimsContext` jednostkowych, zawijać kod testu w a kontrolować okres istnienia podkładek. W przeciwnym razie podkładki będzie trwać do AppDomain zamknięty. Najprostszym sposobem utworzenia `ShimsContext` a jest użycie `Create()` metody statycznej, jak pokazano w poniższym kodzie:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Bardzo ważne jest, aby prawidłowo dysponować każdym kontekstem podkładki. Zgodnie z ogólną zasadą, zadzwoń do `ShimsContext.Create` wnętrza `using` oświadczenia, aby zapewnić prawidłowe wyczyszczenie zarejestrowanych podkładek. Na przykład można zarejestrować podkładkę dla metody testowej, która zastępuje `DateTime.Now` metodę delegatem, który zawsze zwraca pierwszy stycznia 2000. Jeśli zapomnisz wyczyścić zarejestrowaną podkładki w metodzie testowej, reszta przebiegu testowego zawsze `DateTime.Now` zwróci pierwszą z stycznia 2000 r. jako wartość. Może to być zaskakujące i mylące.

### <a name="write-a-test-with-shims"></a>Napisz test z podkładkami

W kodzie testowym wstaw *objazd* dla metody, którą chcesz sfałszować. Przykład:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet =
                () =>
                { return new DateTime(fixedYear, 1, 1); };

                // Instantiate the component under test:
                var componentUnderTest = new MyComponent();

              // Act:
                int year = componentUnderTest.GetTheCurrentYear();

              // Assert:
                // This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year);
            }
        }
}
```

```vb
<TestClass()> _
Public Class TestClass1
    <TestMethod()> _
    Public Sub TestCurrentYear()
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
            Dim fixedYear As Integer = 2000
            ' Arrange:
            ' Detour DateTime.Now to return a fixed date:
            System.Fakes.ShimDateTime.NowGet = _
                Function() As DateTime
                    Return New DateTime(fixedYear, 1, 1)
                End Function

            ' Instantiate the component under test:
            Dim componentUnderTest = New MyComponent()
            ' Act:
            Dim year As Integer = componentUnderTest.GetTheCurrentYear
            ' Assert:
            ' This will always be true if the component is working:
            Assert.AreEqual(fixedYear, year)
        End Using
    End Sub
End Class
```

Nazwy klas podkładek shim są `Fakes.Shim` składane przez prefiks do oryginalnej nazwy typu.

Podkładki działają, wstawiając *objazdy* do kodu testowej aplikacji. Wszędzie tam, gdzie występuje wywołanie oryginalnej metody, system Fakes wykonuje objazd, dzięki czemu zamiast wywoływania prawdziwej metody, wywoływany jest kod podkładki.

Należy zauważyć, że objazdy są tworzone i usuwane w czasie wykonywania. Zawsze należy utworzyć objazd w życiu `ShimsContext`. Po usunięciu wszystkie podkładki utworzone podczas aktywności są usuwane. Najlepszym sposobem, aby to `using` zrobić jest wewnątrz instrukcji.

Może zostać wyświetlony błąd kompilacji stwierdzający, że obszar nazw Podróbki nie istnieje. Ten błąd czasami pojawia się, gdy istnieją inne błędy kompilacji. Napraw inne błędy i zniknie.

## <a name="shims-for-different-kinds-of-methods"></a>Podkładki do różnych rodzajów metod

Typy podkładek umożliwiają zastąpienie dowolnej metody .NET, w tym metod statycznych lub metod niewirtualnych, własnymi delegatami.

### <a name="static-methods"></a>Metody statyczne

Właściwości dołączania podkładek do metod statycznych są umieszczane w typie podkładki. Każda właściwość ma tylko ustawiacz, który może służyć do dołączenia delegata do metody docelowej. Na przykład, biorąc `MyClass` pod uwagę `MyMethod`klasę z metodą statyczną:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Możemy dołączyć podkładkę `MyMethod` do tego zawsze zwraca 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody wystąpienia (dla wszystkich wystąpień)

Podobnie jak metody statyczne, metody wystąpienia mogą być shimmed dla wszystkich wystąpień. Właściwości do dołączenia tych podkładek są umieszczane w typie zagnieżdżonym o nazwie AllInstances, aby uniknąć nieporozumień. Na przykład, biorąc `MyClass` pod uwagę `MyMethod`klasę z metodą wystąpienia:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Można dołączyć podkładkę `MyMethod` do tego zawsze zwraca 5, niezależnie od wystąpienia:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Wygenerowana struktura typu ShimMyClass wygląda następująco:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Należy zauważyć, że podróbki przekazuje wystąpienie środowiska uruchomieniowego jako pierwszy argument delegata w tym przypadku.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody wystąpienia (dla jednego wystąpienia środowiska uruchomieniowego)

Metody wystąpienia mogą być również shimmed przez różnych delegatów, na podstawie odbiornika wywołania. Dzięki temu ta sama metoda wystąpienia mieć różne zachowania na wystąpienie typu. Właściwości, aby skonfigurować te podkładki są metody wystąpienia samego typu podkładki. Każdy typ podkładki shim wystąpienia jest również skojarzony z nieprzetworzonym wystąpieniem typu shimmed.

Na przykład, biorąc `MyClass` pod uwagę `MyMethod`klasę z metodą wystąpienia:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Możemy skonfigurować dwa typy podkładek MyMethod w taki sposób, że pierwszy zawsze zwraca 5, a drugi zawsze zwraca 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Wygenerowana struktura typu ShimMyClass wygląda następująco:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

Rzeczywiste shimmed wystąpienia typu można uzyskać za pośrednictwem instance właściwości:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ podkładki ma również niejawną konwersję do typu shimmed, więc zwykle można po prostu użyć typu podkładki, jak jest:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktorów

Konstruktory mogą być również shimmed w celu dołączenia typów podkładki do przyszłych obiektów. Każdy konstruktor jest narażony jako metoda statyczna Konstruktor w typie podkładki. Na przykład biorąc `MyClass` pod uwagę klasę z konstruktora biorący całkowitą:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Ustawiliśmy typ podkładki konstruktora tak, aby każde przyszłe wystąpienie zwracało wartość -5, gdy wywoływana jest funkcja obliczania wartości, niezależnie od wartości w konstruktorze:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Każdy typ podkładki udostępnia dwa konstruktory. Domyślny konstruktor powinien być używany, gdy potrzebne jest świeże wystąpienie, podczas gdy konstruktor biorący shimmed wystąpienie jako argument powinien być używany tylko w podkładkach konstruktora:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Wygenerowana struktura typu ShimMyClass przypomina następujący kod:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>Elementy podstawowe

Właściwości podkładki podstawowych elementów członkowskich można uzyskać, tworząc podkładkę dla typu podstawowego i przekazując wystąpienie podrzędne jako parametr do konstruktora klasy podkładki bazowej.

Na przykład, biorąc `MyBase` pod uwagę `MyMethod` klasę z `MyChild`metodą wystąpienia i podtypem:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Możemy skonfigurować `MyBase` podkładkę, tworząc nową `ShimMyBase` podkładkę:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Należy zauważyć, że typ podkładki podrzędnej jest niejawnie konwertowany na wystąpienie podrzędne, gdy jest przekazywany jako parametr do konstruktora podkładki podstawowej.

Wygenerowana struktura typu ShimMyChild i ShimMyBase przypomina następujący kod:

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>Konstruktory statyczne

Typy podkładek uwidaczniają metodę `StaticConstructor` statyczną do podkładki statycznego konstruktora typu. Ponieważ konstruktory statyczne są wykonywane tylko raz, należy upewnić się, że podkładka jest skonfigurowana przed dostępem do dowolnego elementu członkowskiego typu.

### <a name="finalizers"></a>Finalizatory

Finalizatory nie są obsługiwane w podróbki.

### <a name="private-methods"></a>Metody prywatne

Generator kodu Fakes tworzy właściwości podkładki dla metod prywatnych, które mają tylko widoczne typy w podpisie, czyli typy parametrów i typ zwracany widoczne.

### <a name="binding-interfaces"></a>Interfejsy wiązania

Gdy typ shimmed implementuje interfejs, generator kodu emituje metodę, która pozwala na powiązanie wszystkich elementów członkowskich z tego interfejsu naraz.

Na przykład, biorąc `MyClass` pod `IEnumerable<int>`uwagę klasę, która implementuje:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Można podkładka implementacje `IEnumerable<int>` w MyClass wywołując Bind metody:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Wygenerowana struktura typu ShimMyClass przypomina następujący kod:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Zmienianie zachowania domyślnego

Każdy wygenerowany typ podkładki `IShimBehavior` zawiera wystąpienie `ShimBase<T>.InstanceBehavior` interfejsu, za pośrednictwem właściwości. Zachowanie jest używane za każdym razem, gdy klient wywołuje element członkowski wystąpienia, który nie został jawnie shimmed.

Jeśli zachowanie nie zostało jawnie ustawione, używa wystąpienia zwróconego `ShimsBehaviors.Current` przez właściwość statyczną. Domyślnie ta właściwość zwraca zachowanie, `NotImplementedException` które zgłasza wyjątek.

To zachowanie można zmienić w `InstanceBehavior` dowolnym momencie, ustawiając właściwość na dowolnym wystąpieniu podkładki. Na przykład poniższy fragment kodu zmienia podkładkę na zachowanie, które nic nie robi lub zwraca `default(T)`domyślną wartość typu zwracanego , czyli:

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Zachowanie można również zmienić globalnie dla wszystkich shimmed wystąpień, dla których `InstanceBehavior` `ShimsBehaviors.Current` właściwość nie została jawnie ustawiona przez ustawienie właściwości statycznej:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Wykrywanie dostępu do środowiska

Istnieje możliwość dołączenia zachowania do wszystkich elementów członkowskich, w tym metod `ShimsBehaviors.NotImplemented` statycznych, określonego `Behavior` typu, przypisując zachowanie do właściwości statycznej odpowiedniego typu podkładki:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Współbieżność

Typy podkładek mają zastosowanie do wszystkich wątków w AppDomain i nie mają koligacji wątku. Jest to ważny fakt, jeśli planujesz użyć potoku testów, który obsługuje współbieżność. Testy obejmujące typy podkładek nie można uruchomić jednocześnie. Ta właściwość nie jest wymuszana przez środowisko uruchomieniowe Fakes.

## <a name="call-the-original-method-from-the-shim-method"></a>Wywołanie oryginalnej metody z metody podkładki

Wyobraź sobie, że chcesz napisać tekst do systemu plików po sprawdzeniu poprawności nazwy pliku przekazanej do metody. W takim przypadku należy wywołać oryginalną metodę w środku metody podkładki.

Pierwszym podejściem do rozwiązania tego problemu jest zawijanie wywołania oryginalnej metody przy użyciu pełnomocnika i `ShimsContext.ExecuteWithoutShims()`, jak w poniższym kodzie:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Innym podejściem jest ustawienie podkładki na null, wywołanie oryginalnej metody i przywrócenie podkładki.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System.Środowisko

Aby podkładka <xref:System.Environment?displayProperty=fullName>, dodać następującą zawartość do pliku mscorlib.fakes po **Assembly** element:

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po przebudowie rozwiązania, metody i właściwości <xref:System.Environment?displayProperty=fullName> w klasie są dostępne do shimmed, na przykład:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Ograniczenia

Podkładek nie można używać we wszystkich typach z biblioteki klasy podstawowej .NET **mscorlib** i **System**.

## <a name="see-also"></a>Zobacz też

- [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog Petera Provosta: Podkładki Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Klip wideo (1h16): Testowanie niesprawdzonego kodu z podróbkami w programie Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
