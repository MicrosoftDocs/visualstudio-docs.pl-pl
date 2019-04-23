---
title: 'Instrukcje: Rozszerzanie projektanta języka specyficznego dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85a4356837180d13428acf34636f28cca668a423
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063156"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Instrukcje: Rozszerzanie projektanta języka specyficznego dla domeny

Można wykonać rozszerzenia do projektanta, którego używasz do edytowania definicji DSL. Typy rozszerzenia, które można wprowadzać należą: dodanie polecenia menu, dodanie obsługi przeciągnij i kliknij dwukrotnie gestów i reguł, które są wyzwalane, gdy zmienią się określone typy wartości lub relacje. Rozszerzenia można jako Visual Studio Integration rozszerzenie (VSIX) w pakiecie i dystrybuowane do innych użytkowników.

Przykładowy kod i więcej informacji na temat tej funkcji można znaleźć programu Visual Studio [wizualizacji i modelowania SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Konfigurowanie rozwiązania

Skonfiguruj projekt, który zawiera kod rozszerzenia, a projekt VSIX, które eksportuje projektu. Rozwiązanie może zawierać inne projekty, które są włączone w samym VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Aby utworzyć rozwiązanie rozszerzenia projektanta DSL

1. Utwórz nowy projekt za pomocą **biblioteki klas** szablonu projektu. Projekt ten będzie zawierał kod rozszerzenia.

2. Utwórz nową **projekt VSIX** projektu.

     Wybierz **Dodaj do rozwiązania**.

     *Source.Extension.vsixmanifest* zostanie otwarty w edytorze manifestu VSIX.

3. Powyżej pola zawartość, kliknij przycisk **Dodaj zawartość**.

4. W **Dodaj zawartość** okno dialogowe, zestaw **wybierz typ zawartości** do **składnik MEF**i ustaw **projektu** do projektu biblioteki klas.

5. Kliknij przycisk **Wybierz wersje** i upewnij się, że **programu Visual Studio Enterprise** jest zaznaczone.

6. Upewnij się, że projekt VSIX jest projektem startowym rozwiązania.

7. W projekcie biblioteki klas Dodaj odwołania do następujących zestawów:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Testowanie i wdrażanie

Aby przetestować jakiegokolwiek rozszerzenia, w tym temacie, tworzenie i uruchamianie rozwiązania. Otwiera doświadczalne wystąpienie programu Visual Studio. W tym wypadku otwórz rozwiązanie DSL. Edytowanie diagramu DslDefinition. Zachowania rozszerzeń będą widoczne.

Aby wdrożyć rozszerzeń do głównego programu Visual Studio, a także na innych komputerach, wykonaj następujące kroki:

1. Znajdź plik VSIX instalacji w projekcie VSIX bin\\*\*\\\*.vsix

2. Skopiuj ten plik do komputera docelowego, a następnie w Eksploratorze Windows (lub Eksploratora plików), kliknij go dwukrotnie.

     Otwiera Menedżera rozszerzeń programu Visual Studio, aby upewnić się, że rozszerzenie zostało zainstalowane.

Aby odinstalować rozszerzenie, wykonaj następujące kroki:

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.

2. Zaznacz rozszerzenie, a następnie usuń go.

## <a name="add-a-shortcut-menu-command"></a>Dodaj polecenie Menu skrótów

Aby polecenie menu skrótów, pojawiają się na powierzchni projektanta DSL lub w oknie Eksplorator DSL, napisz klasy podobne do następujących.

Klasa musi implementować `ICommandExtension` i muszą mieć atrybut `DslDefinitionModelCommandExtension`.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Obsługa gesty myszy

Kod jest podobny do kodu polecenie menu.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Odpowiadanie na zmiany wartości

Ten program obsługi wymaga modelu domeny działała prawidłowo. Firma Microsoft zapewnia model domeny proste.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Poniższy kod implementuje prosty model. Utwórz nowy identyfikator GUID, Zastąp symbol zastępczy.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```