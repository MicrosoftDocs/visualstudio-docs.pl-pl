---
title: Informacje o kodzie DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
ms.assetid: 8e5c10e4-6323-433e-b88a-5d3d92639030
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e8d82712a2fb8e30b13f9f369bf87be5292c199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659491"
---
# <a name="understanding-the-dsl-code"></a>Znajomość kodu DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozwiązanie języka specyficznego dla domeny (DSL) generuje interfejs API, za pomocą którego można odczytywać i aktualizować wystąpienia DSL w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ten interfejs API jest zdefiniowany w kodzie, który jest generowany na podstawie definicji DSL. W tym temacie opisano wygenerowany interfejs API.

## <a name="the-example-solution-component-diagrams"></a>Przykładowe rozwiązanie: diagramy składników
 Aby utworzyć rozwiązanie, które jest źródłem większości przykładów w tym temacie, Utwórz DSL na podstawie szablonu rozwiązania **model składników** . Jest to jeden z szablonów standardowych, które pojawiają się podczas tworzenia nowego rozwiązania DSL.

> [!NOTE]
> Schemat DSL diagramów składników nie jest powiązany ze diagramami składników UML, które można utworzyć przy użyciu menu architektura w programie Visual Studio. W oknie dialogowym **Nowy projekt** rozwiń pozycję **inne Types\Extensibility projektu** , a następnie kliknij przycisk **Projektant języka specyficznego dla domeny**.

 Naciśnij klawisz F5 i Eksperymentuj, jeśli nie znasz tego szablonu rozwiązania. Zwróć uwagę na to, że tworzysz porty, przeciągając narzędzie portu na składnik, a także łącząc porty.

 ![Składniki i połączone porty](../modeling/media/componentsample.png "ComponentSample")

## <a name="the-structure-of-the-dsl-solution"></a>Struktura rozwiązania DSL
 Projekt **DSL** definiuje interfejs API dla języka DSL. Projekt **DslPackage** definiuje, w jaki sposób integruje się z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Możesz również dodać własne projekty, które mogą również zawierać kod generowany na podstawie modelu.

### <a name="the-code-directories"></a>Katalogi kodu
 Większość kodu w każdym z tych projektów jest generowana z **Dsl\DslDefinition.DSL**. Wygenerowany kod znajduje się w folderze **wygenerowanego kodu** . Aby wyświetlić wygenerowany plik, kliknij przycisk **[+]** obok wygenerowanego pliku. **TT** .

 Zalecamy sprawdzenie wygenerowanego kodu, aby pomóc w zrozumieniu DSL. Aby wyświetlić wygenerowane pliki, rozwiń pliki *. tt w Eksplorator rozwiązań.

 Pliki \*. tt zawierają bardzo mały wygenerowany kod. Zamiast tego wykorzystują dyrektywy `<#include>` do dołączania udostępnionych plików szablonów. Udostępnione pliki można znaleźć w **folderze \Program Files\Microsoft Visual Studio 10.0 \ COMMON7\IDE\EXTENSIONS\MICROSOFT\DSL SDK\DSL Designer\11.0\TextTemplates**

 Dodając własny kod programu do rozwiązania DSL, Dodaj go do oddzielnego pliku poza wygenerowanym folderem kodu. Może być konieczne utworzenie niestandardowego folderu **kodu** . (Po dodaniu nowego pliku kodu do folderu niestandardowego Pamiętaj o skorygowaniu przestrzeni nazw w początkowym szkieletzie kodu).

 Zdecydowanie zalecamy, aby nie edytować wygenerowanego kodu bezpośrednio, ponieważ zmiany zostaną utracone podczas odbudowywania rozwiązania. Zamiast tego, aby dostosować DSL:

- Dostosuj wiele parametrów w definicji DSL.

- Zapisuj klasy częściowe w oddzielnych plikach kodu, aby przesłonić metody, które są zdefiniowane w, lub dziedziczone przez, wygenerowane klasy. W niektórych przypadkach należy ustawić opcję **Generuj podwójnie pochodną** klasy w definicji DSL, aby można było zastąpić wygenerowaną metodę.

- Ustaw opcje w definicji DSL, które powodują, że wygenerowany kod zapewnia "haki" dla własnego kodu.

     Na przykład jeśli ustawisz opcję **ma niestandardowy Konstruktor** klasy domeny, a następnie skompilujesz rozwiązanie, zobaczysz komunikaty o błędach. Po dwukrotnym kliknięciu jednego z tych komunikatów o błędach zobaczysz komentarze w wygenerowanym kodzie, który wyjaśni, jakie dane mają być podane w kodzie niestandardowym.

- Napisz własne szablony tekstowe, aby wygenerować kod specyficzny dla aplikacji. Można użyć plików dołączanych do udostępniania części szablonów, które są wspólne dla wielu projektów, i można utworzyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonów projektu, aby skonfigurować projekty, które są inicjowane przy użyciu własnej struktury plików.

## <a name="generated-files-in-dsl"></a>Wygenerowane pliki w DSL
 Następujące wygenerowane pliki pojawiają się w projekcie **DSL** .

 *YourDsl* `Schema.xsd`

 Schemat dla plików, które zawierają wystąpienia elementu DSL. Ten plik jest kopiowany do katalogu kompilacji (**bin**). Podczas instalowania programu DSL można skopiować ten plik do **folderu \Program Files\Microsoft Visual Studio 11.0 \ Xml\Schemas** , aby umożliwić zweryfikowanie plików modelu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

 W przypadku dostosowania serializacji przez ustawienie opcji w Eksploratorze DSL schemat zostanie odpowiednio zmieniony. Jednak jeśli piszesz własny kod serializacji, ten plik może już nie reprezentować rzeczywistego schematu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie serializacji File Storage i XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Konstruktor połączeń jest klasą, która tworzy relacje. Jest to kod za narzędziem połączenia. Ten plik zawiera parę klas dla każdego narzędzia połączenia. Ich nazwy są uzyskiwane z nazw i narzędzi do łączenia z domeną: Konstruktor *relacji*i *ConnectorTool*ConnectAction.

 (W przykładowym rozwiązaniu składnika jeden z konstruktorów połączeń nosi nazwę elemencie ConnectionBuilder, jest to współdziałanie, ponieważ relacja domeny nosi nazwę połączenie).

 Relacja jest tworzona w metodzie `Builder.Connect()` *relacji* . Wersja domyślna sprawdza, czy źródłowe i docelowe elementy modelu są akceptowalne, a następnie tworzy wystąpienie relacji. Na przykład:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Każda klasa konstruktora jest generowana z węzła w sekcji **konstruktorzy połączeń** w Eksploratorze DSL. Jedna `Connect` Metoda może tworzyć relacje między jedną lub większą liczbą par klas domeny. Każda para jest definiowana przez dyrektywę Connect link, którą można znaleźć w Eksploratorze DSL w węźle Konstruktor.

 Można na przykład dodać do jednej z trzech typów relacji w przykładowej linii DSL. Spowoduje to udostępnienie użytkownikowi narzędzia z pojedynczym połączeniem. Typ wystąpienia relacji będzie zależeć od typów elementów źródłowych i docelowych wybranych przez użytkownika.  Aby dodać dyrektywy łączenia linków, kliknij prawym przyciskiem myszy konstruktora w Eksploratorze DSL.

 Aby napisać niestandardowy kod, który jest uruchamiany po utworzeniu określonego typu relacji domeny, wybierz odpowiednią dyrektywę Połącz link w węźle Konstruktor. W okno Właściwości ustaw opcję **Użyj połączenia niestandardowego**. Skompiluj ponownie rozwiązanie, a następnie podaj kod w celu skorygowania występujących błędów.

 Aby napisać niestandardowy kod, który jest uruchamiany za każdym razem, gdy użytkownik korzysta z tego narzędzia połączenia, ustaw właściwość **jest niestandardowa** konstruktora połączeń. Można podać kod, który decyduje o tym, czy element źródłowy jest dozwolony, czy określona kombinacja źródłowa i docelowa jest dozwolona i jakie aktualizacje powinny zostać wprowadzone do modelu po nawiązaniu połączenia. Na przykład można zezwolić na połączenie tylko wtedy, gdy nie utworzy pętli na diagramie. Zamiast pojedynczego łącza relacji można utworzyć wystąpienie bardziej złożonego wzorca kilku elementów powiązanych między źródłem a celem.

 `Connectors.cs`

 Zawiera klasy łączników, które są elementami diagramu, które zwykle reprezentują relacje odwołania. Każda klasa jest generowana z jednego łącznika w definicji DSL. Każda Klasa łączników pochodzi od <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Aby kolor i inne funkcje stylu były zmienne w czasie wykonywania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż polecenie **Dodaj uwidocznione**.

 Aby utworzyć dodatkowe funkcje stylu w czasie wykonywania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Zawiera klasę, która definiuje diagram. Pochodzi ona od <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Aby kolor i inne funkcje stylu były zmienne w czasie wykonywania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż polecenie **Dodaj uwidocznione**.

 Ponadto ten plik zawiera regułę `FixupDiagram`, która reaguje, gdy nowy element zostanie dodany do modelu. Reguła dodaje nowy kształt i łączy kształt z elementem modelu.

 `DirectiveProcessor.cs`

 Ten procesor dyrektywy ułatwia użytkownikom pisanie szablonów tekstowych, które odczytują wystąpienie DSL. Procesor dyrektywy ładuje zestawy (dll) dla DSL i efektywnie wstawia `using` instrukcji dla przestrzeni nazw. Pozwala to kodowi w szablonach tekstowych używać klas i relacji zdefiniowanych w DSL.

 Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) i [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementacje klas domen zdefiniowanych przez użytkownika, w tym klasy abstrakcyjne i klasy głównej modelu. Są one uzyskiwane z <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Każda klasa domeny zawiera:

- Definicja właściwości i zagnieżdżona Klasa obsługi dla każdej właściwości domeny. Można przesłonić OnValueChanging () i OnValueChanged (). Aby uzyskać więcej informacji, zobacz [Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).

   W przykładzie DSL Klasa `Comment` zawiera `Text` właściwości i klasę procedury obsługi `TextPropertyHandler`.

- Właściwości metody dostępu dla relacji, w których uczestniczy Ta klasa domeny. (Nie istnieje Klasa zagnieżdżona dla właściwości roli.)

   W przykładzie DSL Klasa `Comment` ma metody dostępu, które uzyskują dostęp do modelu nadrzędnego za pomocą `ComponentModelHasComments` relacji osadzania.

- Konstruktor. Jeśli chcesz przesłonić te ustawienia, zestaw **ma konstruktora niestandardowego** dla klasy domeny.

- Metody obsługi prototypu grupy elementów (EGP). Są one niezbędne, jeśli użytkownik może *scalić* (dodać) inny element w wystąpieniach tej klasy. Zazwyczaj użytkownik robi to poprzez przeciąganie z narzędzia elementu lub innego kształtu lub przez wklejenie.

   W przykładzie DSL port wejściowy lub port wyjściowy można scalić ze składnikiem. Ponadto składniki i Komentarze można scalać z modelem. Program

   Metody obsługi EGP w klasie składnika umożliwiają składnikowi akceptowanie portów, ale nie komentarzy. Procedura obsługi EGP w klasie modelu głównego akceptuje Komentarze i składniki, ale nie porty.

  `DomainModel.cs`

  Klasa, która reprezentuje model domeny. Pochodzi ona od <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
> Ta wartość nie jest taka sama jak Klasa główna modelu.

 W przypadku kopiowania i usuwania zamknięć Zdefiniuj, jakie inne elementy mają być uwzględniane podczas kopiowania lub usuwania elementu. Możesz kontrolować to zachowanie, ustawiając **kopię propagacji** i **propagowanie** właściwości po każdej stronie każdej relacji. Jeśli chcesz, aby wartości były ustalane dynamicznie, możesz napisać kod, aby zastąpić metody klas zamknięcia. Aby uzyskać więcej informacji [, zobacz jak: programowe zachowanie kopiowania i wklejania — przekierowanie](../misc/how-to-program-copy-and-paste-behavior-redirect.md).

 `DomainModelResx.resx`

 Zawiera ona ciągi takie jak opisy klas domen i właściwości, nazwy właściwości, etykiety przybornika, standardowe komunikaty o błędach i inne ciągi, które mogą być wyświetlane użytkownikowi. Zawiera również ikony narzędzi i obrazy dla kształtów obrazów.

 Ten plik jest powiązany z skompilowanym zestawem i zawiera wartości domyślne tych zasobów. Możesz lokalizować DSL, tworząc zestaw satelicki zawierający zlokalizowaną wersję zasobów. Ta wersja zostanie użyta, gdy program DSL zostanie zainstalowany w kulturze zgodnej z zlokalizowanymi zasobami. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

 `DomainRelationships.cs`

 Każdy link między dwoma elementami w modelu jest reprezentowany przez wystąpienie klasy relacji domeny. Wszystkie klasy relacji pochodzą od <xref:Microsoft.VisualStudio.Modeling.ElementLink>, które z kolei są wyprowadzane z <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Ponieważ jest to ModelElement, wystąpienie relacji może mieć właściwości i może być źródłem lub celem relacji.

 `HelpKeywordHelper.cs`

 Udostępnia funkcje, które są używane, gdy użytkownik naciśnie klawisz F1.

 `MultiplicityValidation.cs`

 W rolach relacji, w których można określić liczebność 1.. 1 lub 1.. *, należy ostrzec użytkownika, że wymagane jest co najmniej jedno wystąpienie relacji. Ten plik zawiera ograniczenia walidacji, które implementują te ostrzeżenia. Link 1.. 1 do osadzania elementu nadrzędnego nie został zweryfikowany.

 Aby można było wykonać te ograniczenia, należy ustawić jedną z opcji **użycia...** w węźle **EDITOR\VALIDATION** w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Ten plik zawiera kod tylko wtedy, gdy został dołączony deskryptor typu niestandardowego do właściwości domeny. Aby uzyskać więcej informacji, zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Metoda walidacji, która zapewnia, że żadne dwa elementy nie odwołują się do tego samego monikera. Aby uzyskać więcej informacji, zobacz [Dostosowywanie serializacji File Storage i XML](../modeling/customizing-file-storage-and-xml-serialization.md).

- Klasa SerializationHelper, która dostarcza funkcje, które są używane wspólnie przez klasy serializacji.

  `Serializer.cs`

  Klasa serializatorów dla każdej klasy domeny, relacji, kształtu, łącznika, diagramu i modelu.

  Wiele funkcji tych klas można kontrolować za pomocą ustawień w Eksploratorze DSL w obszarze **zachowanie serializacji kodu XML**.

  `Shapes.cs`

  Klasa dla każdej klasy kształtu w definicji DSL. Kształty są wyprowadzane z <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Aby uzyskać więcej informacji, zobacz [Dostosowywanie serializacji File Storage i XML](../modeling/customizing-file-storage-and-xml-serialization.md).

  Aby zastąpić wygenerowane metody własnymi metodami w klasie częściowej, zestaw **generuje podwójne pochodne** dla łącznika w definicji DSL. Aby zastąpić Konstruktor własnym kodem, ustaw atrybut **ma konstruktora niestandardowego**.

  Aby kolor i inne funkcje stylu były zmienne w czasie wykonywania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż polecenie **Dodaj uwidocznione**.

  Aby utworzyć dodatkowe funkcje stylu w czasie wykonywania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Konfiguruje Przybornik, instalując prototypy grupy elementów w narzędziach elementów. Kopie tych prototypów są scalane z elementami docelowymi, gdy użytkownik uruchamia narzędzie.

  @No__t_0 można przesłonić w celu zdefiniowania elementu przybornika, który tworzy grupę wielu obiektów. Można na przykład zdefiniować element reprezentujący obiekty, które mają podskładniki. Po zmianie kodu Zresetuj eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby wyczyścić pamięć podręczną przybornika.

## <a name="generated-files-in-the-dslpackage-project"></a>Wygenerowane pliki w projekcie DslPackage
 DslPackage Couples model DSL do powłoki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zarządzania oknem, przybornikiem i poleceniami menu. Większość klas jest podwójnym pochodnym, dzięki czemu można przesłonić dowolną metodę.

 `CommandSet.cs`

 Polecenia menu kontekstowego, które są widoczne na diagramie. Możesz dostosować lub dodać do tego zestawu. Ten plik zawiera kod dla poleceń. Lokalizacja poleceń w menu jest określana przez plik Commands. vsct. Aby uzyskać więcej informacji, zobacz [pisanie poleceń i akcji użytkownika](../modeling/writing-user-commands-and-actions.md).

 `Constants.cs`

 Identyfikatory GUID.

 `DocData.cs`

 *YourDsl* `DocData` zarządza ładowaniem i zapisywaniem modelu do pliku, a następnie tworzy wystąpienie magazynu.

 Jeśli na przykład chcesz zapisać DSL w bazie danych zamiast pliku, możesz przesłonić metody `Load` i `Save`.

 `DocView.cs`

 *YourDsl* `DocView` zarządza oknem, w którym pojawia się diagram. Na przykład można osadzić diagram wewnątrz formularza systemu Windows:

 Dodaj plik kontrolny użytkownika do projektu DslPackage. Dodaj panel, w którym można wyświetlić diagram. Dodaj przyciski i inne kontrolki. W widoku Kod formularza Dodaj następujący kod, dostosowując nazwy do ustawień DSL:

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

 Tworzy wystąpienia `DocData` i `DocView`. Jest on realizowany przy użyciu standardowego interfejsu, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używany do otwierania edytora podczas uruchamiania pakietu DSL. Jest on przywoływany w atrybucie `ProvideEditorFactory` w Package.cs

 `GeneratedVSCT.vsct`

 Lokalizuje standardowe polecenia menu w menu, takie jak menu kontekstowe diagramu, menu **Edycja** i tak dalej. Kod dla poleceń znajduje się w CommandSet.cs. Można zmienić lub zmodyfikować standardowe polecenia oraz dodać własne polecenia. Aby uzyskać więcej informacji, zobacz [pisanie poleceń i akcji użytkownika](../modeling/writing-user-commands-and-actions.md).

 `ModelExplorer.cs`

 Definiuje Eksploratora modeli dla DSL. Jest to widok drzewa modelu, który użytkownik widzi obok diagramu.

 Na przykład można przesłonić `InsertTreeView()`, aby zmienić kolejność, w jakiej elementy pojawiają się w Eksploratorze modelu.

 Jeśli chcesz, aby zaznaczenie w Eksploratorze modelu było zsynchronizowane z wybranym diagramem, możesz użyć następującego kodu:

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

 Definiuje okno, w którym jest wyświetlany Eksplorator modeli. Obsługuje Wybieranie elementów w Eksploratorze.

 `Package.cs`

 Ten plik definiuje sposób integracji DSL z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Atrybuty klasy pakietu rejestrują DSL jako program obsługi dla plików, które mają rozszerzenie pliku, definiują jego Przybornik i definiują sposób otwierania nowego okna. Metoda Initialize () jest wywoływana jednokrotnie, gdy pierwszy DSL jest ładowany do wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 `Source.extension.vsixmanifest`

 Aby dostosować ten plik, edytuj plik `.tt`.

> [!WARNING]
> Jeśli edytujesz plik TT w celu uwzględnienia zasobów, takich jak ikony lub obrazy, upewnij się, że zasób jest uwzględniony w kompilacji VSIX. W Eksplorator rozwiązań wybierz plik i upewnij się, że właściwość **include in VSIX** jest `True`.

 Ten plik kontroluje sposób pakowania DSL do rozszerzenia integracji z programem Visual Studio (VSIX). Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też
 [Jak definiować](../modeling/how-to-define-a-domain-specific-language.md) [modele, klasy i relacje](../modeling/understanding-models-classes-and-relationships.md) specyficzne dla domeny — [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md) [w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
