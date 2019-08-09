---
title: Uruchamianie testów jednostkowych na rozszerzeniach UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5aeeb8bf9ec70a7288316c8b4c6baa337c232621
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871722"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Uruchamianie testów jednostek dla rozszerzeń UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zapewnić stabilny kod przy użyciu kolejnych zmian, zalecamy napisać testy jednostkowe i wykonać je w ramach regularnego procesu kompilacji. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md). Aby skonfigurować testy dla rozszerzeń modelowania programu Visual Studio, potrzebne są pewne informacje. Podsumowanie:

- [Konfigurowanie testu jednostkowego dla rozszerzeń VSIX](#Host)

   Uruchom testy za pomocą karty hosta VS IDE. Opatrz każdą metodę `[HostType("VS IDE")]`testową prefiksem. Ta karta hosta jest [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamiana, gdy testy są uruchamiane.

- [Uzyskiwanie dostępu do DTE i magazynie modeli.](#DTE)

   Zwykle trzeba będzie otworzyć model i jego diagramy oraz uzyskać dostęp `IModelStore` do programu w ramach inicjalizacji testu.

- [Otwieranie diagramu modelu](#Opening)

   Można rzutować `EnvDTE.ProjectItem` do i z `IDiagramContext`.

- [Wykonywanie zmian w wątku interfejsu użytkownika](#UiThread)

   Testy, które wprowadzają zmiany do magazynu modeli, muszą być wykonywane w wątku interfejsu użytkownika. Można tego użyć `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` .

- [Polecenia testowania, gesty i inne składniki MEF](#MEF)

   Aby przetestować składniki MEF, należy jawnie połączyć ich zaimportowane właściwości z wartościami.

  Te punkty są rozbudowane w poniższych sekcjach.

  Przykład przetestowanego przez jednostkę rozszerzenia UML można znaleźć w galerii przykładów kodu na [UML — szybkie wprowadzanie przy użyciu tekstu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="Host"></a>Konfigurowanie testu jednostkowego dla rozszerzeń VSIX
 Metody w rozszerzeniach modelowania zwykle działają z diagramem, który jest już otwarty. Metody używają MEF Importy, takich jak **IDiagramContext** i **ILinkedUndoContext**. Środowisko testowe musi skonfigurować ten kontekst przed uruchomieniem testów.

#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Aby skonfigurować test jednostkowy wykonywany w programie[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Utwórz projekt rozszerzenia UML i projekt testu jednostkowego.

    1. **Projekt rozszerzenia UML.** Zwykle jest to tworzone przy użyciu poleceń, gestów lub szablonów projektu walidacji. Na przykład zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Projekt testu jednostkowego.** Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).

2. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Utwórz rozwiązanie, które zawiera projekt modelowania UML. To rozwiązanie będzie używane jako początkowy stan testów. Powinna być oddzielona od rozwiązania, w którym piszesz rozszerzenie UML i jego testy jednostkowe. Aby uzyskać więcej informacji, zobacz [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **W projekcie rozszerzenia UML**Edytuj plik. csproj jako tekst i upewnij się, że są wyświetlane `true`następujące wiersze:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     Aby edytować plik. csproj jako tekst, wybierz pozycję **Zwolnij projekt** w menu skrótów projektu w Eksplorator rozwiązań. Następnie wybierz pozycję **Edytuj.... csproj**. Po edytowaniu tekstu wybierz pozycję Załaduj **ponownie projekt**.

4. W projekcie rozszerzenia UML Dodaj następujący wiersz do **Properties\AssemblyInfo.cs**. Dzięki temu testy jednostkowe uzyskują dostęp do metod, które mają zostać przetestowane:

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **W projekcie testów jednostkowych**Dodaj następujące odwołania do zestawu:

    - *Projekt rozszerzenia UML*

    - **EnvDTE.dll**

    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**

    - **Microsoft.VisualStudio.Uml.Interfaces.dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. Oznacz atrybut `[HostType("VS IDE")]` prefiksem każdej metody testowej, w tym metody inicjacji.

     Zapewni to, że test zostanie uruchomiony w eksperymentalnym wystąpieniu programu Visual Studio.

## <a name="DTE"></a>Uzyskiwanie dostępu do DTE i magazynie modeli.
 Napisz metodę, aby otworzyć projekt modelowania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Zazwyczaj chcesz otworzyć rozwiązanie tylko raz w każdym przebiegu testu. Aby uruchomić metodę tylko raz, należy poprzedzić metodę `[AssemblyInitialize]` atrybutem. Nie zapomnij, że dla każdej metody testowej jest również wymagany atrybut [HostType ("VS IDE")].  Na przykład:

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 Jeśli wystąpienie <xref:EnvDTE.Project?displayProperty=fullName> reprezentuje projekt modelowania, można je rzutować do i z [IModelingProject](/previous-versions/ee789474(v=vs.140)).

## <a name="Opening"></a>Otwieranie diagramu modelu
 Dla każdego testu lub klasy testów zwykle chcesz korzystać z otwartego diagramu. Poniższy przykład używa `[ClassInitialize]` atrybutu, który wykonuje tę metodę przed innymi metodami w tej klasie testowej. Ponownie nie zapomnij, że dla każdej metody testowej jest wymagany również atrybut [HostType ("VS IDE")]:

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="UiThread"></a>Wykonywanie zmian modelu w wątku interfejsu użytkownika
 Jeśli testy lub testowane metody są wprowadzane do magazynu modeli, należy wykonać je w wątku interfejsu użytkownika. Jeśli tego nie zrobisz, może zostać wyświetlony komunikat `AccessViolationException`. Ujmij kod metody testowej w wywołaniu wywołania:

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="MEF"></a>Testowanie polecenia, gestu i innych składników MEF
 Składniki MEF używają deklaracji właściwości, które mają `[Import]` atrybut i których wartości są ustawiane przez ich hosty. Zazwyczaj takie właściwości to IDiagramContext, SVsServiceProvider i ILinkedUndoContext. Podczas testowania metody, która używa dowolnej z tych właściwości, przed wykonaniem testowanej metody należy ustawić ich wartości. Na przykład jeśli zapisano rozszerzenie polecenia podobne do tego kodu:

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 Następnie można ustawić zaimportowane właściwości w następujący sposób:

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 Jeśli chcesz przetestować metodę, która przyjmuje zaimportowaną właściwość jako parametr, można zaimportować właściwość do klasy testowej i zastosować `SatisfyImportsOnce` do wystąpienia testowego. Na przykład:

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 W tym przykładzie dwa atrybuty każdej metody testowej są łączone dla wygody w jednym wierszu.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Dostęp z testów do metod prywatnych i zmiennych
 Czasami chcesz przetestować metodę, która jest prywatna, lub sprawdzić stan pola, które jest prywatne, przed i po wykonaniu testowanej metody. Stanowi to problem, ponieważ testy znajdują się w osobnym zestawie do testowanej klasy. Istnieje kilka taktykę, które można wziąć pod uwagę, w tym następujące:

 Test tylko za pomocą elementów publicznych i wewnętrznych Napisz testy tak, aby korzystały tylko z publicznych (lub wewnętrznych) klas i członków. Jest to najlepsze rozwiązanie. Testy będą nadal działały nawet wtedy, gdy Refaktoryzacja wewnętrznej implementacji zestawu podlega testowi. Stosując te same testy przed i po zmianach, można się upewnić, że zmiany nie zmieniły zachowania zestawu.

 Aby to umożliwić, może być konieczne przeprowadzenie restrukturyzacji kodu. Na przykład może być konieczne oddzielenie niektórych metod do innej klasy.

 Dzięki poważnej rozważenia tego podejścia często będziesz wiedzieć, że kod jest łatwiejszy do odczytania i zmiany, i mniej podatny na błędy, gdy zmiany są konieczne.

 Można zezwolić zestawowi testowemu na dostęp do wewnętrznych elementów przez dodanie atrybutu w **Properties\AssemblyInfo.cs** w projekcie, który ma być testowany:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Zdefiniuj interfejs testowy Zdefiniuj interfejs, który obejmuje zarówno publiczne elementy członkowskie klasy do przetestowania, jak i dodatkowe właściwości i metody dla prywatnych elementów członkowskich, które mają być w stanie korzystać z testów. Dodaj ten interfejs do projektu, który ma zostać przetestowany. Na przykład:

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Dodaj metody do testowanej klasy, aby jawnie zaimplementować metody dostępu. Należy zachować te dodatkowe metody niezależnie od klasy głównej, pisząc je w definicji klasy częściowej w osobnym pliku. Na przykład:

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Zezwól zestawowi testowemu na używanie interfejsów testowych przez dodanie tego atrybutu do testowanego zestawu:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 W metodach testów jednostkowych Użyj interfejsu testowego. Na przykład:

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Definiowanie metod dostępu przy użyciu odbicia jest tak, jak zalecamy. Starsze wersje programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewniały narzędzia, które automatycznie utworzyły metodę dostępu dla każdej metody prywatnej. Chociaż jest to wygodne, nasze środowisko zasugeruje, że w efekcie testy jednostkowe są bardzo silnie powiązane ze strukturą wewnętrzną testowanej aplikacji. Powoduje to dodatkową pracę w przypadku zmiany wymagań lub architektury, ponieważ testy należy zmienić wraz z implementacją. Ponadto wszelkie błędne założenia w projekcie implementacji są również wbudowane w testy, aby testy nie znalazły błędów.

## <a name="see-also"></a>Zobacz też
 [Anatomia testu jednostkowego](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [UML — szybkie wprowadzanie przy użyciu tekstu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)
