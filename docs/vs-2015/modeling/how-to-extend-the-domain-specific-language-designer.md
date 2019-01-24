---
title: 'Instrukcje: Rozszerzanie projektanta języka specyficznego dla domeny | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 645346098b954fb57f5bb09f5ee97cfa48302150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766160"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Instrukcje: Rozszerzanie projektanta języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wykonać rozszerzenia do projektanta, którego używasz do edytowania definicji DSL. Typy rozszerzenia, które można wprowadzać należą: dodanie polecenia menu, dodanie obsługi przeciągnij i kliknij dwukrotnie gestów i reguł, które są wyzwalane, gdy zmienią się określone typy wartości lub relacje. Rozszerzenia można jako Visual Studio Integration rozszerzenie (VSIX) w pakiecie i dystrybuowane do innych użytkowników.  
  
 Przykładowy kod i więcej informacji na temat tej funkcji można znaleźć programu Visual Studio [wizualizacji i modelowania SDK (VMSDK) witryny sieci Web](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## <a name="setting-up-the-solution"></a>Konfigurowanie rozwiązania  
 Skonfiguruj projekt, który zawiera kod rozszerzenia, a projekt VSIX, które eksportuje projektu. Rozwiązanie może zawierać inne projekty, które są włączone w samym VSIX.  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>Aby utworzyć rozwiązanie rozszerzenia projektanta DSL  
  
1.  Tworzenie nowego projektu przy użyciu szablonu projektu biblioteki klas. W **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** a następnie w środkowym oknie kliknij pozycję **biblioteki klas**.  
  
     Projekt ten będzie zawierał kod rozszerzenia.  
  
2.  Tworzenie nowego projektu przy użyciu szablonu projektu VSIX. W **nowy projekt** okna dialogowego rozwiń **Visual C#**, kliknij przycisk **rozszerzalności**, a następnie w środkowym oknie Wybierz **projekt VSIX**.  
  
     Wybierz **Dodaj do rozwiązania**.  
  
     Source.Extension.vsixmanifest zostanie otwarty w edytorze manifestu VSIX.  
  
3.  Powyżej pola zawartość, kliknij przycisk **Dodaj zawartość**.  
  
4.  W **Dodaj zawartość** okno dialogowe, zestaw **wybierz typ zawartości** do **składnik MEF**i ustaw **projektu** do projektu biblioteki klas.  
  
5.  Kliknij przycisk **Wybierz wersje** i upewnij się, że **programu Visual Studio Enterprise** jest zaznaczone.  
  
6.  Upewnij się, że projekt VSIX jest projektem startowym rozwiązania.  
  
7.  W projekcie biblioteki klas Dodaj odwołania do następujących zestawów:  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## <a name="testing-and-deployment"></a>Testowanie i wdrażanie  
 Aby przetestować jakiegokolwiek rozszerzenia, w tym temacie, tworzenie i uruchamianie rozwiązania. Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarty. W tym wypadku otwórz rozwiązanie DSL. Edytowanie diagramu DslDefinition. Zachowania rozszerzeń będą widoczne.  
  
 Do wdrożenia rozszerzenia do głównego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]i na innych komputerach, wykonaj następujące czynności:  
  
1. Znajdź plik VSIX instalacji w projekcie VSIX bin\\*\*\\\*.vsix  
  
2. Skopiuj ten plik do komputera docelowego, a następnie w Eksploratorze Windows (lub Eksploratora plików), kliknij go dwukrotnie.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwiera Menedżera rozszerzenia, aby upewnić się, że rozszerzenie zostało zainstalowane.  
  
   Aby odinstalować rozszerzenie, wykonaj następujące kroki:  
  
3. w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.  
  
4. Zaznacz rozszerzenie, a następnie usuń go.  
  
## <a name="adding-a-shortcut-menu-command"></a>Dodawanie polecenia Menu skrótów  
 Aby polecenie menu skrótów, pojawiają się na powierzchni projektanta DSL lub w oknie Eksplorator DSL, napisz klasy podobne do następujących.  
  
 Klasa musi implementować `ICommandExtension` i muszą mieć atrybut `DslDefinitionModelCommandExtension`.  
  
```  
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
  
## <a name="handling-mouse-gestures"></a>Obsługa gesty myszy  
 Kod jest podobny do kodu polecenie menu.  
  
```  
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
  
## <a name="responding-to-value-changes"></a>Reagowanie na zmiany wartości  
 Ten program obsługi wymaga modelu domeny działała prawidłowo. Firma Microsoft zapewnia model domeny proste.  
  
```  
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
  
```  
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
