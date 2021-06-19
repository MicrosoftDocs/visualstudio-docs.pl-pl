---
title: Rozszerzanie DSL za pomocą MEF
description: Dowiedz się, jak rozszerzyć język specyficzny dla domeny (DSL) przy użyciu Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388883"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozszerzanie DSL za pomocą MEF

Język specyficzny dla domeny (DSL) można rozszerzyć przy użyciu Managed Extensibility Framework (MEF). Ty lub inni deweloperzy będziecie mogli pisać rozszerzenia dla DSL bez zmiany definicji DSL i kodu programu. Rozszerzenia te obejmują polecenia menu, programy obsługi przeciągania i upuszczania oraz walidację. Użytkownicy będą mogli zainstalować dsl, a następnie opcjonalnie zainstalować dla niego rozszerzenia.

Ponadto po włączeniu MEF w DSL, może być łatwiejsze do napisania niektórych funkcji DSL, nawet jeśli są one wbudowane razem z DSL.

Aby uzyskać więcej informacji na temat mef, [zobacz Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Aby włączyć dsl ma być rozszerzony przez MEF

1. Utwórz nowy folder o **nazwie MefExtension** w **projekcie DslPackage.** Dodaj do niego następujące pliki:

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

    Jeśli dodasz ten plik, musisz włączyć weryfikację w DSL przy użyciu co najmniej jednego z przełączników w **EdytorzeValidation** w eksploratorze DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nazwa pliku: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Utwórz nowy folder o **nazwie MefExtension** wewnątrz **projektu Dsl.** Dodaj do niego następujące pliki:

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

3. Dodaj następujący wiersz do istniejącego pliku o nazwie **DslPackage\Commands.vsct:**

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Wstaw wiersz po istniejącej `<Include>` dyrektywie.

4. Otwórz *dslDefinition.dsl.*

5. W eksploratorze DSL wybierz pozycję **Editor\Validation.**

6. W okno Właściwości upewnij się, że co najmniej jedna z właściwości o nazwie **Uses ma** nazwę `true` .

7. Na pasku **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony.**

     Pliki podmiotu zależnego są wyświetlane pod każdym dodanym plikiem.

8. Skompilowanie i uruchomienie rozwiązania w celu sprawdzenia, czy rozwiązanie nadal działa.

Dsl jest teraz z obsługą MEF. Jako rozszerzenia MEF można pisać polecenia menu, programy obsługi gestów i ograniczenia weryfikacji. Możesz napisać te rozszerzenia w rozwiązaniu DSL razem z innym kodem niestandardowym. Ponadto ty lub inni deweloperzy możecie pisać oddzielne rozszerzenia Visual Studio, które rozszerzają dsl.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Tworzenie rozszerzenia dla DSL z obsługą mef

Jeśli masz dostęp do DSL z obsługą mef utworzone przez siebie lub kogoś innego, możesz napisać dla niego rozszerzenia. Rozszerzenia mogą służyć do dodawania poleceń menu, programów obsługi gestów lub ograniczeń walidacji. Do tworzenia tych rozszerzeń należy użyć Visual Studio rozszerzenia (VSIX). Rozwiązanie ma dwie części: projekt biblioteki klas, który tworzy zestaw kodu, i projekt VSIX, który pakuje zestaw.

### <a name="to-create-a-dsl-extension-vsix"></a>Aby utworzyć rozszerzenie DSL VSIX

1. Utwórz nowy projekt **Biblioteka** klas.

2. W nowym projekcie dodaj odwołanie do zestawu DSL.

   - Ten zestaw ma zazwyczaj nazwę, która kończy się na ".Dsl.dll".

   - Jeśli masz dostęp do projektu DSL, plik zestawu można znaleźć w katalogu **Dsl \\ bin \\ \***

   - Jeśli masz dostęp do pliku VSIX DSL, możesz znaleźć zestaw, zmieniając rozszerzenie nazwy pliku VSIX na ".zip". Zdekompresuj .zip plik.

3. Dodaj odwołania do następujących zestawów .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Utwórz nowy projekt **VSIX.**

5. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt VSIX i wybierz polecenie **Ustaw jako projekt startowy**.

6. W nowym projekcie otwórz plik open **source.extension.vsixmanifest.**

7. Kliknij **pozycję Dodaj zawartość.** W oknie dialogowym ustaw dla ustawienia **Typ** zawartości wartość **Składnik MEF,** a w polu **Projekt źródłowy** ustaw projekt biblioteki klas.

8. Dodaj odwołanie VSIX do DSL.

   1. W **pliku source.extension.vsixmanifest** kliknij **pozycję Dodaj odwołanie**

   2. W oknie dialogowym kliknij **pozycję Dodaj ładunek,** a następnie znajdź plik VSIX DSL. Plik VSIX jest wbudowany w rozwiązanie DSL w **pojemniku \\ \\ \* DslPackage**.

       Umożliwia to użytkownikom instalowanie DSL i rozszerzenia w tym samym czasie. Jeśli użytkownik zainstalował już DSL, zostanie zainstalowane tylko Twoje rozszerzenie.

9. Przejrzyj i zaktualizuj inne pola w **pliku source.extension.vsixmanifest**. Kliknij **pozycję Wybierz wersje** i sprawdź, czy ustawiono Visual Studio wersje.

10. Dodaj kod do projektu biblioteki klas. Skorzystaj z przykładów w następnej sekcji jako przewodnika.

     Można dodać dowolną liczbę klas poleceń, gestów i walidacji.

11. Aby przetestować rozszerzenie, naciśnij **klawisz F5**. W eksperymentalnym wystąpieniu Visual Studio utwórz lub otwórz przykładowy plik DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Pisanie rozszerzeń MEF dla plików DSL

Rozszerzenia można pisać w projekcie kodu zestawu oddzielnego rozwiązania rozszerzenia DSL. Możesz również użyć mef w projekcie DslPackage jako wygodnego sposobu pisania poleceń, gestów i kodu weryfikacyjnego w ramach DSL.

### <a name="menu-commands"></a>Polecenia menu

Aby napisać polecenie menu, zdefiniuj klasę, która implementuje klasę i poprzedza ją atrybutem zdefiniowanym w dsl <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> o nazwie *YourDsl* `CommandExtension` . Można napisać więcej niż jedną klasę poleceń menu.

`QueryStatus()` Jest wywoływana za każdym razem, gdy użytkownik kliknie diagram prawym przyciskiem myszy. Powinien sprawdzić bieżący wybór i ustawić , `command.Enabled` aby wskazać, kiedy polecenie ma zastosowanie.

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

### <a name="gesture-handlers"></a>Programy obsługi gestów

Procedura obsługi gestów może radzić sobie z obiektami przeciąganych na diagram z dowolnego miejsca, wewnątrz lub Visual Studio. Poniższy przykład umożliwia użytkownikowi przeciąganie plików z Eksplorator Windows na diagram. Tworzy elementy, które zawierają nazwy plików.

Można pisać programy obsługi, aby radzić sobie z przeciąganiem z innych modeli DSL i modeli UML. Aby uzyskać więcej informacji, [zobacz How to: Add a Drag-and-Drop Handler (Jak dodać program obsługi przeciągania i upuszczania).](../modeling/how-to-add-a-drag-and-drop-handler.md)

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

Metody walidacji są oznaczone przez `ValidationExtension` atrybut generowany przez DSL, a także przez <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Metoda może występować w dowolnej klasie, która nie jest oznaczona przez atrybut.

Aby uzyskać więcej informacji, zobacz Validation in a Domain-Specific Language (Walidacja [w Domain-Specific Języku ).](../modeling/validation-in-a-domain-specific-language.md)

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
