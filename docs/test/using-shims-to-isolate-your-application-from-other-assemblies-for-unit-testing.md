---
title: Izolowanie aplikacji za pomocą podkładek (testy jednostkowe)
description: Dowiedz się, jak używać typów podkładek do przekierowania wywołań do określonych metod w celu pisania kodu w ramach testu. Podkładki mogą zwracać spójne wyniki przy każdym wywołaniu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 72a976ccd487abdfa2c6501c0dcafee07dc5f4ae
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042863"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Izolowanie aplikacji na użytek testów jednostkowych za pomocą podkładek

**Typy podkładek** są jedną z dwóch technologii, których używa Microsoft Fakes Framework, aby umożliwiać izolowanie testowanych składników od środowiska. Podkładki przekierowają wywołania określonych metod do kodu, który piszesz w ramach testu. Wiele metod zwraca różne wyniki zależne od warunków zewnętrznych, ale podkładki są pod kontrolą testu i mogą zwracać spójne wyniki przy każdym wywołaniu. Ułatwia to pisanie testów.

Użyj *podkładek,* aby odizolować kod od zestawów, które nie są częścią rozwiązania. Aby odizolować od siebie składniki rozwiązania, użyj *wycinki*.

Aby uzyskać omówienie i wskazówki dotyczące szybkiego startu, zobacz [Izolowanie](../test/isolating-code-under-test-with-microsoft-fakes.md)testowego kodu za pomocą Microsoft Fakes .

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework projektu
::: moniker range=">=vs-2019"
- Obsługa projektów w stylu platformy .NET Core, .NET 5.0 i ZESTAWU SDK w wersji zapoznawczej w wersji Visual Studio 2019 Update 6 i jest domyślnie włączona w aktualizacji Update 8. Aby uzyskać więcej informacji, zobacz Microsoft Fakes dla projektów w stylu [platformy .NET Core i zestawu SDK.](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)
::: moniker-end

## <a name="example-the-y2k-bug"></a>Przykład: usterka Y2K

Rozważmy metodę, która zgłasza wyjątek 1 stycznia 2000 r.:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testowanie tej metody jest problematyczne, ponieważ program zależy od metody , która zależy od zegara komputera, zależnej od środowiska, nie `DateTime.Now` deterministycznej metody. Ponadto obiekt jest właściwością statyczną, więc nie można w tym miejscu `DateTime.Now` użyć typu wycinki. Ten problem jest objawem problemu z izolacją w testach jednostkowych: programy, które bezpośrednio wywołują interfejsy API bazy danych, komunikują się z usługami internetowymi i tak dalej, są trudne do przetestowania jednostkowego, ponieważ ich logika zależy od środowiska.

W tym miejscu należy używać typów podkładek. Typy podkładek zapewniają mechanizm dekodowania dowolnej metody .NET do delegata zdefiniowanego przez użytkownika. Typy podkładek są generowane przez kod przez generator Fakes i używają delegatów, które nazywamy typami podkładek, do określania nowych implementacji metod.

Poniższy test pokazuje, jak używać podkładki typu , aby zapewnić niestandardową `ShimDateTime` implementację funkcji DateTime.Now:

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

## <a name="how-to-use-shims"></a>Jak używać podkładek

Najpierw dodaj zestaw Fakes:

1. W **Eksplorator rozwiązań**: 
    - W przypadku starszej wersji .NET Framework Project (styl bez zestawu SDK) rozwiń węzeł Odwołania projektu testu **jednostkowego.**
    ::: moniker range=">=vs-2019"
    - W przypadku projektu w stylu zestawu SDK przeznaczonego dla platformy .NET Framework, .NET  Core lub .NET 5.0 rozwiń węzeł Zależności, aby znaleźć zestaw, który chcesz sfałszować, w obszarze Zestawy,  **Projekty** lub **Pakiety**.
    ::: moniker-end
    - Jeśli pracujesz w programie Visual Basic,  wybierz pozycję Pokaż wszystkie pliki na pasku **Eksplorator rozwiązań** narzędzi, aby wyświetlić **węzeł Odwołania.**

2. Wybierz zestaw zawierający definicje klas, dla których chcesz utworzyć podkładki. Jeśli na przykład chcesz podkładki **DateTime**, wybierz pozycję **System.dll**.

3. W menu skrótów wybierz pozycję Add Fakes Assembly (Dodaj **zestaw fakes).**

### <a name="use-shimscontext"></a>Używanie podkładekContext

W przypadku używania typów podkładek w platformie testów jednostkowych opakuj kod testowy w ramce , aby kontrolować okres istnienia `ShimsContext` podkładek. W przeciwnym razie podkładki będą trwały do momentu zamknięcia elementu AppDomain. Najprostszym sposobem utworzenia klasy jest `ShimsContext` użycie metody `Create()` statycznej, jak pokazano w poniższym kodzie:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Ważne jest, aby prawidłowo usunąć każdy kontekst podkładki. Z reguły należy wywołać wewnątrz instrukcji , aby zapewnić prawidłowe wyczyszczenie zarejestrowanych `ShimsContext.Create` `using` podkładek. Na przykład możesz zarejestrować podkładki dla metody testowej, która zastępuje metodę delegatem, który zawsze zwraca pierwszy ze stycznia `DateTime.Now` 2000 r. Jeśli zapomnisz wyczyścić zarejestrowaną podkładkę w metodzie testowej, reszta testu zawsze zwróci wartość pierwszego stycznia 2000 `DateTime.Now` r. Może to być zaskakujące i mylące.

### <a name="write-a-test-with-shims"></a>Pisanie testu z podkładkami

W kodzie testowym wstaw *dekoniektę* dla metody, którą chcesz podszyć. Na przykład:

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

Nazwy klas podkładek składa się z `Fakes.Shim` prefiksu do oryginalnej nazwy typu.

Podkładki działają przez wstawienie *dekodatorów* do kodu testowej aplikacji. Wszędzie tam, gdzie wystąpi wywołanie oryginalnej metody, system Fakes wykonuje dekonwersję, dzięki czemu zamiast wywoływania metody rzeczywistej jest wywoływany kod podkładki.

Zwróć uwagę, że dekodowane elementy są tworzone i usuwane w czasie uruchamiania. Należy zawsze utworzyć dekoniektę w okresie życia `ShimsContext` . Po jego usunięciu wszystkie podkładki utworzone podczas jej działania są usuwane. Najlepszym sposobem na to jest wewnątrz `using` instrukcji .

Może zostać wyświetlony błąd kompilacji z informacją, że przestrzeń nazw Fakes nie istnieje. Ten błąd występuje czasami, gdy występują inne błędy kompilacji. Napraw inne błędy, które znikną.

## <a name="shims-for-different-kinds-of-methods"></a>Podkładki dla różnych rodzajów metod

Typy podkładek umożliwiają zastępowanie dowolnych metod platformy .NET, w tym metod statycznych lub niewirtualnych, własnymi delegatami.

### <a name="static-methods"></a>Metody statyczne

Właściwości dołączania podkładek do metod statycznych są umieszczane w typie podkładek. Każda właściwość ma tylko ustawiacz, który może służyć do dołączania delegata do metody docelowej. Na przykład, biorąc pod uwagę `MyClass` klasę z metodą statyczną `MyMethod` :

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Możemy dołączyć podkładki do , `MyMethod` która zawsze zwraca wartość 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody wystąpienia (dla wszystkich wystąpień)

Podobnie jak metody statyczne, metody wystąpień mogą być podkładki dla wszystkich wystąpień. Właściwości dołączania tych podkładek są umieszczane w zagnieżdżonych typach o nazwie AllInstances, aby uniknąć nieporozumień. Na przykład, biorąc pod uwagę `MyClass` klasę z metodą wystąpienia `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Możesz dołączyć podkładki do obiektu `MyMethod` , która zawsze zwraca wartość 5, niezależnie od wystąpienia:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Wygenerowana struktura typu ShimMyClass wygląda podobnie do następującego kodu:

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

Zauważ, że w tym przypadku środowisko Fakes przekazuje wystąpienie środowiska uruchomieniowego jako pierwszy argument delegata.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody wystąpienia (dla jednego wystąpienia środowiska uruchomieniowego)

Metody wystąpienia mogą być również podkładki przez różnych delegatów, w zależności od odbiornika wywołania. Dzięki temu ta sama metoda wystąpienia może mieć różne zachowania na wystąpienie typu. Właściwości do skonfigurowania tych podkładek to metody wystąpień typu podkładki. Każdy typ podkładki z wystąpieniami jest również skojarzony z nieprzetworzoną wystąpieniem typu podkładki.

Na przykład, biorąc pod uwagę `MyClass` klasę z metodą wystąpienia `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Możemy skonfigurować dwa typy podkładek MyMethod, tak aby pierwsza zawsze zwracała wartość 5, a druga zawsze zwraca wartość 10:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Wygenerowana struktura typu ShimMyClass wygląda podobnie do następującego kodu:

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

Dostęp do rzeczywistego wystąpienia typu podkładki można uzyskać za pośrednictwem właściwości Instance:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ podkładki ma również niejawną konwersję na typ podkładki, więc zazwyczaj można po prostu użyć typu podkładki w następujący sposób:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktory

Konstruktory można również podkładki w celu dołączenia typów podkładek do przyszłych obiektów. Każdy konstruktor jest ujmowany jako statyczny konstruktor metody w typie podkładki. Na przykład, biorąc pod uwagę `MyClass` klasę z konstruktorem, który przyjmuje liczbę całkowitą:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Typ podkładki konstruktora jest konstruowany tak, aby każde przyszłe wystąpienie zwracało wartość -5 po wywołaniu metody getter wartości, niezależnie od wartości w konstruktorze:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Każdy typ podkładki uwidacznia dwa konstruktory. Konstruktor domyślny powinien być używany, gdy potrzebne jest nowe wystąpienie, a konstruktor, który przyjmuje wystąpienie podkładki jako argument, powinien być używany tylko w podkładce konstruktora:

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

### <a name="base-members"></a>Podstawowe składowe

Do właściwości podkładek podstawowych składowych można uzyskać dostęp, tworząc podkładkę dla typu podstawowego i przekazując wystąpienie podrzędne jako parametr do konstruktora klasy podstawowej podkładki.

Na przykład, mając `MyBase` klasę z metodą wystąpienia `MyMethod` i podtypem `MyChild` :

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Podkładki możemy `MyBase` skonfigurować, tworząc nową `ShimMyBase` podkładki:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Należy pamiętać, że typ podkładki podrzędnej jest niejawnie konwertowany na wystąpienie podrzędne, gdy jest przekazywany jako parametr do podstawowego konstruktora podkładki.

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

Typy podkładek uwidoczniają statyczną `StaticConstructor` metodę podkładki statycznego konstruktora typu. Ponieważ konstruktory statyczne są wykonywane tylko raz, należy się upewnić, że podkładka jest skonfigurowana przed dostępem do dowolnego członka typu.

### <a name="finalizers"></a>Finalizatory

Finalizery nie są obsługiwane w przypadku fałszywych.

### <a name="private-methods"></a>Metody prywatne

Generator kodu Fakes tworzy właściwości podkładki dla metod prywatnych, które mają tylko typy widoczne w sygnaturze, czyli typy parametrów i typ zwracany są widoczne.

### <a name="binding-interfaces"></a>Interfejsy powiązania

Gdy typ podkładki implementuje interfejs, generator kodu emituje metodę, która umożliwia powiązanie wszystkich elementów członkowskich z tego interfejsu jednocześnie.

Na przykład, biorąc pod uwagę `MyClass` klasę, która implementuje `IEnumerable<int>` klasę :

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Implementacje klasy w myclass można `IEnumerable<int>` podkładki, wywołując metodę Bind:

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

## <a name="change-the-default-behavior"></a>Zmienianie domyślnego zachowania

Każdy wygenerowany typ podkładki zawiera wystąpienie `IShimBehavior` interfejsu za pośrednictwem `ShimBase<T>.InstanceBehavior` właściwości . To zachowanie jest używane za każdym razem, gdy klient wywołuje element członkowski wystąpienia, który nie został jawnie podkładki.

Jeśli zachowanie nie zostało jawnie ustawione, używa wystąpienia zwróconego przez właściwość `ShimBehaviors.Current` statyczną. Domyślnie ta właściwość zwraca zachowanie, które zgłasza `NotImplementedException` wyjątek.

To zachowanie można zmienić w dowolnym momencie, ustawiając właściwość `InstanceBehavior` na dowolnym wystąpieniu podkładki. Na przykład poniższy fragment kodu zmienia podkładki na zachowanie, które nic nie robi lub zwraca wartość domyślną zwracanej typu — czyli `default(T)` :

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimBehaviors.DefaultValue;
```

Zachowanie można również zmienić globalnie dla wszystkich wystąpień podkładek, dla których właściwość nie została jawnie ustawiona przez `InstanceBehavior` ustawienie właściwości `ShimBehaviors.Current` statycznej:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimBehaviors.Current = ShimBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Wykrywanie dostępu do środowiska

Istnieje możliwość dołączenia zachowania do wszystkich elementów członkowskich, w tym metod statycznych, określonego typu przez przypisanie zachowania do właściwości statycznej odpowiedniego typu `ShimBehaviors.NotImplemented` `Behavior` podkładki:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Współbieżność

Typy podkładek mają zastosowanie do wszystkich wątków w domenie Aplikacji i nie mają koligacji wątku. Jest to ważny fakt, jeśli planujesz używać programu do testowania, który obsługuje współbieżność. Testy obejmujące typy podkładek nie mogą być uruchamiane współbieżnie. Ta właściwość nie jest wymuszana przez środowisko uruchomieniowe fakes.

## <a name="call-the-original-method-from-the-shim-method"></a>Wywołanie oryginalnej metody z metody podkładki

Wyobraź sobie, że chcesz zapisać tekst w systemie plików po walidacji nazwy pliku przekazanej do metody . W takim przypadku należy wywołać oryginalną metodę w środku metody podkładki.

Pierwszym podejściem do rozwiązania tego problemu jest zawijanie wywołania oryginalnej metody przy użyciu delegata i `ShimsContext.ExecuteWithoutShims()` , jak w poniższym kodzie:

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

Innym podejściem jest ustawienie podkładki na wartość null, wywołanie oryginalnej metody i przywrócenie podkładki.

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

## <a name="systemenvironment"></a>System.Environment

Aby podkładki <xref:System.Environment?displayProperty=fullName> , dodaj następującą zawartość do pliku mscorlib.fakes po **elemencie Assembly:**

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po odbudowaniu rozwiązania metody i właściwości w klasie są dostępne do <xref:System.Environment?displayProperty=fullName> podkładki, na przykład:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Ograniczenia

Podkładki nie mogą być używane we wszystkich typach z biblioteki klas bazowych .NET **mscorlib** i **System** w programie .NET Framework oraz w środowisku **System.Runtime** na .NET Core lub .NET 5.0.

## <a name="see-also"></a>Zobacz też

- [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog Petera Provosta: Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Wideo (1h16): Testing untestable code with fakes in Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
