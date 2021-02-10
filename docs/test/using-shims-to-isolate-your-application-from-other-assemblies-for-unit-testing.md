---
title: Izolowanie aplikacji za pomocą podkładki (testy jednostkowe)
description: Dowiedz się, jak używać typów podkładki do przewrócenia wywołań do określonych metod w kodzie, który piszesz jako część testu. Podkładka może zwracać spójne wyniki przy każdym wywołaniu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: f15af6958c7f5855b5005fc0a6aa4c821346ccb5
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006403"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Używanie podkładki do izolowania aplikacji do testów jednostkowych

**Typy podkładki** są jedną z dwóch technologii używanych przez firmę Microsoft do wyizolowania składników w ramach testu ze środowiska. Podkładki przewołują wywołania do określonych metod w kodzie, który piszesz jako część testu. Wiele metod zwraca różne wyniki zależne od warunków zewnętrznych, ale podkładka jest pod kontrolą testu i może zwracać spójne wyniki przy każdym wywołaniu. Ułatwia to zapisanie testów.

Użyj *podkładek* , aby odizolować swój kod od zestawów, które nie są częścią rozwiązania. Aby izolować składniki rozwiązania od siebie, użyj *wycinków*.

Aby zapoznać się z omówieniem i "Szybki Start", zobacz [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md)elementów sztucznych firmy Microsoft.

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework
::: moniker range=">=vs-2019"
- Obsługa projektu .NET Core, .NET 5,0 i zestawu SDK w wersji zapoznawczej w programie Visual Studio 2019 Update 6 i jest włączona domyślnie w wersji Update 8. Aby uzyskać więcej informacji, zobacz artykuły [firmy Microsoft dla projektów .NET Core i SDK](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

## <a name="example-the-y2k-bug"></a>Przykład: Usterka Y2K

Rozważmy metodę, która zgłasza wyjątek 1 stycznia 2000:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Testowanie tej metody jest przyczyną problemów, ponieważ program zależy od `DateTime.Now` metody, która zależy od zegara komputera, metody niedeterministycznej zależnej od środowiska. Ponadto `DateTime.Now` jest właściwością statyczną, więc nie można użyć w tym miejscu typu zastępczego. Ten problem jest objawem problemu z izolacją w testach jednostkowych: programy, które bezpośrednio odwołują się do interfejsów API bazy danych, komunikują się z usługami sieci Web itd., są trudne do testów jednostkowych, ponieważ ich logika zależy od środowiska.

Jest to miejsce, w którym powinny być używane typy podkładek. Typy podkładki zapewniają mechanizm do rozdzielania dowolnej metody .NET z delegatem zdefiniowanym przez użytkownika. Typy podkładek to kod generowany przez generator sztuczny i używają delegatów, które nazywają typy podkładki, aby określić nowe implementacje metod.

Poniższy test pokazuje, jak używać typu podkładki, `ShimDateTime` , aby zapewnić niestandardową implementację daty/godziny. teraz:

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

## <a name="how-to-use-shims"></a>Jak używać podkładki

Najpierw Dodaj zestaw elementów sztucznych:

1. W **Eksplorator rozwiązań**, 
    - W przypadku starszego projektu .NET Framework (styl inny niż zestaw SDK) rozwiń węzeł **odwołania** projektu testów jednostkowych.
    ::: moniker range=">=vs-2019"
    - W przypadku projektu w stylu zestawu SDK .NET Framework, .NET Core lub .NET 5,0 rozwiń węzeł **zależności** , aby znaleźć zestaw, który ma zostać sfałszowany w ramach **zestawów**, **projektów** lub **pakietów**.
    ::: moniker-end
    - Jeśli pracujesz w Visual Basic, wybierz pozycję **Pokaż wszystkie pliki** na **Eksplorator rozwiązań** pasku narzędzi, aby wyświetlić węzeł **odwołania** .

2. Wybierz zestaw, który zawiera definicje klas, dla których chcesz utworzyć podkładki. Na przykład, jeśli chcesz określić **datę i godzinę** dla podkładki, wybierz pozycję **System.dll**.

3. W menu skrótów wybierz polecenie **Dodaj** elementy sztuczne.

### <a name="use-shimscontext"></a>Użyj ShimsContext

W przypadku korzystania z typów podkładek w środowisku testów jednostkowych należy otoczyć kod testu w `ShimsContext` celu kontrolowania okresu istnienia podkładki. W przeciwnym razie podkładki będą ostatnio do momentu wyłączenia elementu AppDomain. Najprostszym sposobem tworzenia `ShimsContext` jest użycie metody statycznej `Create()` , jak pokazano w poniższym kodzie:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Należy prawidłowo usunąć każdy kontekst podkładek. Jako zasada elementu kciuka Wywołaj `ShimsContext.Create` wewnątrz `using` instrukcji, aby upewnić się, że prawidłowe czyszczenie zarejestrowanych podkładek. Na przykład można zarejestrować podkładkę dla metody testowej, która zastępuje `DateTime.Now` metodę delegatem, który zawsze zwraca pierwszy z stycznia 2000. Jeśli zapomnisz wyczyścić zarejestrowaną podkładkę w metodzie testowej, pozostała część przebiegu testu zawsze zwróci pierwszy styczeń 2000 jako `DateTime.Now` wartość. Może to być zaskakujące i mylące.

### <a name="write-a-test-with-shims"></a>Napisz test z podkładkami

W kodzie testowym Wstaw *deprezentację* dla metody, która ma zostać sfałszowana. Na przykład:

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

Nazwy klas podkładków składają się z prefiksu `Fakes.Shim` do oryginalnej nazwy typu.

Podkładki działają *przez wstawianie* postanowień do kodu testowanej aplikacji. Wszędzie tam, gdzie występuje wywołanie oryginalnej metody, system sztuczni wykonuje deprezentację, więc zamiast wywoływania rzeczywistej metody, kod podkładki jest wywoływany.

Zauważ, że dewycieczki są tworzone i usuwane w czasie wykonywania. Należy zawsze utworzyć deprezentację w całym okresie istnienia `ShimsContext` . Po jego usunięciu wszystkie utworzone podkładki są usuwane. Najlepszym sposobem wykonania tej czynności jest wewnątrz `using` instrukcji.

Może zostać wyświetlony błąd kompilacji informujący o tym, że przestrzeń nazw elementów sztucznych nie istnieje. Ten błąd jest czasami wyświetlany, gdy występują inne błędy kompilacji. Popraw inne błędy i zostanie ono wyznikane.

## <a name="shims-for-different-kinds-of-methods"></a>Podkładki dla różnych rodzajów metod

Typy podkładki umożliwiają zamianę dowolnej metody .NET, w tym metod statycznych lub metod niewirtualnych, z własnymi delegatami.

### <a name="static-methods"></a>Metody statyczne

Właściwości służące do dołączania podkładek do metod statycznych są umieszczane w typie podkładki. Każda właściwość ma tylko metodę ustawiającą, której można użyć do dołączenia delegata do metody docelowej. Na przykład, dana Klasa `MyClass` z metodą statyczną `MyMethod` :

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Możemy dołączyć podkładkę do `MyMethod` zawsze zwraca 5:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Metody wystąpień (dla wszystkich wystąpień)

Podobnie jak w przypadku metod statycznych, metody wystąpień mogą być zastąpionym podkładką dla wszystkich wystąpień. Właściwości służące do dołączania tych podkładek są umieszczane w typie zagnieżdżonym o nazwie AllInstances, aby uniknąć pomyłek. Na przykład, dana Klasa `MyClass` z metodą wystąpienia `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Możesz dołączyć podkładkę do `MyMethod` zawsze zwracającą 5, niezależnie od wystąpienia:

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

Zwróć uwagę, że elementy sztuczne przekazują wystąpienie środowiska uruchomieniowego jako pierwszy argument delegata w tym przypadku.

### <a name="instance-methods-for-one-runtime-instance"></a>Metody wystąpień (dla jednego wystąpienia czasu wykonywania)

Metody wystąpień mogą być również zastąpionym podkładką przez różnych delegatów na podstawie odbiorcy wywołania. Dzięki temu ta sama metoda wystąpienia ma różne zachowania dla każdego wystąpienia typu. Właściwości do konfigurowania tych podkładek są metodami wystąpień samego typu podkładki. Każdy typ niejawnej podkładki jest również skojarzony z nieprzetworzonym wystąpieniem typu zastąpionym podkładką.

Na przykład, dana Klasa `MyClass` z metodą wystąpienia `MyMethod` :

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Możemy skonfigurować dwa typy podkładek metod, takie jak pierwszy zwraca wartość 5, a drugi zawsze zwraca wartość 10:

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

Do rzeczywistego wystąpienia typu zastąpionym podkładką można uzyskać dostęp za pomocą właściwości wystąpienia:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Typ podkładki ma również niejawną konwersję na typ zastąpionym podkładką, więc zazwyczaj można użyć typu podkładki jako:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Konstruktory

Konstruktory mogą być także zastąpionym podkładką w celu dołączania typów podkładki do przyszłych obiektów. Każdy Konstruktor jest narażony jako Konstruktor metody statycznej w typie podkładki. Na przykład, biorąc pod uwagę Klasa `MyClass` z konstruktorem pobierającym liczbę całkowitą:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Konfigurowanie typu podkładki dla konstruktora, tak aby każde następne wystąpienie zwracało wartość-5 podczas wywoływania metody pobierającej, niezależnie od wartości w konstruktorze:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Każdy typ podkładki uwidacznia dwa konstruktory. Domyślny konstruktor powinien być używany, gdy jest zbędne nowe wystąpienie, podczas gdy konstruktor przyjmujący wystąpienie zastąpionym podkładką jako argument powinien być używany tylko w podkładkach z konstruktorem:

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

### <a name="base-members"></a>Podstawowe elementy członkowskie

Do właściwości podkładkowych członków podstawowych można uzyskać dostęp przez utworzenie podkładki dla typu podstawowego i przekazanie wystąpienia podrzędnego jako parametru do konstruktora podstawowej klasy podkładek.

Na przykład, dana Klasa `MyBase` z metodą wystąpienia `MyMethod` i podtyp `MyChild` :

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Można skonfigurować podkładkę dla programu `MyBase` , tworząc nową `ShimMyBase` podkładkę:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Należy zauważyć, że podrzędny Typ podkładki jest niejawnie konwertowany do wystąpienia podrzędnego, gdy jest przenoszona jako parametr do podstawowego konstruktora podkładki.

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

Typy podkładki ujawniają statyczną metodę `StaticConstructor` do podkładek konstruktora statycznego typu. Ponieważ konstruktory statyczne są wykonywane tylko raz, należy upewnić się, że podkładka jest skonfigurowana przed uzyskaniem dostępu do dowolnego elementu członkowskiego typu.

### <a name="finalizers"></a>Finalizatory

Finalizatory nie są obsługiwane w przypadku elementów sztucznych.

### <a name="private-methods"></a>Metody prywatne

Generator kodu sztucznego tworzy właściwości podkładek dla metod prywatnych, które mają tylko widoczne typy w podpisie, to oznacza, że typy parametrów i typ zwracany są widoczne.

### <a name="binding-interfaces"></a>Interfejsy powiązań

Gdy typ zastąpionym podkładką implementuje interfejs, generator kodu emituje metodę, która pozwala na powiązanie wszystkich elementów członkowskich z tego interfejsu jednocześnie.

Na przykład, dana Klasa `MyClass` implementująca `IEnumerable<int>` :

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

W celu utworzenia podkładki implementacji `IEnumerable<int>` w systemie MyClass można wywołać metodę bind:

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

## <a name="change-the-default-behavior"></a>Zmień zachowanie domyślne

Każdy wygenerowany Typ podkładki przechowuje wystąpienie `IShimBehavior` interfejsu za pomocą `ShimBase<T>.InstanceBehavior` właściwości. Zachowanie jest używane za każdym razem, gdy klient wywołuje element członkowski wystąpienia, który nie został jawnie zastąpionym podkładką.

Jeśli zachowanie nie zostało jawnie ustawione, używa wystąpienia zwróconego przez właściwość statyczną `ShimsBehaviors.Current` . Domyślnie ta właściwość zwraca zachowanie, które zgłasza `NotImplementedException` wyjątek.

Takie zachowanie można zmienić w dowolnym momencie, ustawiając `InstanceBehavior` Właściwość w dowolnym wystąpieniu podkładki. Na przykład poniższy fragment kodu zmienia podkładkę na zachowanie, które nic nie robi ani nie zwraca wartości domyślnej typu zwracanego — to znaczy `default(T)` :

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Zachowanie można także zmienić globalnie dla wszystkich wystąpień zastąpionym podkładką, dla których `InstanceBehavior` Właściwość nie została jawnie ustawiona przez ustawienie właściwości statycznej `ShimsBehaviors.Current` :

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Wykrywanie dostępu do środowiska

Istnieje możliwość dołączenia zachowania do wszystkich elementów członkowskich, w tym metod statycznych, o określonym typie przez przypisanie `ShimsBehaviors.NotImplemented` zachowania do właściwości statycznej `Behavior` odpowiadającego typu podkładki:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Współbieżność

Typy podkładki mają zastosowanie do wszystkich wątków w domenie aplikacji i nie mają koligacji wątku. Jest to ważny fakt, jeśli planujesz użyć modułu uruchamiającego testy, który obsługuje współbieżność. Testy obejmujące typy podkładek nie mogą być uruchamiane współbieżnie. Ta właściwość nie jest wymuszana przez środowisko uruchomieniowe elementów sztucznych.

## <a name="call-the-original-method-from-the-shim-method"></a>Wywołaj oryginalną metodę z metody podkładki

Załóżmy, że chcesz napisać tekst do systemu plików po walidacji nazwy pliku przekazaną do metody. W takim przypadku należy wywołać metodę początkową w środku metody podkładek.

Pierwszym podejściem do rozwiązania tego problemu jest zawinięcie wywołania do oryginalnej metody przy użyciu delegata i `ShimsContext.ExecuteWithoutShims()` , jak w poniższym kodzie:

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

Innym podejściem jest ustawienie podkładki na wartość null, wywołanie metody oryginalnej i przywrócenie podkładki.

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

## <a name="systemenvironment"></a>System. Environment

W przypadku podkładki <xref:System.Environment?displayProperty=fullName> Dodaj następującą zawartość do pliku mscorlib. sztuczne po elemencie **Assembly** :

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Po skompilowaniu rozwiązania metody i właściwości w <xref:System.Environment?displayProperty=fullName> klasie są dostępne do zastąpionym podkładką, na przykład:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Ograniczenia

Podkładki nie mogą być używane dla wszystkich typów z biblioteki klas bazowych .NET **mscorlib** i **system** w .NET Framework, a w programie **System. Runtime** w programie .NET Core lub .NET 5,0.

## <a name="see-also"></a>Zobacz też

- [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Blog Peterowi Provost: podkładki dla programu Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Wideo (1h16): testowanie kodu nietestowanego za pomocą elementów sztucznych w programie Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
