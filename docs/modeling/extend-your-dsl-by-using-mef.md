---
title: Rozszerzanie DSL za pomocą MEF
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04d14b3b17953ef30620d9f616bb471b186e9c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547644"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozszerzanie DSL za pomocą MEF

Język specyficzny dla domeny można rozłożyć przy użyciu Managed Extensibility Framework (MEF). Ty lub inni deweloperzy będą mogli pisać rozszerzenia dla DSL bez zmiany definicji DSL i kodu programu. Takie rozszerzenia obejmują polecenia menu, programy obsługi przeciągania i upuszczania oraz sprawdzanie poprawności. Użytkownicy będą mogli instalować Twoje DSL, a następnie opcjonalnie instalować rozszerzenia.

Ponadto po włączeniu usługi MEF w języku DSL można łatwiej pisać niektóre funkcje Twojego języka DSL, nawet jeśli są one połączone z DSL.

Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Aby umożliwić Rozszerzanie DSL przez MEF

1. Utwórz nowy folder o nazwie **MefExtension** w projekcie **DslPackage** . Dodaj do niego następujące pliki:

     Nazwa pliku: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Ustaw identyfikator GUID w tym pliku na taki sam jak identyfikator GUID CommandSetId zdefiniowany w DslPackage\GeneratedCode\Constants.tt

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

    W przypadku dodania tego pliku należy włączyć walidację w DSL przy użyciu co najmniej jednego z przełączników w **EditorValidation** w Eksploratorze DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nazwa pliku: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Utwórz nowy folder o nazwie **MefExtension** w projekcie **DSL** . Dodaj do niego następujące pliki:

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

3. Dodaj następujący wiersz do istniejącego pliku o nazwie **DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Wstaw wiersz po istniejącej `<Include>` dyrektywie.

4. Otwórz *DslDefinition. DSL*.

5. W Eksploratorze DSL wybierz pozycję **Editor\Validation**.

6. Upewnij się, że w okno Właściwości należy **użyć** co najmniej jednej z właściwości o nazwie `true` .

7. Na pasku narzędzi **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony**.

     Pliki zależne są wyświetlane pod każdym z plików, które zostały dodane.

8. Kompiluj i uruchamiaj rozwiązanie, aby upewnić się, że nadal działa.

Funkcja DSL jest teraz MEF. Można pisać polecenia menu, programy obsługi gestów i ograniczenia sprawdzania poprawności jako rozszerzenia MEF. Te rozszerzenia można napisać w rozwiązaniu DSL wraz z innym kodem niestandardowym. Ponadto ty lub inni deweloperzy mogą pisać oddzielne rozszerzenia programu Visual Studio, które rozszerzają swój DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Tworzenie rozszerzenia dla DSL z włączoną obsługą MEF

Jeśli masz dostęp do MEF DSL utworzonego przez siebie lub inną osobę, możesz napisać dla niego rozszerzenia. Rozszerzenia mogą służyć do dodawania poleceń menu, programów obsługi gestów lub ograniczeń walidacji. Do tworzenia tych rozszerzeń służy rozwiązanie Visual Studio Extension (VSIX). Rozwiązanie ma dwie części: projekt biblioteki klas, który kompiluje zestaw kodu, oraz projekt VSIX, który jest pakietem zestawu.

### <a name="to-create-a-dsl-extension-vsix"></a>Aby utworzyć VSIX rozszerzenia DSL

1. Utwórz nowy projekt **biblioteki klas** .

2. W nowym projekcie Dodaj odwołanie do zestawu DSL.

   - Ten zestaw ma zwykle nazwę kończącą się ciągiem ".Dsl.dll".

   - Jeśli masz dostęp do projektu DSL, możesz znaleźć plik zestawu w ** \\ \\ \* koszu katalogu DSL**

   - Jeśli masz dostęp do pliku VSIX DSL, możesz znaleźć zestaw, zmieniając rozszerzenie nazwy pliku VSIX na ". zip". Dekompresowanie pliku zip.

3. Dodaj odwołania do następujących zestawów .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Utwórz nowy projekt **projektu VSIX** .

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt VSIX i wybierz polecenie **Ustaw jako projekt startowy**.

6. W nowym projekcie Otwórz **Źródło. Extension. vsixmanifest**.

7. Kliknij pozycję **Dodaj zawartość**. W oknie dialogowym Ustaw **Typ zawartości** na **składnik MEF**i **projekt źródłowy** do projektu biblioteki klas.

8. Dodaj odwołanie VSIX do DSL.

   1. W polu **source. Extension. vsixmanifest**kliknij pozycję **Dodaj odwołanie** .

   2. W oknie dialogowym kliknij pozycję **Dodaj ładunek** , a następnie Znajdź plik VSIX DSL. Plik VSIX jest skompilowany w rozwiązaniu DSL w **DslPackage \\ bin \\ \* **.

       Dzięki temu użytkownicy mogą instalować jednocześnie DSL i Twoje rozszerzenie. Jeśli użytkownik zainstalował już modem DSL, zostanie zainstalowane tylko rozszerzenie.

9. Przejrzyj i zaktualizuj pozostałe pola **source. Extension. vsixmanifest**. Kliknij pozycję **Wybierz wersje** i sprawdź, czy są ustawione poprawne wersje programu Visual Studio.

10. Dodaj kod do projektu biblioteki klas. Skorzystaj z przykładów w następnej sekcji jako przewodnika.

     Można dodać dowolną liczbę klas poleceń, gestów i walidacji.

11. Aby przetestować rozszerzenie, naciśnij klawisz **F5**. W eksperymentalnym wystąpieniu programu Visual Studio Utwórz lub Otwórz przykładowy plik DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Pisanie rozszerzeń MEF dla językami DSL

Można pisać rozszerzenia w projekcie kodu zestawu oddzielnego rozwiązania do rozszerzenia DSL. Możesz również użyć MEF w projekcie DslPackage, jako wygodny sposób pisania poleceń, gestów i kodu sprawdzania poprawności jako części DSL.

### <a name="menu-commands"></a>Polecenia menu

Aby napisać polecenie menu, zdefiniuj klasę implementującą <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> i prefiks klasy z atrybutem, który jest zdefiniowany w DSL o nazwie *YourDsl* `CommandExtension` . Można napisać więcej niż jedną klasę poleceń menu.

`QueryStatus()` jest wywoływana za każdym razem, gdy użytkownik kliknie prawym przyciskiem myszy diagram. Powinien on sprawdzić bieżące zaznaczenie i ustawić, `command.Enabled` Aby wskazać, kiedy polecenie ma zastosowanie.

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

Procedura obsługi gestu może obsłużyć obiekty przeciągane na diagram z dowolnego miejsca, wewnątrz lub na zewnątrz programu Visual Studio. Poniższy przykład umożliwia użytkownikowi przeciąganie plików z Eksploratora Windows na diagram. Tworzy elementy, które zawierają nazwy plików.

Procedury obsługi można pisać, aby przeciągać z innych modeli DSL i modeli UML. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

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

### <a name="validation-constraints"></a>Ograniczenia walidacji

Metody walidacji są oznaczane przez `ValidationExtension` atrybut generowany przez DSL, a także przez <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Metoda może pojawić się w dowolnej klasie, która nie jest oznaczona przez atrybut.

Aby uzyskać więcej informacji, zobacz [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md).

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

## <a name="see-also"></a>Zobacz też

- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Sprawdzanie poprawności w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)
