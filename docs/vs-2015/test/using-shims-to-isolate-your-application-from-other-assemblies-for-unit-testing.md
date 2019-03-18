---
title: Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 14
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2ab2925024fdf9e4f0b4e93db34b375b89933a48
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155946"
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typy podkładek ** są jedną z dwóch technologii używanych struktura sztucznych elementów testowych Microsoft pozwala łatwo wyodrębniać składniki w ramach testu w środowisku. Podkładki kierowanie wywołań do określonych metod do kodu napisanego w ramach testu. Wiele metod zwracać różne wyniki zależne od warunków zewnętrznych, ale podkładka jest pod kontrolą testów i może zwrócić spójne wyniki w każdym wywołaniu. To sprawia, że testy znacznie łatwiejsze do zapisu.  
  
 Stosowanie podkładek do izolowania kodu z zestawów, które nie są częścią rozwiązania. Aby wyizolować składników rozwiązania od siebie nawzajem, firma Microsoft zaleca, aby użyć wycinków.  
  
 Aby uzyskać omówienie i szybki start wskazówki, zobacz [izolując kod w ramach testu, with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
  Zobacz [wideo (1 godz. 16): Testowanie kodu bez sprawdzalnego działa zgodnie z substytutami w programie Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Przykład: Błąd Y2K  
 Rozważmy metodę, która zgłosiła wyjątek na 1 stycznia 2000:  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }
}  
  
```  
  
 Testowanie tej metody jest szczególnie problematyczny, ponieważ program jest zależny od `DateTime.Now`, metody, która zależy od komputera użytkownika zegara, środowisko zależne, metoda deterministyczna. Ponadto `DateTime.Now` jest właściwość statyczna, więc nie można tutaj użyć typu klasy zastępczej. Ten problem dotyczy objawem problem izolacji testów jednostkowych: programów bezpośrednio wywoływać interfejsy API bazy danych, komunikacja z usługami sieci web i tak dalej, które są trudne do testu jednostkowego, ponieważ logikę zależy od środowiska.  
  
 Jest to, gdzie typy podkładek należy używać. Typy podkładek udostępniają mechanizm można przekierować dowolnej metody .NET do delegata zdefiniowane przez użytkownika. Typy podkładek są kod wygenerowany przez generator substytutów i używają delegatów, które nazywamy typy podkładek, aby określić nowych implementacji metody.  
  
 Następującego testu pokazuje, jak używać typu shim `ShimDateTime`, aby zapewnić niestandardową implementację DateTime.Now:  
  
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
  
##  <a name="BKMK_Fakes_requirements"></a> Jak używać podkładek  
  
###  <a name="AddFakes"></a> Dodaj zestawy elementów sztucznych  
  
1.  W Eksploratorze rozwiązań rozwiń projekt testów jednostkowych **odwołania**.  
  
    -   Jeśli pracujesz w języku Visual Basic, musisz wybrać **Pokaż wszystkie pliki** na pasku narzędzi Eksploratora rozwiązań, aby zobaczyć listę odwołań.  
  
2.  Wybierz zestaw zawierający definicje klas, dla których chcesz utworzyć podkładki. Na przykład jeśli chcesz chciał podłożyć daty/godziny, wybierz opcję System.dll  
  
3.  W menu skrótów wybierz **Dodaj zestawy Substytuowane**.  
  
###  <a name="ShimsContext"></a> Użyj ShimsContext  
 Używając typy podkładek w środowiska testów jednostkowych, należy wpisać kod testowy w `ShimsContext` kontrolować okres istnienia usługi podkładki. Jeśli firma Microsoft nie wymaga to, Twoje podkładki będzie wystarczą do momentu zamknięcia elementu AppDomain. Najprostszym sposobem utworzenia `ShimsContext` przy użyciu statycznych `Create()` metody, jak pokazano w poniższym kodzie:  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Koniecznie prawidłowo dispose w każdym kontekście podkładki. Jako ogólną regułę można przyjąć, zawsze wywołuj `ShimsContext.Create` wewnątrz `using` instrukcję, aby zapewnić właściwe rozliczanie zarejestrowanych podkładki. Na przykład, możesz zarejestrować podkładki dla metody testowej, która zastępuje `DateTime.Now` metody delegata, która zawsze zwraca pierwszy stycznia 2000. Jeśli zapomnisz wyczyść zarejestrowanych podkładki w metodzie testowej, pozostała część przebiegu testu zawsze zwróci wartość pierwszego 2000 stycznia jako DateTime.Now. Może to być suprising i kłopotliwe.  
  
###  <a name="WriteShims"></a> Napisać test podkładek  
 W kodzie testowym Wstaw *przekierowania* dla metody, którą chcesz substytuować. Na przykład:  
  
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
  
 Nazwy klasy shim są tworzone przez dodanie przedrostka `Fakes.Shim` do oryginalnej nazwy typu.  
  
 Podkładek pracy przez wstawienie *przekierowania* w kodzie testowanej aplikacji. Wszędzie tam, gdzie wywołania do oryginalnej metody system elementów sztucznych wykonuje przekierowania, tak, aby zamiast wywołania metody rzeczywistych, nosi nazwę kod podkładki.  
  
 Należy zauważyć, że przekierowania są tworzone i usuwane w czasie wykonywania. Musisz utworzyć zawsze przekierowania w ramach cyklu życia `ShimsContext`. Po jego usunięciu wszelkich podkładki utworzonej podczas aktywnego są usuwane. Najlepszym sposobem, w tym celu znajduje się wewnątrz `using` instrukcji.  
  
 Możesz zobaczyć kompilacji o błędzie informującym, przestrzeń nazw elementów sztucznych nie istnieje. Ten błąd pojawia się czasami, gdy istnieją inne błędy kompilacji. Usuń inne błędy, a jego będą dopasowywane.  
  
##  <a name="BKMK_Shim_basics"></a> Podkładki dla różnych rodzajów metod  
 Typy podkładek umożliwiają Zastąp dowolnej metody .NET, w tym metod statycznych i metod niewirtualnych, za pomocą własnych obiektów delegowanych.  
  
###  <a name="BKMK_Static_methods"></a> Metody statyczne  
 Właściwości, aby dołączyć podkładek do metody statyczne są umieszczane w typu shim. Każda właściwość ma setter, który może służyć do dołączania obiekt delegowany do metody docelowej. Na przykład, biorąc klasy `MyClass` przy użyciu statycznej metody `MyMethod`:  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Dołączamy podkładek do `MyMethod` która zawsze zwraca 5:  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Metody wystąpienia (dla wszystkich wystąpień)  
 Podobnie do metody statyczne metody wystąpienia można można użyć podkładki dla wszystkich wystąpień. Właściwości, które można dołączyć te podkładek są umieszczane w zagnieżdżony typ o nazwie wszystkich wystąpień, aby uniknąć mylenia go. Na przykład, biorąc klasy `MyClass` z metodą wystąpienia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Możesz dołączyć podkładek do `MyMethod` która zawsze zwraca 5, niezależnie od tego, wystąpienie:  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 Struktura wygenerowany typ ShimMyClass wygląda podobnie do poniższego kodu:  
  
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
  
 Należy zauważyć, że elementów sztucznych przekazuje wystąpienie środowiska IR w tym przypadku jako pierwszy argument delegata.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Wystąpienie metody (jedno wystąpienie środowiska wykonawczego)  
 Metody wystąpienia można również można użyć podkładki dla przez różne delegatów, oparte na odbiorcy wywołania. Dzięki temu tej samej metody wystąpienia, można mieć różne ustawienia dla każdego wystąpienia tego typu. Właściwości, aby skonfigurować te ustawienia są metody wystąpienia samego typu shim. Każdy typ podkładki wystąpień jest również skojarzony z wystąpieniem pierwotnych z typem zastąpionym podkładką.  
  
 Na przykład, biorąc klasy `MyClass` z metodą wystąpienia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Firma Microsoft można skonfigurować dwa typy podkładek MyMethod taki sposób, że pierwszy z nich zawsze zwraca 5, a drugi zawsze zwraca 10:  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 Struktura wygenerowany typ ShimMyClass wygląda podobnie do poniższego kodu:  
  
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
  
 Za pomocą właściwości wystąpienia można uzyskać dostępu do wystąpienia rzeczywiste typem zastąpionym podkładką:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Typ ma również niejawna konwersja z typem zastąpionym podkładką, aby można było używać typu podkładki, ponieważ jest zwykle wystarczy:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Konstruktory  
 Konstruktory mogą również można użyć podkładki dla Aby dołączyć typy podkładek do obiektów w przyszłości. Każdy Konstruktor jest ujawniona jako statycznej metody konstruktora do typu shim. Na przykład, biorąc klasy `MyClass` przy użyciu konstruktora, biorąc liczbą całkowitą:  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Skonfigurujemy typ konstruktora, aby każde wystąpienie przyszłych zwraca -5, gdy zostanie wywołana metoda pobierająca wartość, niezależnie od wartości w Konstruktorze:  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Należy pamiętać, że każdy typ podkładki udostępnia dwa konstruktory. Domyślny konstruktor powinny być używane, gdy wymagane jest nowym wystąpieniu podczas konstruktora, biorąc typu shim wystąpienie jako argument powinien być używany w tylko wtedy podkładek Konstruktor:  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 Struktura wygenerowany typ ShimMyClass podobny kod followoing:  
  
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
  
###  <a name="BKMK_Base_members"></a> Składowe bazowe  
 Tworząc podkładki dla typu podstawowego, a następnie przekazując wystąpienia podrzędne jako parametr do konstruktora klasy bazowej podkładki można uzyskać dostępu do właściwości podkładki elementów podstawowych.  
  
 Na przykład, biorąc klasy `MyBase` z metodą wystąpienia `MyMethod` i podtypem `MyChild`:  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Możemy skonfigurować podkładka dla `MyBase` przez utworzenie nowego `ShimMyBase` podkładek:  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Należy pamiętać, że typ podrzędny jest niejawnie konwertowany na wystąpienie podrzędnych, gdy przekazany jako parametr do konstruktora podstawowego podkładki.  
  
 Wygenerowany typ struktury ShimMyChild i ShimMyBase przypomina następujący kod:  
  
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
  
###  <a name="BKMK_Static_constructors"></a> Konstruktory statyczne  
 Typy podkładek ujawnia metody statyczne `StaticConstructor` chciał podłożyć statyczne konstruktora typu. Ponieważ konstruktory statyczne są wykonywane, gdy tylko, musisz upewnić się, że podkładka jest skonfigurowana, przed uzyskaniem dostępu do dowolnego członka typu.  
  
###  <a name="BKMK_Finalizers"></a> Finalizatory  
 Finalizatory nie są obsługiwane w Fakes.  
  
###  <a name="BKMK_Private_methods"></a> Metody prywatne  
 Generator kodu pozornego spowoduje to utworzenie właściwości podkładki dla metody prywatne, którzy mają tylko typy widoczne dla podpisu, czyli typy parametrów i zwracany typ jest widoczny.  
  
###  <a name="BKMK_Binding_interfaces"></a> Interfejsy powiązania  
 Gdy typem zastąpionym podkładką implementuje interfejs, generator kodu emituje metodę, która umożliwi jednocześnie powiązać wszystkie elementy członkowskie z tego interfejsu.  
  
 Na przykład, biorąc klasy `MyClass` implementującej `IEnumerable<int>`:  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Firma Microsoft może podkładkę implementacje `IEnumerable<int>` w MyClass przez wywołanie metody Bind:  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 Struktura wygenerowany typ ShimMyClass przypomina następujący kod:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Zmiana domyślnego zachowania  
 Każdy typ podkładki wygenerowanego posiada wystąpienie `IShimBehavior` interfejs, za pomocą `ShimBase<T>.InstanceBehavior` właściwości. To zachowanie jest używana zawsze, gdy klient wywołuje element członkowski wystąpienia, który nie został jawnie obsługiwane.  
  
 Jeśli zachowanie nie została jawnie ustawiona, zostanie użyty wystąpienia zwróconą przez statyczną `ShimsBehaviors.Current` właściwości. Domyślnie właściwość ta zwraca zachowanie, które zgłasza `NotImplementedException` wyjątku.  
  
 To zachowanie można zmienić w dowolnym momencie przez ustawienie `InstanceBehavior` właściwość dowolne wystąpienie podkładki. Na przykład poniższy fragment kodu zmienia podkładka do zachowania, które nie działa lub zwraca wartość domyślną typu zwracanego — czyli wartość default(T):  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 To zachowanie można także zmienić globalnie dla wszystkich wystąpień typu shim dla którego `InstanceBehavior` właściwość nie została jawnie ustawiona przez ustawienie statycznego `ShimsBehaviors.Current` właściwości:  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Uzyskuje dostęp do środowiska wykrywanie  
 Istnieje możliwość dołączyć zachowanie dla wszystkich członków, w tym metody statyczne, określonego typu, przypisując `ShimsBehaviors.NotImplemented` zachowanie, aby właściwość statyczna `Behavior` odpowiedniego typu shim:  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Współbieżność  
 Typy podkładek stosowane do wszystkich wątków w domenie aplikacji i braku koligacji wątku. Jest to ważne faktów, jeśli planujesz użyć modułu uruchamiającego testy, która obsługuje współbieżność: testy obejmujące typy podkładek, nie można uruchomić jednocześnie. Ta właściwość nie jest enfored w czasie wykonywania elementów sztucznych.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Wywoływanie oryginalną metodę z metodą podkładki  
 Wyobraź sobie, że Chcieliśmy, aby faktycznie wpisać tekst w systemie plików, po sprawdzania poprawności nazwy pliku przekazywany do metody. W takiej sytuacji firma Microsoft będzie chciała wywołać oryginalnej metody w środku metoda podkładki.  
  
 Pierwszym sposobem, aby rozwiązać ten problem jest powodującą otoczenie wywołania do oryginalnej metody za pomocą delegata i `ShimsContext.ExecuteWithoutShims()` zgodnie z poniższym kodem:  
  
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
  
 Innym rozwiązaniem jest podkładki o wartości null, wywołaj metodę oryginalnego i przywrócić podkładka.  
  
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
  
##  <a name="BKMK_Limitations"></a> Ograniczenia  
 Nie można użyć podkładki dla wszystkich typów z biblioteki klas podstawowych platformy .NET **mscorlib** i **systemu**.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Peter Provost blog: Visual Studio 2012 Shims](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Wideo (1 godz. 16): Testowanie kodu bez sprawdzalnego działa zgodnie z substytutami w programie Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)
