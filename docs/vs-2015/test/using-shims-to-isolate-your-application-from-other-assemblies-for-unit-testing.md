---
title: Używanie podkładki do izolowania aplikacji od innych zestawów do testowania jednostkowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa9db3e67b1f5ba5e183f8df0c7b34372476fb08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851169"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy podkładki * * są jedną z dwóch technologii, które są używane przez środowisko sztuczne firmy Microsoft, aby można było łatwo izolować testowane składniki w środowisku. Podkładki przewołują wywołania do określonych metod w kodzie, który piszesz jako część testu. Wiele metod zwraca różne wyniki zależne od warunków zewnętrznych, ale podkładka jest pod kontrolą testu i może zwracać spójne wyniki przy każdym wywołaniu. Dzięki temu testy są znacznie łatwiejsze.

 Użyj podkładek, aby odizolować swój kod od zestawów, które nie są częścią rozwiązania. Aby izolować składniki rozwiązania od siebie, zalecamy korzystanie z wycinków.

 Aby zapoznać się z omówieniem i przewodnikiem Szybki Start, zobacz [Izolowanie testowanego kodu za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md) elementów sztucznych firmy Microsoft

 **Wymagania**

- Visual Studio Enterprise

  Zobacz [wideo (1h16): testowanie kodu un-weryfikowalne z elementami sztucznymi w programie Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)

## <a name="example-the-y2k-bug"></a><a name="BKMK_Example__The_Y2K_bug"></a> Przykład: Usterka Y2K
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

 Testowanie tej metody jest szczególnie problematyczne, ponieważ program zależy od `DateTime.Now` metody, która zależy od zegara komputera, metody niedeterministycznej zależnej od środowiska. Ponadto `DateTime.Now` jest właściwością statyczną, więc nie można użyć w tym miejscu typu zastępczego. Ten problem jest objawem problemu z izolacją w testach jednostkowych: programy, które bezpośrednio odwołują się do interfejsów API bazy danych, komunikują się z usługami sieci Web i tak dalej, są trudne do testowania jednostkowego, ponieważ ich logika zależy od środowiska.

 Jest to miejsce, w którym powinny być używane typy podkładek. Typy podkładki zapewniają mechanizm do rozdzielania dowolnej metody .NET z delegatem zdefiniowanym przez użytkownika. Typy podkładek to kod generowany przez generator sztuczny i używają delegatów, które nazywają typy podkładki, aby określić nowe implementacje metod.

 Poniższy test pokazuje, jak używać typu podkładki, `ShimDateTime` , aby zapewnić niestandardową implementację daty/godziny. teraz:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}

```

## <a name="how-to-use-shims"></a><a name="BKMK_Fakes_requirements"></a> Jak używać podkładki

### <a name="add-fakes-assemblies"></a><a name="AddFakes"></a> Dodaj zestawy elementów sztucznych

1. W Eksplorator rozwiązań rozwiń **odwołania do**projektu testu jednostkowego.

    - Jeśli pracujesz w Visual Basic, musisz wybrać opcję **Pokaż wszystkie pliki** na pasku narzędzi Eksplorator rozwiązań, aby zobaczyć listę odwołań.

2. Wybierz zestaw, który zawiera definicje klas, dla których chcesz utworzyć podkładki. Na przykład, jeśli chcesz wybrać datę i godzinę dla podkładki, wybierz System.dll

3. W menu skrótów wybierz polecenie **Dodaj**elementy sztuczne.

### <a name="use-shimscontext"></a><a name="ShimsContext"></a> Użyj ShimsContext
 W przypadku korzystania z typów podkładek w środowisku testów jednostkowych należy otoczyć kod testu w ramach, `ShimsContext` Aby kontrolować okres istnienia podkładki. Jeśli nie jest to wymagane, Twoje podkładki byłyby ostatnio używane do momentu wyłączenia elementu AppDomain. Najprostszym sposobem tworzenia `ShimsContext` jest użycie metody statycznej `Create()` , jak pokazano w poniższym kodzie:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}

```

 Poprawne usuwanie kontekstu podkładki ma krytyczne znaczenie. Jako zasada elementu kciuka zawsze Wywołaj `ShimsContext.Create` wewnątrz `using` instrukcji, aby zapewnić prawidłowe wyczyszczenie zarejestrowanych podkładek. Na przykład można zarejestrować podkładkę dla metody testowej, która zastępuje `DateTime.Now` metodę delegatem, który zawsze zwraca pierwszy z stycznia 2000. Jeśli zapomnisz wyczyścić zarejestrowaną podkładkę w metodzie testowej, pozostała część przebiegu testu zawsze zwróci pierwszy styczeń 2000 jako wartość DateTime. Now. Może to być Suprising i mylące.

### <a name="write-a-test-with-shims"></a><a name="WriteShims"></a> Napisz test z podkładkami
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

## <a name="shims-for-different-kinds-of-methods"></a><a name="BKMK_Shim_basics"></a> Podkładki dla różnych rodzajów metod
 Typy podkładki umożliwiają zamianę dowolnej metody .NET, w tym metod statycznych lub metod niewirtualnych, z własnymi delegatami.

### <a name="static-methods"></a><a name="BKMK_Static_methods"></a> Metody statyczne
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
ShimMyClass.MyMethod = () =>5;
```

### <a name="instance-methods-for-all-instances"></a><a name="BKMK_Instance_methods__for_all_instances_"></a> Metody wystąpień (dla wszystkich wystąpień)
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

### <a name="instance-methods-for-one-runtime-instance"></a><a name="BKMK_Instance_methods__for_one_instance_"></a> Metody wystąpień (dla jednego wystąpienia czasu wykonywania)
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
MyClass instance = shim; // implicit cast retrieves the runtime
                         // instance
```

### <a name="constructors"></a><a name="BKMK_Constructors"></a> Konstruktor
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

 Należy pamiętać, że każdy typ podkładki uwidacznia dwa konstruktory. Domyślny konstruktor powinien być używany, gdy jest zbędne nowe wystąpienie, podczas gdy konstruktor przyjmujący wystąpienie zastąpionym podkładką jako argument powinien być używany tylko w podkładkach z konstruktorem:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

 Wygenerowana struktura typu ShimMyClass przypomina kod followoing:

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

### <a name="base-members"></a><a name="BKMK_Base_members"></a> Podstawowe elementy członkowskie
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

### <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> Konstruktory statyczne
 Typy podkładki ujawniają statyczną metodę `StaticConstructor` do podkładek konstruktora statycznego typu. Ponieważ konstruktory statyczne są wykonywane tylko raz, należy upewnić się, że podkładka jest skonfigurowana przed uzyskaniem dostępu do dowolnego elementu członkowskiego typu.

### <a name="finalizers"></a><a name="BKMK_Finalizers"></a> Finalizatory
 Finalizatory nie są obsługiwane w przypadku elementów sztucznych.

### <a name="private-methods"></a><a name="BKMK_Private_methods"></a> Metody prywatne
 Generator kodu sztucznego utworzy właściwości podkładki dla metod prywatnych, które mają tylko widoczne typy w podpisie, tj. typy parametrów i widoczny typ zwracany.

### <a name="binding-interfaces"></a><a name="BKMK_Binding_interfaces"></a> Interfejsy powiązań
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

 Możemy utworzyć podkładkę dla implementacji `IEnumerable<int>` w systemie MyClass, wywołując metodę bind:

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

## <a name="changing-the-default-behavior"></a><a name="BKMK_Changing_the_default_behavior"></a> Zmiana zachowania domyślnego
 Każdy wygenerowany Typ podkładki przechowuje wystąpienie `IShimBehavior` interfejsu za pomocą `ShimBase<T>.InstanceBehavior` właściwości. Zachowanie jest używane za każdym razem, gdy klient wywołuje element członkowski wystąpienia, który nie został jawnie zastąpionym podkładką.

 Jeśli zachowanie nie zostało jawnie ustawione, będzie używać wystąpienia zwróconego przez właściwość statyczną `ShimsBehaviors.Current` . Domyślnie ta właściwość zwraca zachowanie, które zgłasza `NotImplementedException` wyjątek.

 Takie zachowanie można zmienić w dowolnym momencie, ustawiając `InstanceBehavior` Właściwość w dowolnym wystąpieniu podkładki. Na przykład poniższy fragment kodu zmienia podkładkę na zachowanie, które nic nie robi ani nie zwraca wartości domyślnej typu zwracanego — to znaczy, domyślnie (T):

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
ShimsBehaviors.Current =
    ShimsBehaviors.DefaultValue;

```

## <a name="detecting-environment-accesses"></a><a name="BKMK_Detecting_environment_accesses"></a> Wykrywanie dostępu do środowiska
 Istnieje możliwość dołączenia zachowania do wszystkich elementów członkowskich, w tym metod statycznych, o określonym typie przez przypisanie `ShimsBehaviors.NotImplemented` zachowania do właściwości statycznej `Behavior` odpowiadającego typu podkładki:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();

```

## <a name="concurrency"></a><a name="BKMK_Concurrency"></a> Współbieżności
 Typy podkładki mają zastosowanie do wszystkich wątków w domenie aplikacji i nie mają koligacji wątku. Jest to ważny fakt, jeśli planujesz używanie modułu uruchamiającego testy, który obsługuje współbieżność: testy obejmujące typy podkładek nie mogą być uruchamiane współbieżnie. Ta właściwość nie jest enfored przez środowisko uruchomieniowe elementów sztucznych.

## <a name="calling-the-original-method-from-the-shim-method"></a><a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Wywoływanie oryginalnej metody z metody podkładki
 Załóżmy, że chcemy faktycznie napisać tekst do systemu plików po zweryfikowaniu nazwy pliku przekazaną do metody. W takim przypadku chcemy wywołać oryginalną metodę w środku metody podkładek.

 Pierwszym podejściem do rozwiązania tego problemu jest zawinięcie wywołania do oryginalnej metody za pomocą delegata i `ShimsContext.ExecuteWithoutShims()` jak w poniższym kodzie:

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

 Innym rozwiązaniem jest ustawienie podkładki na wartość null, wywołanie oryginalnej metody i przywrócenie podkładki.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter”);
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

## <a name="limitations"></a><a name="BKMK_Limitations"></a> Limity
 Podkładki nie mogą być używane dla wszystkich typów **z biblioteki MFC** i **systemu**klas podstawowych platformy .NET.

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Zobacz też
 [Izolowanie testowanego kodu za pomocą programu Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) reprezentacjis [Peterowi Provost: Visual Studio 2012 podkładks](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2) [wideo (1H16): testowanie kodu un-weryfikowalne z elementami sztucznymi w programie Visual Studio 2012](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
