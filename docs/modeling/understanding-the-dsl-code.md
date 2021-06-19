---
title: Znajomość kodu DSL
description: Dowiedz się, jak rozwiązanie języka Domain-Specific (DSL) generuje interfejs API, który umożliwia odczytywanie i aktualizowanie wystąpień DSL w języku Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84f75298bc2854172eb7ec63bd6412e5703cfad7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388584"
---
# <a name="understanding-the-dsl-code"></a>Znajomość kodu DSL

Rozwiązanie Domain-Specific Language (DSL) generuje interfejs API, który umożliwia odczytywanie i aktualizowanie wystąpień DSL w języku Visual Studio. Ten interfejs API jest zdefiniowany w kodzie, który jest generowany na podstawie definicji DSL. W tym temacie opisano wygenerowany interfejs API.

## <a name="the-example-solution-component-diagrams"></a>Przykładowe rozwiązanie: Diagramy składników

Aby utworzyć rozwiązanie, które jest źródłem większości przykładów w tym temacie, utwórz DSL na podstawie szablonu **rozwiązania Modele** składników. Jest to jeden ze standardowych szablonów, który pojawia się podczas tworzenia nowego rozwiązania DSL.

> [!NOTE]
> Szablon DSL diagramów składników jest **nazywany** projektant języka specyficznego dla domeny .

Naciśnij **klawisz F5** i poeksperymentuj, jeśli nie znasz tego szablonu rozwiązania. W szczególności należy zauważyć, że porty tworzy się przez przeciągnięcie narzędzia portów do składnika i że można połączyć porty.

![Składniki i połączone porty](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>Struktura rozwiązania DSL
 Projekt **Dsl** definiuje interfejs API dla DSL. Projekt **DslPackage** definiuje sposób integracji z Visual Studio. Możesz również dodać własne projekty, które mogą również zawierać kod wygenerowany na podstawie modelu.

### <a name="the-code-directories"></a>Katalogi kodu
 Większość kodu w każdym z tych projektów jest generowana z **dsl\DslDefinition.dsl**. Wygenerowany kod znajduje się w **folderze Wygenerowany** kod. Aby wyświetlić wygenerowany plik, kliknij **pozycję [+]** obok wygenerowanego **pliku tt.**

 Zalecamy sprawdzenie wygenerowanego kodu, aby ułatwić zrozumienie dsl. Aby wyświetlić wygenerowane pliki, rozwiń pliki *.tt w Eksplorator rozwiązań.

 Pliki \* tt zawierają bardzo mało kodu generującego. Zamiast tego używają dyrektyw `<#include>` do dołączania udostępnionych plików szablonów. Pliki udostępnione można znaleźć w **folderze \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\projektant DSL\11.0\TextTemplates**

 Po dodaniu własnego kodu programu do rozwiązania DSL dodaj go w osobnym pliku poza folderem Wygenerowany kod. Możesz utworzyć folder **Kod niestandardowy.** (Podczas dodawania nowego pliku kodu do folderu niestandardowego pamiętaj, aby poprawić przestrzeń nazw w początkowym szkieletie kodu).

 Zdecydowanie zalecamy, aby nie edytować wygenerowanego kodu bezpośrednio, ponieważ zmiany zostaną utracone podczas ponownego kompilowania rozwiązania. Zamiast tego, aby dostosować DSL:

- Dostosuj wiele parametrów w definicji DSL.

- Napisz klasy częściowe w oddzielnych plikach kodu, aby przesłonić metody zdefiniowane w wygenerowanych klasach lub dziedziczone przez nie. W niektórych przypadkach należy ustawić generuje podwójne pochodne opcji klasy w definicji DSL, aby można było **przesłonić** wygenerowaną metodę.

- Ustaw opcje w definicji DSL, które powodują, że wygenerowany kod zapewnia "zaczepienia" dla własnego kodu.

     Jeśli na przykład ustawisz opcję **Ma** konstruktor niestandardowy klasy domeny, a następnie skompilowasz rozwiązanie, zobaczysz komunikaty o błędach. Po dwukrotnym kliknięciu jednego z tych komunikatów o błędach zobaczysz komentarze w wygenerowanym kodzie, które wyjaśniają, co powinien dostarczyć kod niestandardowy.

- Pisanie własnych szablonów tekstowych w celu wygenerowania kodu specyficznego dla aplikacji. Plików dołączanych można używać do udostępniania części szablonów, które są wspólne dla wielu projektów, i można tworzyć szablony projektów programu Visual Studio w celu skonfigurowania projektów, które są zainicjowane przy użyciu własnej struktury plików.

## <a name="generated-files-in-dsl"></a>Wygenerowane pliki w DSL
 W projekcie Dsl są wyświetlane następujące **wygenerowane** pliki.

 *TwojeDla*`Schema.xsd`

 Schemat plików, który zawiera wystąpienia DSL. Ten plik jest kopiowany do katalogu kompilacji **(bin).** Podczas instalowania DSL, można skopiować ten plik do **\Program Files\Microsoft Visual Studio 11.0\Xml\Schemas,** dzięki czemu pliki modelu można zweryfikować. Aby uzyskać więcej informacji, zobacz [Wdrażanie Domain-Specific Language Solutions.](msi-and-vsix-deployment-of-a-dsl.md)

 Jeśli dostosujemy serializację przez ustawienie opcji w Eksploratorze DSL, schemat odpowiednio się zmieni. Jeśli jednak napiszesz własny kod serializacji, ten plik może już nie reprezentować rzeczywistego schematu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Konstruktor połączeń to klasa, która tworzy relacje. Jest to kod narzędzia połączenia. Ten plik zawiera parę klas dla każdego narzędzia połączenia. Ich nazwy pochodzą od nazw relacji domeny i narzędzia połączenia: *Relationship* Builder i *ConnectorTool* ConnectAction.

 (W przykładzie rozwiązania składnika jeden z konstruktorów połączeń nosi nazwę ConnectionBuilder, jest to przypadek, ponieważ relacja domeny nosi nazwę Połączenie).

 Relacja jest tworzona w *metodzie Relationship.* `Builder.Connect()` Wersja domyślna sprawdza, czy elementy modelu źródłowego i docelowego są akceptowalne, a następnie iniekuje relację. Na przykład:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Każda klasa konstruktora jest generowana na podstawie węzła w sekcji **Konstruktory połączeń** w Eksploratorze DSL. Jedna `Connect` metoda może tworzyć relacje między co najmniej jedną parą klas domeny. Każda para jest definiowana przez dyrektywę Link Connect, którą można znaleźć w Eksploratorze DSL w węźle konstruktora.

 Można na przykład dodać do jednego konstruktora połączeń dyrektywy Link Connect dla każdego z trzech typów relacji w przykładowym DSL. Zapewni to użytkownikowi jedno narzędzie połączenia. Typ wystąpienia relacji będzie zależeć od typów elementów źródłowych i docelowych wybranych przez użytkownika.  Aby dodać dyrektywy Link Connect, kliknij prawym przyciskiem myszy konstruktora w Eksploratorze DSL.

 Aby napisać kod niestandardowy uruchamiany po utworzeniu określonego typu relacji domeny, wybierz odpowiednią dyrektywę Link Connect w węźle konstruktora. W niestandardowych okno Właściwości wartość **używa połączenia niestandardowego**. Ponownie skompilować rozwiązanie, a następnie podać kod w celu poprawienia wynikowych błędów.

 Aby napisać kod niestandardowy uruchamiany za każdym razem, gdy użytkownik używa tego narzędzia połączenia, ustaw właściwość **Jest niestandardową** konstruktora połączeń. Możesz podać kod, który decyduje o tym, czy element źródłowy jest dozwolony, czy dozwolona jest konkowana kombinacja źródła i obiektu docelowego oraz jakie aktualizacje powinny być dokonywane w modelu po nawiązaniu połączenia. Na przykład można zezwolić na połączenie tylko wtedy, gdy nie utworzy pętli na diagramie. Zamiast pojedynczego połączenia relacji można utworzyć bardziej złożony wzorzec kilku elementów powiązanych między źródłem i obiektem docelowym.

 `Connectors.cs`

 Zawiera klasy dla łączników, które są elementami diagramu, które zwykle reprezentują relacje odwołania. Każda klasa jest generowana na podstawie jednego łącznika w definicji DSL. Każda klasa łącznika pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Aby sprawić, że kolor i inne funkcje stylu będą zmienne w czasie działania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż **polecenie Dodaj ujawnione**.

 Aby wprowadzić dodatkowe funkcje stylu do zmiennej w czasie uruchamiania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement> .

 `Diagram.cs`

 Zawiera klasę, która definiuje diagram. Pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> .

 Aby sprawić, że kolor i inne funkcje stylu będą zmienne w czasie działania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż **polecenie Dodaj ujawnione**.

 Ponadto ten plik zawiera regułę, która odpowiada po dodaniu nowego `FixupDiagram` elementu do modelu. Reguła dodaje nowy kształt i łączy kształt z elementem modelu.

 `DirectiveProcessor.cs`

 Ten procesor dyrektywy ułatwia użytkownikom pisanie szablonów tekstowych, które odczytuje wystąpienie DSL. Procesor dyrektywy ładuje zestawy (biblioteki DLL) dla DSL i skutecznie wstawia `using` instrukcje dla przestrzeni nazw. Dzięki temu kod w szablonach tekstowych może używać klas i relacji zdefiniowanych w DSL.

 Aby uzyskać więcej informacji, zobacz Generowanie kodu z języka [Domain-Specific i](../modeling/generating-code-from-a-domain-specific-language.md) Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych [T4.](../modeling/creating-custom-t4-text-template-directive-processors.md)

 `DomainClasses.cs`

 Implementacje zdefiniowanych klas domeny, w tym klas abstrakcyjnych i klasy głównej modelu. Pochodzą one od klasy <xref:Microsoft.VisualStudio.Modeling.ModelElement> .

 Każda klasa domeny zawiera:

- Definicja właściwości i zagnieżdżona klasa procedury obsługi dla każdej właściwości domeny. Można zastąpić metody OnValueChanging() i OnValueChanged(). Aby uzyskać więcej informacji, zobacz Procedury obsługi zmian wartości [właściwości domeny](../modeling/domain-property-value-change-handlers.md).

   W przykładzie DSL klasa `Comment` zawiera właściwość i `Text` klasę procedury obsługi `TextPropertyHandler` .

- Właściwości klasy dostępu dla relacji, w których uczestniczy ta klasa domeny. (Nie ma klasy zagnieżdżonych dla właściwości roli).

   W przykładzie DSL klasa ma dostęp do swojego modelu nadrzędnego za `Comment` pośrednictwem relacji osadzania `ComponentModelHasComments` .

- Konstruktorów. Jeśli chcesz je przesłonić, ustaw dla klasy domeny wartość **Ma** konstruktor niestandardowy.

- Metody obsługi prototypu grupy elementów (EGP). Są one niezbędne, jeśli użytkownik może *scalić* (dodać) inny element do wystąpień tej klasy. Zazwyczaj użytkownik robi to, przeciągając z narzędzia elementu lub innego kształtu albo wklejając.

   W przykładzie DSL port wejściowy lub port wyjściowy można scalić ze składnikiem. Ponadto składniki i komentarze można scalać z modelem. Dla zasobu

   Metody obsługi EGP w klasie Component umożliwiają składnikowi akceptowanie portów, ale nie komentarzy. Procedura obsługi EGP w klasie modelu głównego akceptuje komentarze i składniki, ale nie porty.

  `DomainModel.cs`

  Klasa reprezentująca model domeny. Pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.DomainModel> .

> [!NOTE]
> To nie jest to samo, co klasa główna modelu.

 Zamknięcia kopiowania i usuwania definiują, jakie inne elementy powinny zostać dołączone po skopiowaniu lub usunięciu elementu. To zachowanie można kontrolować, ustawiając  właściwości **Propagacja** kopiowania i propagacji usuwania ról po każdej stronie każdej relacji. Jeśli chcesz, aby wartości są określane dynamicznie, możesz napisać kod zastępujący metody klas Zamknięcia.

 `DomainModelResx.resx`

 Zawiera on ciągi, takie jak opisy klas i właściwości domeny, nazwy właściwości, etykiety przybornika, standardowe komunikaty o błędach i inne ciągi, które mogą być wyświetlane użytkownikowi. Zawiera również ikony narzędzi i obrazy kształtów obrazów.

 Ten plik jest powiązany z wbudowanym zestawem i zawiera wartości domyślne tych zasobów. Język DSL można zlokalizowane przez utworzenie zestawu satelicka, który zawiera zlokalizowanej wersji zasobów. Ta wersja będzie używana, gdy DSL jest zainstalowany w kulturze zgodnej z zlokalizowanymi zasobami. Aby uzyskać więcej informacji, zobacz [Wdrażanie Domain-Specific Language Solutions.](msi-and-vsix-deployment-of-a-dsl.md)

 `DomainRelationships.cs`

 Każde połączenie między dwoma elementami w modelu jest reprezentowane przez wystąpienie klasy relacji domeny. Wszystkie klasy relacji pochodzą od <xref:Microsoft.VisualStudio.Modeling.ElementLink> klasy , która z kolei pochodzi od klasy <xref:Microsoft.VisualStudio.Modeling.ModelElement> . Ponieważ jest to element ModelElement, wystąpienie relacji może mieć właściwości i może być źródłem lub obiektem docelowym relacji.

 `HelpKeywordHelper.cs`

 Udostępnia funkcje, które są używane, gdy użytkownik naciśnie klawisz F1.

 `MultiplicityValidation.cs`

 W rolach relacji, w których określasz liczebność 1..1 lub 1..*, użytkownik powinien zostać ostrzec, że wymagane jest co najmniej jedno wystąpienie relacji. Ten plik zawiera ograniczenia weryfikacji, które implementują te ostrzeżenia. Link 1..1 do osadzonego elementu nadrzędnego nie jest weryfikowany.

 Aby te ograniczenia zostały wykonane, należy ustawić jedną z opcji **Uses...** w węźle **Edytor\Walidacja** w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [Validation in a Domain-Specific Language (Walidacja w Domain-Specific języku](../modeling/validation-in-a-domain-specific-language.md)).

 `PropertiesGrid.cs`

 Ten plik zawiera kod tylko wtedy, gdy do właściwości domeny został dołączony deskryptor typu niestandardowego. Aby uzyskać więcej informacji, zobacz [Dostosowywanie okna właściwości](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Metoda walidacji, aby upewnić się, że ta sama monikera nie odwołuje się do żadnych dwóch elementów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).

- SerializationHelper, klasa, która zapewnia funkcje, które są używane przez klasy serializacji wspólne.

  `Serializer.cs`

  Klasa serializatora dla każdej klasy domeny, relacji, kształtu, łącznika, diagramu i modelu.

  Wiele funkcji tych klas można kontrolować za pomocą ustawień w Eksploratorze DSL w obszarze **Zachowanie serializacji XML**.

  `Shapes.cs`

  Klasa dla każdej klasy kształtu w definicji DSL. Kształty pochodzą od <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> . Aby uzyskać więcej informacji, zobacz [Dostosowywanie File Storage i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).

  Aby zastąpić wygenerowane metody własnymi metodami w klasie częściowej, ustaw wartość **Generates Double Derived dla** łącznika w definicji DSL. Aby zastąpić konstruktor własnym kodem, ustaw wartość **Ma konstruktor niestandardowy**.

  Aby sprawić, że kolor i inne funkcje stylu będą zmienne w czasie działania, kliknij prawym przyciskiem myszy klasę na diagramie definicji DSL i wskaż **polecenie Dodaj ujawnione**.

  Aby wprowadzić zmienne dodatkowe funkcje stylu w czasie uruchamiania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Konfiguruje przybornik, instalując prototypy grup elementów w narzędziach elementów. Kopie tych prototypów są scalane z elementami docelowymi, gdy użytkownik uruchamia narzędzie.

  Można `CreateElementPrototype()` przesłonić element przybornika tworzący grupę kilku obiektów. Można na przykład zdefiniować element reprezentujący obiekty, które mają składniki podrzędne. Po zmianie kodu zresetuj eksperymentalne wystąpienie Visual Studio, aby wyczyścić pamięć podręczną przybornika.

## <a name="generated-files-in-the-dslpackage-project"></a>Wygenerowane pliki w projekcie DslPackage
 Pakiet DslPackage paruje model DSL z Visual Studio, zarządzając oknami, przybornikami i poleceniami menu. Większość klas jest podwójnie pochodnymi, dzięki czemu można zastąpić dowolną z ich metod.

 `CommandSet.cs`

 Polecenia menu dostępne po kliknięciu prawym przyciskiem myszy, które są widoczne na diagramie. Możesz dostosować lub dodać do tego zestawu. Ten plik zawiera kod poleceń . Lokalizacja poleceń w menu jest określana przez plik Commands.vsct. Aby uzyskać więcej informacji, zobacz [Writing User Commands and Actions (Pisanie poleceń i akcji użytkownika).](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

 `Constants.cs`

 Identyfikatory guid.

 `DocData.cs`

 *TwojeDla* `DocData` zarządza ładowaniem i zapisywaniem modelu w pliku oraz tworzy wystąpienie magazynu.

 Jeśli na przykład chcesz zapisać DSL w bazie danych zamiast pliku, możesz przesłonić metody `Load` `Save` i .

 `DocView.cs`

 *TwojeDla* `DocView` zarządza oknem, w którym jest wyświetlany diagram. Można na przykład osadzić diagram w formularzu systemu Windows:

 Dodaj plik kontroli użytkownika do projektu DslPackage. Dodaj panel, w którym można wyświetlić diagram. Dodaj przyciski i inne kontrolki. W widoku kodu formularza dodaj następujący kod, dostosowując nazwy do dsl:

```csharp
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

 Iniektuje `DocData` wystąpienia i `DocView` . Spełnia standardowego interfejsu, który Visual Studio do otwierania edytora podczas uruchamiania pakietu DSL. Jest on przywołyny w `ProvideEditorFactory` atrybutze w pliku Package.cs

 `GeneratedVSCT.vsct`

 Lokalizuje standardowe polecenia menu w menu, takie jak menu kontekstowe diagramu, **menu** Edycja i tak dalej. Kod poleceń znajduje się w commandset.cs. Standardowe polecenia można przenosić lub modyfikować, a także dodawać własne polecenia. Aby uzyskać więcej informacji, zobacz [Writing User Commands and Actions (Pisanie poleceń i akcji użytkownika).](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

 `ModelExplorer.cs`

 Definiuje Eksploratora modeli dla DSL. Jest to widok drzewa modelu, który użytkownik widzi obok diagramu.

 Można na przykład przesłonić element , aby zmienić kolejność, w jakiej `InsertTreeView()` elementy są wyświetlane w Eksploratorze modeli.

 Jeśli chcesz, aby wybór w Eksploratorze modeli był zsynchronizowany z wyborem diagramu, możesz użyć następującego kodu:

```csharp
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

 Definiuje okno, w którym jest wyświetlany Eksplorator modelu. Obsługuje wybór elementów w eksploratorze.

 `Package.cs`

 Ten plik definiuje sposób integracji DSL z Visual Studio. Atrybuty klasy pakietu rejestruje DSL jako program obsługi dla plików, które mają rozszerzenie pliku, zdefiniuj jego przybornik i zdefiniuj sposób otwierania nowego okna. Metoda Initialize() jest wywoływana jeden raz, gdy pierwszy DSL jest ładowany do Visual Studio wystąpienia.

 `Source.extension.vsixmanifest`

 Aby dostosować ten plik, edytuj `.tt` plik.

> [!WARNING]
> Jeśli edytujesz plik tt w celu dołączyć zasoby, takie jak ikony lub obrazy, upewnij się, że zasób jest uwzględniony w kompilacji VSIX. W Eksplorator rozwiązań wybierz plik i upewnij się, że właściwość Include in VSIX (Uwzględnij w **VSIX)** ma wartość `True` .

 Ten plik kontroluje sposób, w jaki DSL jest pakowany do Visual Studio Integration Extension (VSIX). Aby uzyskać więcej informacji, zobacz [Wdrażanie Domain-Specific Language Solutions.](msi-and-vsix-deployment-of-a-dsl.md)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Pisanie kodu w celu dostosowania Domain-Specific językowego](../modeling/writing-code-to-customise-a-domain-specific-language.md)
