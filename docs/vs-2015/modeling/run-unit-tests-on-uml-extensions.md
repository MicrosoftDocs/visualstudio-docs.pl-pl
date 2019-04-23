---
title: Uruchamianie testów jednostkowych na rozszerzeniach UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e37f6d7891e561beecdf0f9146d647822940571b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079853"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Uruchamianie testów jednostek dla rozszerzeń UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zapewnić stabilne, wykonując kolejne zmiany kodu, firma Microsoft zaleca pisanie testów jednostkowych, a następnie wykonać je jako część procesu kompilacji regularne. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md). Aby skonfigurować testy dla rozszerzenia modelowania programu Visual Studio, potrzebujesz niektórych kluczowych informacji. Podsumowanie:  
  
- [Konfigurowanie testów jednostkowych dla rozszerzenia VSIX](#Host)  
  
   Uruchom testy z karty hosta środowiska IDE programu VS. Prefiks każdej metody testowej z `[HostType("VS IDE")]`. Ten adapter hosta uruchamia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamiania testów.  
  
- [Uzyskiwanie dostępu do obiektu DTE i ModelStore](#DTE)  
  
   Zazwyczaj trzeba będzie otworzyć modelu i jego diagramy i dostęp `IModelStore` podczas inicjowania testu.  
  
- [Otwieranie diagramu modelu](#Opening)  
  
   Można rzutować `EnvDTE.ProjectItem` do i z `IDiagramContext`.  
  
- [Wykonywanie niezależnych od zmian w wątku interfejsu użytkownika](#UiThread)  
  
   Testy, wprowadzić zmiany w magazynie modeli, które muszą być wykonywane w wątku interfejsu użytkownika. Możesz użyć `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` tego.  
  
- [Testowanie poleceń i gestów i inne składniki MEF](#MEF)  
  
   Aby przetestować składniki MEF, należy jawnie nawiązać ich importowane właściwości wartości.  
  
  Te punkty są opracowane w poniższych sekcjach.  
  
  Przykładem rozszerzenia UML jednostki przetestowane można znaleźć w galerii przykładów kodu w [UML — szybka wejścia przy użyciu tekstu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="Host"></a> Konfigurowanie testów jednostkowych dla rozszerzenia VSIX  
 Metody w swoich rozszerzeniach modelowania zwykle współpracować z diagramu, który jest już otwarty. Metody takie jak używać importów MEF **IDiagramContext** i **ILinkedUndoContext**. Przed uruchomieniem testów środowisku testowym, należy skonfigurować ten kontekst.  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Aby skonfigurować test jednostkowy, który jest wykonywany w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1. Utwórz projekt rozszerzenia UML i projekt testów jednostkowych.  
  
    1. **Projekt rozszerzenia UML.** Zazwyczaj należy utworzyć przy użyciu polecenia, gestu lub szablonów projektu sprawdzania poprawności. Na przykład zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
    2. **Projekt testów jednostkowych.** Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).  
  
2. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania zawierającego projekt modelowania UML. To rozwiązanie będzie używany jako początkowy stan testów. Powinno być niezależne od rozwiązania, w którym zapisu rozszerzenia UML i jego testów jednostkowych. Aby uzyskać więcej informacji, zobacz [UML tworzenie projektów i diagramów modelowania](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
3. **W projekcie rozszerzenia UML**, Edytuj plik csproj jako tekst i upewnij się, że następujące wiersze, Pokaż `true`:  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     Aby edytować plik .csproj jako tekst, wybierz pozycję **Zwolnij projekt** menu skrótów projektu w Eksploratorze rozwiązań. Następnie wybierz **Edytuj. .csproj**. Po zakończeniu edycji tekstu, wybierz **Załaduj ponownie projekt**.  
  
4. W projekcie rozszerzenia UML, należy dodać następujący wiersz do **Properties\AssemblyInfo.cs**. Dzięki temu testów jednostkowych, aby dostęp do metod, które chcesz przetestować:  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5. **W projekcie testów jednostkowych**, Dodaj następujące odwołania do zestawów:  
  
    - *Projekt rozszerzenia UML*  
  
    - **EnvDTE.dll**  
  
    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    - **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**  
  
    - **Microsoft.VisualStudio.Uml.Interfaces.dll**  
  
    - **Microsoft.VSSDK.TestHostFramework.dll**  
  
6. Prefiks atrybutu `[HostType("VS IDE")]` do każdej metody testowej, włączając w to metody inicjowania.  
  
     Pozwoli to zagwarantować, że testy zostaną uruchomione w eksperymentalnym wystąpieniu programu Visual Studio.  
  
## <a name="DTE"></a> Uzyskiwanie dostępu do obiektu DTE i ModelStore  
 Napisanie metody, aby otworzyć projekt modelowania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Zazwyczaj chcesz otworzyć to rozwiązanie tylko raz w każdym przebiegu testu. Aby uruchomić metody tylko raz, prefiks metody z `[AssemblyInitialize]` atrybutu. Nie zapomnij również muszą atrybutu [HostType ("środowiska IDE programu VS")] dla każdej metody testowej.  Na przykład:  
  
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
        // http://msdn.microsoft.com/library/ee791691.aspx  
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
  
 Jeśli wystąpienie <xref:EnvDTE.Project?displayProperty=fullName> reprezentuje projekcie modelowania, a następnie można go rzutować do i z <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>.  
  
## <a name="Opening"></a> Otwieranie diagramu modelu  
 Dla każdego testu lub klas testów zazwyczaj chcesz pracować Otwórz diagram. W poniższym przykładzie użyto `[ClassInitialize]` atrybut, który wykonuje tę metodę przed innymi metodami w tej klasie testu. Ponownie nie należy zapominać, również muszą atrybutu [HostType ("środowiska IDE programu VS")] dla każdej metody testowej:  
  
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
  
## <a name="UiThread"></a> Wykonaj zmiany modelu w wątku interfejsu użytkownika  
 Jeśli testy lub metody w ramach badania, zmienić magazyn modeli, następnie należy wykonać je w wątku interfejsu użytkownika. Jeśli nie zrobisz, możesz zobaczyć `AccessViolationException`. W wywołaniu Invoke, należy dołączyć kod metody testowej:  
  
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
  
## <a name="MEF"></a> Testowanie polecenia, gestu i inne składniki MEF  
 Składniki MEF Użyj deklaracje właściwości, które mają `[Import]` atrybutu, a których wartości są ustawiane przez ich hostów. Zazwyczaj takie właściwości obejmują IDiagramContext SVsServiceProvider i ILinkedUndoContext. Podczas testowania metodą, która wykorzystuje dowolne z tych właściwości należy ustawić ich wartości przed wykonaniem testowaną metodę. Na przykład jeśli napisano rozszerzeniem polecenie podobne do tego kodu:  
  
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
  
 Następnie można ustawić właściwości importowanych w następujący sposób:  
  
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
  
 Jeśli chcesz przetestować metody, która przyjmuje zaimportowaną właściwość jako parametr, a następnie można zaimportować właściwości do klasy testowej i zastosować `SatisfyImportsOnce` do wystąpienia testu. Na przykład:  
  
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
  
 W tym przykładzie dwa atrybuty dla każdej metody testowej są łączone dla wygody w jednym wierszu.  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>Dostęp do metody prywatne i zmiennych z testów  
 Czasami chcesz przetestować metodę, która jest prywatny, lub chcesz sprawdzić stan pola, które są prywatne, przed i po wykonaniu metody w ramach testu. Przedstawia trudności, ponieważ nie jest rozróżniana w osobnym zestawie do klas w ramach testu. Istnieje kilka taktyka, które należy rozważyć, takie jak następujące:  
  
 Testowanie tylko przy użyciu publicznych i wewnętrznych elementów  
 Pisania testów, tak aby używały tylko publiczne (lub wewnętrznym) klas i składowych. Jest to najlepsze podejście. Testy będą nadal działać, nawet jeśli zrefaktoryzujesz wewnętrzną implementację zestawu, w ramach testu. Stosując te same testy przed i po nim zmiany, można mieć pewność, że zmiany nie zmieniono zachowanie zestawu.  
  
 Aby to umożliwić, może być zmiana struktury kodu. Na przykład może być konieczne rozdzielić niektóre metody na inną klasę.  
  
 Dzięki zapewnieniu bardzo ważna kwestia tego podejścia, często znajdziesz czy kod jest łatwiejsza do odczytu i zmiany, a mniej prone błędy podczas zmiany są wymagane.  
  
 Możesz zezwolić zestawu testowego uzyskiwać dostęp do wewnętrznych elementów, dodając atrybut w **Properties\AssemblyInfo.cs** w projekcie, który ma zostać przetestowana:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Zdefiniuj interfejs testu  
 Zdefiniuj interfejs, który obejmuje zarówno publiczne elementy członkowskie klasy do przetestowania, a dodatkowe właściwości i metody dla prywatnych elementów członkowskich, które mają testy, aby mieć możliwość użycia. Ten interfejs należy dodać do projektu, który ma zostać przetestowana. Na przykład:  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 Dodaj metody klasy do przetestowania, aby jawnie implementować metody dostępu. Zachowaj te dodatkowe metody niezależnie od głównej klasy, zapisując je w definicji klasy częściowej w oddzielnym pliku. Na przykład:  
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 Zezwalaj na zestawu testów do użycia interfejsów testu, dodając ten atrybut do zestawu, która jest testowana:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 W przypadku metody testów jednostkowych za pomocą interfejsu testu. Na przykład:  
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 Zdefiniuj metody dostępu przy użyciu odbicia  
 Jest to sposób, że firma Microsoft zaleca najmniej. Starsze wersje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podane narzędzie, które są tworzone automatycznie dla każdej metody prywatnej metody dostępu. Mimo że jest to wygodne, nasze środowisko sugeruje, że zwykle powoduje testy jednostkowe, które są bardzo silnie sprzężona wewnętrznej struktury aplikacji, poddawanego testom. Skutkuje to dodatkowej pracy po zmianie wymagań lub architektura, ponieważ testy mają zostać zmienione wraz z wdrożenia. Ponadto błędne założenia w projekcie wdrożenia również są wbudowane w testów, tak, aby testy nie uważają, że błędy.  
  
## <a name="see-also"></a>Zobacz też  
 [Anatomia testu jednostkowego](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML — szybka wejścia przy użyciu tekstu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)
