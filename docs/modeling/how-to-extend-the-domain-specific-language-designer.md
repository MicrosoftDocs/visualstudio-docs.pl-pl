---
title: 'Porady: rozszerzanie projektanta języka specyficznego dla domeny'
description: Dowiedz się, jak tworzyć rozszerzenia projektanta, które są używane do edytowania definicji języka specyficznego dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f56385a5ddcede66e886899ce03f213f1e665db6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881597"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Porady: rozszerzanie projektanta języka specyficznego dla domeny

Aby edytować definicje DSL, można tworzyć rozszerzenia projektanta. Typy rozszerzeń, które można wykonać, obejmują dodawanie poleceń menu, Dodawanie programów obsługi dla gestów przeciągania i podwójnego kliknięcia oraz reguły wyzwalane po zmianie określonych typów wartości lub relacji. Rozszerzenia mogą być spakowane jako rozszerzenie integracji programu Visual Studio (VSIX) i dystrybuowane do innych użytkowników.

Aby uzyskać przykładowy kod i więcej informacji na temat tej funkcji, zobacz Visual Studio [Wizualizacja i Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Skonfiguruj rozwiązanie

Skonfiguruj projekt zawierający kod rozszerzenia oraz projekt VSIX, który eksportuje projekt. Twoje rozwiązanie może zawierać inne projekty, które są włączone do tego samego VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Aby utworzyć rozwiązanie rozszerzenia projektant DSL

1. Utwórz nowy projekt przy użyciu szablonu projektu **biblioteki klas** . Ten projekt będzie zawierać kod rozszerzeń.

2. Utwórz nowy projekt **projektu VSIX** .

     Wybierz pozycję **Dodaj do rozwiązania**.

     Plik *source. Extension. vsixmanifest* zostanie otwarty w edytorze manifestu VSIX.

3. Powyżej pola zawartość kliknij przycisk **Dodaj zawartość**.

4. W oknie dialogowym **Dodawanie zawartości** Ustaw **opcję Wybierz typ zawartości** na **składnik MEF**, a następnie ustaw **projekt** na projekt biblioteki klas.

5. Kliknij pozycję **Wybierz wersje** i upewnij się, że **Visual Studio Enterprise** jest zaznaczone.

6. Upewnij się, że projekt VSIX jest projektem startowym rozwiązania.

7. W projekcie biblioteki klas Dodaj odwołania do następujących zestawów:

     Microsoft. VisualStudio. CoreUtility

     Microsoft. VisualStudio. Modeling. Sdk. 11.0

     Microsoft. VisualStudio. Modeling. Sdk. Diagrams. 11.0

     Microsoft. VisualStudio. Modeling. Sdk. DslDefinition. 11.0

     Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0

     System. ComponentModel. kompozycji

     System. Drawing

     System. Drawing. Design

     System. Windows. Forms

## <a name="test-and-deployment"></a>Testowanie i wdrażanie

Aby przetestować dowolne rozszerzenia w tym temacie, skompiluj i uruchom rozwiązanie. Zostanie otwarte doświadczalne wystąpienie programu Visual Studio. W tym przypadku należy otworzyć rozwiązanie DSL. Edytuj diagram DslDefinition. Można zobaczyć zachowanie rozszerzenia.

Aby wdrożyć rozszerzenia w głównym programie Visual Studio i innych komputerach, wykonaj następujące kroki:

1. Znajdź plik instalacji VSIX w projekcie VSIX w pliku bin \\ * \\ \* . vsix

2. Skopiuj ten plik na komputer docelowy, a następnie kliknij go dwukrotnie w Eksploratorze Windows (lub Eksploratorze plików).

     Zostanie otwarty Menedżer rozszerzeń programu Visual Studio, aby upewnić się, że rozszerzenie zostało zainstalowane.

Aby odinstalować rozszerzenie, wykonaj następujące kroki:

1. w programie Visual Studio w menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

2. Wybierz rozszerzenie i usuń je.

## <a name="add-a-shortcut-menu-command"></a>Dodaj polecenie menu skrótów

Aby polecenie menu skrótów było wyświetlane na powierzchni projektant DSL lub w oknie Eksplorator DSL, napisz klasę podobną do następującej.

Klasa musi implementować `ICommandExtension` i musi mieć atrybut `DslDefinitionModelCommandExtension` .

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

## <a name="handle-mouse-gestures"></a>Obsługa gestów myszy

Kod jest podobny do kodu polecenia menu.

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

## <a name="respond-to-value-changes"></a>Reagowanie na zmiany wartości

Ta procedura obsługi wymaga, aby model domeny działał poprawnie. Udostępniamy prosty model domeny.

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

Poniższy kod implementuje prosty model. Utwórz nowy identyfikator GUID, aby zastąpić symbol zastępczy.

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