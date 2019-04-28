---
title: Rozszerzanie DSL za pomocą MEF
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b62719fb00910e4eef183f960e1a1d4ea9a4a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994532"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozszerzanie DSL za pomocą MEF

Usługi języka specyficznego dla domeny (DSL) można rozszerzyć za pomocą Managed Extensibility Framework (MEF). Użytkownik i inni deweloperzy będą mogli pisanie rozszerzeń dla języka DSL bez wprowadzania zmian w definicji DSL, a kodu programu. Takie rozszerzenia obejmują polecenia menu, obsługi przeciągania i upuszczania oraz sprawdzania poprawności. Użytkownicy będą mogli zainstalować DSL, a następnie opcjonalnie zainstalować rozszerzenia dla niego.

Ponadto po włączeniu MEF w DSL może być łatwiejsze do pisania, niektóre funkcje DSL, nawet jeśli zostały one wszystkie utworzone wraz z język DSL.

Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Aby włączyć DSL być rozszerzony za MEF

1. Utwórz nowy folder o nazwie **MefExtension** wewnątrz **DslPackage** projektu. Dodaj następujące pliki do niego:

     Nazwa pliku: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Ustaw identyfikator GUID w tym pliku, aby być taka sama jak CommandSetId identyfikator GUID, który jest zdefiniowany w DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Nazwa pliku: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Nazwa pliku: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Nazwa pliku: `ValidationExtensionRegistrar.tt`

    Jeśli dodasz ten plik, należy włączyć sprawdzania poprawności w DSL za pomocą co najmniej jeden z przełączników w **EditorValidation** w Eksplorator DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nazwa pliku: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Utwórz nowy folder o nazwie **MefExtension** wewnątrz **Dsl** projektu. Dodaj następujące pliki do niego:

     Nazwa pliku: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Nazwa pliku: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Nazwa pliku: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Dodaj następujący wiersz do istniejącego pliku, który nosi nazwę **DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Wstaw wiersz po istniejącej `<Include>` dyrektywy.

4. Otwórz *DslDefinition.dsl*.

5. Eksplorator modelu DSL wybierz **Editor\Validation**.

6. W oknie dialogowym właściwości upewnij się, że co najmniej jedna z właściwości o nazwie **używa** jest `true`.

7. W **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Przekształć wszystkie szablony**.

     Pliki pomocnicze są wyświetlane poniżej każdego z plików, które zostały dodane.

8. Skompiluj i uruchom rozwiązanie, aby sprawdzić, że nadal działa.

DSL jest teraz włączone MEF. Polecenia menu, procedury obsługi gestów i ograniczeń sprawdzania poprawności można napisać jako rozszerzenia MEF. Można napisać te rozszerzenia w rozwiązaniu DSL wraz z innymi kod niestandardowy. Ponadto możesz lub innym deweloperom napisać oddzielne rozszerzeń programu Visual Studio DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Tworzenie rozszerzenia dla języka DSL włączone MEF

Jeśli masz dostęp do utworzonych przez siebie lub kogoś innego DSL włączone MEF, można napisać rozszerzeń dla niego. Rozszerzenia może służyć do dodawania polecenia menu, procedury obsługi gestów lub ograniczenia sprawdzania poprawności. Aby tworzyć te rozszerzenia, należy użyć rozwiązania programu Visual Studio rozszerzenia (VSIX). To rozwiązanie składa się z dwóch części: projekt biblioteki klas, który tworzy zestaw kodu i projektu VSIX, które pakiety zestawu.

### <a name="to-create-a-dsl-extension-vsix"></a>Aby utworzyć rozszerzenie VSIX języka DSL

1. Utwórz nową **biblioteki klas** projektu.

2. W nowym projekcie Dodaj odwołanie do zestawu język DSL.

   - Ten zestaw jest zwykle ma nazwę, która kończy się ". DSL.dll".

   - Jeśli masz dostęp do projektu DSL, można znaleźć pliku zestawu w katalogu **Dsl\bin\\\\***

   - Jeśli masz dostęp do pliku VSIX języka DSL, można znaleźć zestawu, zmieniając rozszerzenie nazwy pliku w pliku VSIX ".zip". Zdekompresuj plik zip.

3. Dodaj odwołania do następujących zestawów .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Utwórz nową **projekt VSIX** projektu.

5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt VSIX lub wybrać **Ustaw jako projekt startowy**.

6. Otwórz w nowym projekcie **source.extension.vsixmanifest**.

7. Kliknij przycisk **Dodaj zawartość**. W oknie dialogowym Ustaw **typu zawartości** do **składnik MEF**, i **projekt źródłowy** do projektu biblioteki klas.

8. Dodaj odwołanie VSIX do język DSL.

   1. W **source.extension.vsixmanifest**, kliknij przycisk **Dodaj odwołanie**

   2. W oknie dialogowym kliknij **Dodaj ładunku** i odszukaj plik VSIX języka DSL. Plik VSIX jest wbudowana w rozwiązanie DSL w ** DslPackage\bin\\\\***.

       Pozwala to użytkownikom zainstalować język DSL i rozszerzenia, w tym samym czasie. Jeśli użytkownik ma już zainstalowany język DSL, zostanie zainstalowana tylko rozszerzenia.

9. Przejrzyj i zaktualizuj innych polach **source.extension.vsixmanifest**. Kliknij przycisk **Wybierz wersje** i sprawdź, czy są ustawione prawidłowe wersje programu Visual Studio.

10. Dodaj kod do projektu biblioteki klas. Przykładowych w następnej sekcji można używać jako wskazówki.

     Możesz dodać dowolną liczbę polecenia, gestu i sprawdzania poprawności klas.

11. Aby przetestować rozszerzenie, naciśnij klawisz **F5**. W doświadczalnym wystąpieniu programu Visual Studio należy utworzyć lub otworzyć przykładowy plik język DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Pisanie rozszerzenia MEF dla języków DSL

Można napisać rozszerzeń w projekcie kodu zestawu, z oddzielnym rozwiązaniu rozszerzenia DSL. Umożliwia także MEF w projekcie DslPackage to wygodny sposób do zapisania jako część DSL poleceń, gestów i kod sprawdzania poprawności.

### <a name="menu-commands"></a>Polecenia menu

Aby zapisać polecenia menu, zdefiniuj klasę, która implementuje <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> i prefiksu klasa z atrybutem, który jest zdefiniowany w DSL, o nazwie *YourDsl*`CommandExtension`. Można napisać więcej niż jednej klasy polecenia menu.

`QueryStatus()` jest wywoływana zawsze wtedy, gdy użytkownik kliknie prawym przyciskiem myszy diagram. Należy sprawdzić bieżące zaznaczenie i ustaw `command.Enabled` aby wskazać, kiedy polecenie ma zastosowanie.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Programy obsługi gestu

Procedury obsługi gestu poradzenie sobie z obiektami, które zostało przeciągnięte na diagramie z dowolnym miejscu, wewnątrz lub na zewnątrz programu Visual Studio. Poniższy przykład pozwala użytkownikowi na przeciągnij pliki z Eksploratora Windows na diagramie. Tworzy elementy, które zawierają nazwy plików.

Można napisać procedury obsługi, aby poradzić sobie z drags z innymi modelami DSL i modeli UML. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Ograniczenia sprawdzania poprawności

Metody sprawdzania poprawności są oznaczone przez `ValidationExtension` atrybut, który jest generowany przez język DSL, a także przez <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Metoda może występować w dowolnej klasy, która nie jest oznaczona przez atrybut.

Aby uzyskać więcej informacji, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Zobacz także

- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)
