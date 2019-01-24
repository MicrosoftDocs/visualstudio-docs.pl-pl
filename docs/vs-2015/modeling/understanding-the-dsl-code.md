---
title: Znajomość kodu DSL | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
ms.assetid: 8e5c10e4-6323-433e-b88a-5d3d92639030
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fc0db508fc06cc5b80db589ba7ebd88bc3221be
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777455"
---
# <a name="understanding-the-dsl-code"></a>Znajomość kodu DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozwiązania języka specyficznego dla domeny (DSL) generuje interfejs API, który umożliwia odczytywanie i aktualizowanie wystąpienia elementu DSL w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ten interfejs API jest zdefiniowana w kodzie, który jest generowany na podstawie definicji DSL. W tym temacie opisano generowanego interfejsu API.  
  
## <a name="the-example-solution-component-diagrams"></a>W rozwiązaniu przykładowym: Diagramy składników  
 Aby utworzyć rozwiązanie, który jest źródłem Większość przykładów w tym temacie, należy utworzyć DSL z **modeli składnika** szablonu rozwiązania. Jest to jeden z szablonów standardowych, które pojawia się podczas tworzenia nowego rozwiązania języka DSL.  
  
> [!NOTE]
>  Szablon języka DSL diagramów składników nie jest związana z diagramy składników UML, które można utworzyć za pomocą menu architektury w programie Visual Studio. W **nowy projekt** okna dialogowego rozwiń **inne Types\Extensibility projektu** a następnie kliknij przycisk **projektanta języka specyficznego dla domeny**.  
  
 Naciśnij klawisz F5 i eksperymentowania, jeśli nie jesteś zaznajomiony z tym szablonie rozwiązania. Należy zauważyć w szczególności utworzyć portów, przeciągając narzędzie portu na składnik, a następnie połączyć porty.  
  
 ![Składniki i wzajemnie połączonych porty](../modeling/media/componentsample.png "ComponentSample")  
  
## <a name="the-structure-of-the-dsl-solution"></a>Struktury rozwiązania DSL  
 **Dsl** projektu definiuje interfejs API dla DSL. **DslPackage** projektu definiuje, jak zintegrować go z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Można również dodać własne projektów, które również mogą zawierać kod generowany z modelu.  
  
### <a name="the-code-directories"></a>Katalogi kodu  
 Większość kodu w każdym z tych projektów jest generowany na podstawie **Dsl\DslDefinition.dsl**. Wygenerowany kod znajduje się w **wygenerowany kod** folderu. Aby wyświetlić wygenerowany plik, kliknij **[+]** obok Generowanie **.tt** pliku.  
  
 Firma Microsoft zaleca sprawdzenie wygenerowany kod, aby lepiej zrozumieć język DSL. Aby wyświetlić wygenerowanych plików, rozwiń pliki *.tt w Eksploratorze rozwiązań.  
  
 \*.TT — pliki zawierają bardzo mało generowania kodu. Zamiast tego należy użyć `<#include>` dyrektywy dołączać pliki udostępnione szablonu. Udostępnione pliki znajdują się w **\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates**  
  
 Po dodaniu kodu źródłowego do rozwiązania DSL, należy go dodać w oddzielnym pliku poza folderem wygenerowany kod. Możesz chcieć utworzyć **kod niestandardowy** folderu. (Po dodaniu nowego pliku kodu do folderu niestandardowego, pamiętaj, aby poprawić przestrzeni nazw w szkielet kodu początkowego.)  
  
 Zdecydowanie zalecamy nie edytowanie wygenerowanego kodu bezpośrednio, ponieważ Twoje zmiany zostaną utracone podczas ponownego kompilowania rozwiązania. Zamiast tego aby dostosować DSL:  
  
-   Dostosuj wiele parametrów w definicji DSL.  
  
-   Zapisać klas częściowych w plikach osobnego kodu do metody zastąpienia, które są zdefiniowane w lub dziedziczone przez klasy generowane. W niektórych przypadkach należy ustawić **Generates Double Derived** opcji klasy w definicji DSL, aby można było przesłonić metodę wygenerowany.  
  
-   Ustaw opcje w definicji DSL, powodującą, że wygenerowany kod w celu zapewnienia "hooks" własnego kodu.  
  
     Na przykład jeśli ustawisz **ma Konstruktor niestandardowy** opcji klasę domeny i następnie Skompiluj rozwiązanie, zostanie wyświetlony komunikaty o błędach. Po dwukrotnym kliknięciu jednego z tych komunikatów o błędach, będą widzieć żadnych komentarzy w wygenerowanym kodzie, objaśniające, co powinno zapewniać kod niestandardowy.  
  
-   Napisać własne szablony tekstu, aby wygenerować kod specyficzne dla aplikacji. Można Użyj pliki można dołączać do udostępniania części szablonów, które są wspólne dla wielu projektów i tworzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] następujące szablony projektów, które są inicjowane z strukturę pliku projektu.  
  
## <a name="generated-files-in-dsl"></a>Wygenerowane pliki w Dsl  
 Następujące wygenerowanych plików są wyświetlane w **Dsl** projektu.  
  
 *YourDsl* `Schema.xsd`  
  
 Schemat dla plików, który zawiera wystąpienia elementu DSL. Ten plik jest kopiowany do kompilacji (**bin**) katalogu. Po zainstalowaniu DSL, możesz skopiować ten plik, aby **11.0\Xml\Schemas programu Visual Studio \Program Files\Microsoft** , dzięki czemu można zweryfikować plików modelu. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
 Jeśli dostosowujesz serializacji, ustawiając opcje w Eksplorator DSL schematu zostanie zmieniona. Jednak jeśli piszesz kod serializacji, ten plik nie jest już może reprezentować rzeczywiste schematu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
 `ConnectionBuilders.cs`  
  
 Konstruktor połączeń to klasa, która umożliwia tworzenie relacji. Jest kod związany z narzędziem do połączenia. Ten plik zawiera parę klasy dla każdego z narzędzi połączenia. Ich nazwy są uzyskiwane z nazwy domeny narzędzie relacji i połączenia: *Relacja*konstruktora, a *ConnectorTool*ConnectAction.  
  
 (W tym przykładzie rozwiązania składnika nosi nazwę jednego z konstruktorów połączenia elementu ConnectionBuilder, to zbieżność, ponieważ relacja domeny nosi nazwę połączenie).  
  
 Relacja jest tworzony w *relacji* `Builder.Connect()` metody. Domyślna wersja sprawdza, czy elementy modelu źródłowe i docelowe są akceptowane i następnie tworzy wystąpienie relacji. Na przykład:  
  
 `CommentReferencesSubject(sourceAccepted, targetAccepted);`  
  
 Każda klasa konstruktora jest generowany na podstawie węzła w **konstruktory połączeń** sekcji Eksplorator DSL. Jeden `Connect` metoda można tworzyć relacje między jedną lub więcej par klasy domeny. Każda para jest definiowany przez łącze połączyć dyrektywy, który znajduje się w Eksplorator DSL węźle konstruktora.  
  
 Na przykład można dodać do jednego konstruktora połączeń dyrektywy łączenia Linku dla każdego z trzech rodzajów relacji w przykładzie DSL. To będzie udostępniać użytkownikom za pomocą narzędzia pojedynczego połączenia. Typ relacji wystąpienia zależą od typów elementów źródłowych i docelowych, wybranej przez użytkownika.  Aby dodać dyrektywy łączenia Linku, kliknij prawym przyciskiem myszy konstruktora w Eksplorator DSL.  
  
 Do napisania kodu niestandardowego, który jest uruchamiany, gdy określony typ relacji domeny jest tworzony, wybierz odpowiednie dyrektywy łączenia łącze w węźle konstruktora. W oknie właściwości ustaw **korzysta z połączenia niestandardowego**. Ponownie skompiluj rozwiązanie, a następnie podaj kod, aby poprawić błędy wynikowe.  
  
 Aby napisać kod niestandardowy, który zawsze wtedy, gdy użytkownik korzysta z narzędzia połączenia z tym, należy ustawić **jest niestandardowy** właściwości konstruktora połączeń. Możesz podać kod, który decyduje, czy element źródła jest dozwolone, czy określona kombinacja źródła jest dozwolona w docelowym i aktualizacji co powinny zostać wprowadzone do modelu po nawiązaniu połączenia. Na przykład tylko wtedy, gdy nie może utworzyć pętlę w diagramie można zezwolić na połączenia. Zamiast jednej relacji łącza można utworzyć wystąpienia bardziej złożonych wzorca z kilku elementów wzajemnie powiązanych w elemencie źródłowym i docelowym.  
  
 `Connectors.cs`  
  
 Zawiera klasy dla łączników, które są elementy diagramu, które zazwyczaj reprezentują relacje odniesienia. Każda klasa jest generowany na podstawie jeden łącznik w definicji DSL. Każda klasa łącznika jest tworzony na podstawie <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 Aby kolor i niektórych innych zmiennych funkcji stylu w czasie wykonywania, kliknij prawym przyciskiem myszy klas na diagramie w definicji DSL, a następnie wskaż **Dodaj udostępniane**.  
  
 Aby wprowadzić zmienną funkcje dodatkowe style w czasie wykonywania, na przykład zobacz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.  
  
 `Diagram.cs`  
  
 Zawiera klasę, która definiuje diagram. Jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.  
  
 Aby kolor i niektórych innych zmiennych funkcji stylu w czasie wykonywania, kliknij prawym przyciskiem myszy klas na diagramie w definicji DSL, a następnie wskaż **Dodaj udostępniane**.  
  
 Ponadto, ten plik zawiera `FixupDiagram` reguły, która reaguje, gdy nowy element zostanie dodany do modelu. Reguła doda nowy kształt i łączy kształtu do elementu modelu.  
  
 `DirectiveProcessor.cs`  
  
 Procesor dyrektywy pomaga użytkownikom pisania szablonów tekstowych, które wystąpienie DSL. Procesor dyrektywy ładuje zestawy (dll) dla DSL i efektywnie wstawia `using` instrukcje dla swojego obszaru nazw. Dzięki temu kod w szablonach tekstowych, aby użyć klasy i relacje, które zostały zdefiniowane w DSL.  
  
 Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) i [Tworzenie niestandardowych procesorów T4 dotyczącej tekstu szablonu dyrektywy](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 `DomainClasses.cs`  
  
 Implementacje klasy domeny, które zdefiniowano, w tym klasy abstrakcyjne i klasa głównym modelu. Pochodzą one od <xref:Microsoft.VisualStudio.Modeling.ModelElement>.  
  
 Każda klasa domeny zawiera:  
  
- Definicja właściwości i klasy zagnieżdżone obsługi dla każdej właściwości domeny. Można zastąpić OnValueChanging() i OnValueChanged(). Aby uzyskać więcej informacji, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).  
  
   W przykładzie w języku DSL `Comment` klasy zawiera właściwość `Text` i klasę programu obsługi `TextPropertyHandler`.  
  
- Metoda dostępu właściwości relacji, w których uczestniczy tą klasą domeny. (Brak jest nie klasy zagnieżdżonej dla właściwości roli).  
  
   W przykładzie w języku DSL `Comment` klasa ma metody dostępu uzyskujących dostęp do jego nadrzędnego modelu przy użyciu relacji osadzania `ComponentModelHasComments`.  
  
- Konstruktory. Jeśli chcesz je zastąpić, ustaw **ma Konstruktor niestandardowy** dla klasy domeny.  
  
- Metody obsługi grupy prototyp (EGP) elementu. Są one niezbędne, jeśli użytkownik może *scalania* (Dodaj) inny element do wystąpienia tej klasy. Zazwyczaj użytkownik robi to poprzez przeciąganie z narzędziem element lub innego kształtu lub wklejając.  
  
   W przykładzie na składnika można scalić DSL, dane wejściowe portu lub dane wyjściowe. Ponadto składniki i komentarze scalimy na modelu. Program  
  
   Metody obsługi EGP w klasie składnika Zezwalaj na składnik do akceptowania portów, ale nie komentarzy. Program obsługi EGP w klasie modelu głównego akceptuje komentarze i składników, ale nie portów.  
  
  `DomainModel.cs`  
  
  Klasa, która reprezentuje modelu domeny. Jest pochodną <xref:Microsoft.VisualStudio.Modeling.DomainModel>.  
  
> [!NOTE]
>  Nie jest taka sama jak klasa główna modelu.  
  
 Kopiuj i Usuń zamknięcia definiują, co inne elementy powinny być włączone, gdy element zostanie skopiowany lub usunięty. To zachowanie można kontrolować przez ustawienie **propaguje kopiowania** i **propaguje usunąć** właściwości ról na każdej stronie każda relacja. Jeśli chcesz, aby wartości, które mają być określany dynamicznie, można napisać kod, aby przesłonić metody klasy zamknięcia. Aby uzyskać więcej informacji, zobacz [jak: Program kopiowania i wklejania zachowanie — przekierowanie](../misc/how-to-program-copy-and-paste-behavior-redirect.md).  
  
 `DomainModelResx.resx`  
  
 Zawiera ciągi, takich jak opisy klasami domeny i właściwości, nazwy właściwości, etykiety przybornika, standardowy błąd wiadomości i innych ciągów, które mogą być wyświetlane dla użytkownika. Zawiera także ikon narzędzi i obrazy kształtów obrazu.  
  
 Ten plik jest powiązany do wbudowany zestaw i zapewnia wartości domyślne tych zasobów. Można lokalizować DSL, tworząc zestawu satelickiego zawierającego zlokalizowaną wersję zasobów. Ta wersja będzie służyć język DSL jest zainstalowany w kulturze, dopasowując zasoby zlokalizowane. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
 `DomainRelationships.cs`  
  
 Każde łącze między dwoma elementami w modelu jest reprezentowany przez wystąpienie klasy relacji domeny. Wszystkie klasy relacji są uzyskiwane z <xref:Microsoft.VisualStudio.Modeling.ElementLink>, który z kolei pochodzi od <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Ponieważ jest ona zarządzanie magazynem, wystąpienie relacji może mieć właściwości i może być źródłową lub docelową relacji.  
  
 `HelpKeywordHelper.cs`  
  
 Oferuje funkcje, które są używane, gdy użytkownik naciśnie klawisz F1.  
  
 `MultiplicityValidation.cs`  
  
 Role relacji, której określić liczebność 1..1 lub 1.. *, użytkownik zostanie ostrzeżony tego co najmniej jedno wystąpienie relacji jest wymagana. Ten plik zawiera ograniczenia sprawdzania poprawności, które implementują tych ostrzeżeń. 1..1 link osadzania nadrzędny nie został zweryfikowany.  
  
 Dla tych warunków ograniczających do wykonania, musi być zainstalowany jeden z **używa...**  opcji na liście **Editor\Validation** węzła w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
 `PropertiesGrid.cs`  
  
 Ten plik zawiera kod, tylko wtedy, gdy dołączysz deskryptorze typu niestandardowego z właściwością domeny. Aby uzyskać więcej informacji, zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).  
  
 `SerializationHelper.cs`  
  
- Metoda sprawdzania poprawności, aby upewnić się, czy nie dwa elementy odwołują się tej samej krótkiej nazwy. Aby uzyskać więcej informacji, zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
- Klasa SerializationHelper dostarcza funkcje, które często używanych przez klasy serializacji.  
  
  `Serializer.cs`  
  
  Klasa serializatorów dla każdej klasy domeny, relacji, kształt, łącznik, diagramu i modelu.  
  
  Wiele funkcji w ramach tych zajęć kontrolowana przez ustawienia w Eksplorator DSL w obszarze **zachowanie serializacji kodu Xml**.  
  
  `Shapes.cs`  
  
  Klasa, dla każdej klasy kształtu w definicji DSL. Kształty są uzyskiwane z <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Aby uzyskać więcej informacji, zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
  Aby zastąpić wygenerowane metody przy użyciu metody w klasie częściowej, należy ustawić **Generates Double Derived** dla łącznika w definicji DSL. Aby zastąpić konstruktora z własnym kodem, ustaw **ma Konstruktor niestandardowy**.  
  
  Aby kolor i niektórych innych zmiennych funkcji stylu w czasie wykonywania, kliknij prawym przyciskiem myszy klas na diagramie w definicji DSL, a następnie wskaż **Dodaj udostępniane**.  
  
  Aby wprowadzić zmienną funkcje dodatkowe style w czasie wykonywania, na przykład zobacz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
  `ToolboxHelper.cs`  
  
  Konfiguruje, instalując element grupy prototypów do narzędzi elementów przybornika. Kopie tych prototypów są scalane z elementów docelowych, gdy użytkownik uruchomi narzędzie.  
  
  Można zastąpić `CreateElementPrototype()` zdefiniować element przybornika, który tworzy grupę kilka obiektów. Na przykład można zdefiniować elementu do reprezentowania obiektów, które składniki podrzędne. Po zmianie kodu, zresetuj wystąpienie eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aby wyczyścić pamięć podręczną przybornika.  
  
## <a name="generated-files-in-the-dslpackage-project"></a>Wygenerowane pliki w projekcie DslPackage  
 DslPackage couples modelu DSL, który ma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powłoki, zarządzanie okno przybornika i menu poleceń. Większość klas są double derived, dzięki czemu można przesłonić z ich metod.  
  
 `CommandSet.cs`  
  
 Polecenia menu kontekstowego, które są widoczne na diagramie. Można dostosować lub dodać do tego zestawu. Ten plik zawiera kod dla polecenia. Lokalizacja poleceń w menu jest określany przez plik Commands.vsct. Aby uzyskać więcej informacji, zobacz [pisanie poleceń i akcji użytkownika](../modeling/writing-user-commands-and-actions.md).  
  
 `Constants.cs`  
  
 GUIDs.  
  
 `DocData.cs`  
  
 *YourDsl* `DocData` zarządza ładowania i zapisywania modelu do pliku i tworzy wystąpienie Store.  
  
 Na przykład, jeśli chcesz zapisać DSL w bazie danych, a nie plikiem, można zastąpić `Load` i `Save` metody.  
  
 `DocView.cs`  
  
 *YourDsl* `DocView` zarządza okna, w którym pojawia się diagramu. Na przykład można osadzić diagramu w formularzu systemu windows:  
  
 Dodaj plik kontrolki użytkownika do projektu DslPackage. Dodaj Panel, w którym można wyświetlić diagram. Dodawanie przycisków i innych kontrolek. W widoku kodu formularza Dodaj następujący kod, dostosowując nazwy DSL:  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Drawing;  
using System.Data;  
using System.Linq;  
using System.Text;  
using System.Windows.Forms;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Shell;  
  
namespace Company.EmbedInForm  
{  
  public partial class UserControl1 : UserControl  
  {  
    public UserControl1()  
    {  
      InitializeComponent();  
    }  
  
    private DiagramDocView docView;  
  
    public UserControl1(DiagramDocView docView, Control content)  
      : this()  
    {  
      this.docView = docView;  
      panel1.Controls.Add(content);  
    }  
  
    private void button1_Click(object sender, EventArgs e)  
    {  
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      foreach (ExampleElement element in modelRoot.Elements)  
      {  
       listBox1.Items.Add(element.Name);  
      }  
    }  
  }  
  internal partial class EmbedInFormDocView  
  {  
  
    private ContainerControl container;  
  
    /// <summary>  
    /// Return a User Control instead of the DSL window.   
    /// The user control will contain the DSL window.  
    /// </summary>  
  
    public override System.Windows.Forms.IWin32Window Window  
    {  
      get  
      {  
        if (container == null)  
        {  
          // Put the normal DSL Window inside our control  
          container = new UserControl1(this, (Control)base.Window);  
        }  
        return container;  
      }  
    }  
  }  
  
}  
  
```  
  
 `EditorFactory.cs`  
  
 Tworzy wystąpienie `DocData` i `DocView`. Spełnia ona standard interfejs, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa, aby otworzyć Edytor, po uruchomieniu pakietu języka DSL. Odwołuje się do niego `ProvideEditorFactory` atrybutu w Package.cs  
  
 `GeneratedVSCT.vsct`  
  
 Lokalizuje standardowych poleceń w menu, takich jak menu kontekstowego diagram **Edytuj** menu i tak dalej. Kod dla poleceń znajduje się w CommandSet.cs. Można przenosić lub zmodyfikować poleceń standardowych i można dodać własne polecenia. Aby uzyskać więcej informacji, zobacz [pisanie poleceń i akcji użytkownika](../modeling/writing-user-commands-and-actions.md).  
  
 `ModelExplorer.cs`  
  
 Definiuje Eksploratora modelu dla DSL. Jest to widok drzewa modelu, który użytkownik zobaczy wraz z diagramu.  
  
 Na przykład, można zastąpić `InsertTreeView()` Aby zmienić kolejność wyświetlania elementów w Eksploratorze modelu.  
  
 Wybór w Eksploratorze modelu, aby zachować synchronizację z zaznaczenia diagramu, można użyć następującego kodu:  
  
```  
protected override void OnSelectionChanged(global::System.EventArgs e)  
{  
base.OnSelectionChanged(e);  
// get the selected element  
DslModeling::ModelElement selectedElement =   
this.PrimarySelection as DslModeling::ModelElement;  
// Select in the model explorer  
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);  
}  
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)  
where T : DslShell.ModelExplorerToolWindow  
{  
DslShell::ModelingPackage package =   
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;  
  
if (package != null)  
{  
// find the model explorer window  
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;  
if (explorerWindow != null)  
{  
// get the tree container  
DslShell.ModelExplorerTreeContainer treeContainer =   
explorerWindow.TreeContainer;  
// find the tree node  
DslShell.ExplorerTreeNode treeNode =   
treeContainer.FindNodeForElement(modelElement);  
// select the node  
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;  
}  
}  
}  
  
```  
  
 `ModelExplorerToolWindow.cs`  
  
 Definiuje okno, w którym jest wyświetlany w Eksploratorze modelu. Obsługuje wyboru elementów w Eksploratorze.  
  
 `Package.cs`  
  
 Ten plik definiuje, jak język DSL integruje się z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Atrybuty w klasie pakietu zarejestrować język DSL jako program obsługi dla plików, które mają rozszerzenia pliku, zdefiniuj jego przybornika i określić sposób otworzyć nowe okno. Metoda Initialize() jest wywoływana jeden raz, gdy pierwszy DSL jest ładowany do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wystąpienia.  
  
 `Source.extension.vsixmanifest`  
  
 Aby dostosować ten plik, Edytuj `.tt` pliku.  
  
> [!WARNING]
>  Po zmodyfikowaniu pliku .tt, aby uwzględnić zasoby, takie jak ikony lub obrazów, upewnij się, czy zasób jest uwzględniony w kompilacji VSIX. W Eksploratorze rozwiązań wybierz plik, a następnie upewnij się, że **Include w VSIX** właściwość `True`.  
  
 Ten plik Określa, jak język DSL jest spakowany w Visual Studio Integration rozszerzenie (VSIX). Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak zdefiniować języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
 [Objaśnienie modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)   
 [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
