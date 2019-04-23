---
title: Dodawanie właściwości niestandardowych do diagramów zależności
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c4639b5e2edcfebd05dcc6511102c0369b4b3e1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066094"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Dodawanie właściwości niestandardowych do diagramów zależności

Podczas pisania kodu rozszerzenia diagramów zależności, można przechowywać wartości z dowolnego elementu na diagram zależności. Wartości będą się utrzymywać, po zapisaniu i ponownym otwarciu diagramu. Może również zawierać te właściwości są wyświetlane w **właściwości** okna tak, aby użytkownicy mogli widzieć i je edytować. Na przykład można pozwolić użytkownikom na określenie wyrażenia regularnego dla każdej warstwy i napisanie kodu sprawdzania poprawności, aby sprawdzić zgodność nazw klas w każdej warstwie ze wzorcem określonym przez użytkownika.

## <a name="non-visible-properties"></a>Inne niż widocznych właściwości

Jeśli chcesz tylko Twój kod dołączył wartości dowolnego elementu w diagramie zależności, nie musisz zdefiniować składnik MEF. Jest słownik o nazwie `Properties` w <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Po prostu Dodaj zorganizowane wartości do słownika dowolnego elementu warstwy. Zostaną one zapisane jako część diagram zależności.

## <a name="editable-properties"></a>Można edytować właściwości

**Wstępne przygotowania**

> [!IMPORTANT]
> Aby ułatwić właściwości są wyświetlane, wprowadź następującą zmianę na każdym komputerze, na którym ma właściwości warstwy mają być widoczne:
>
> 1. Uruchom program Notatnik za pomocą **Uruchom jako Administrator**. Otwórz *%ProgramFiles%\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. Wewnątrz **zawartości** elementu dodawanie:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. W obszarze **Visual Studio Tools** części programu Visual Studio application menu start, otwórz **wiersz polecenia dla deweloperów**. Wprowadź:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Uruchom ponownie program Visual Studio.

**Upewnij się, że Twój kod znajduje się w projekcie VSIX**

Jeśli Twoja własność jest częścią polecenia, gestu lub projekt sprawdzania poprawności, nie trzeba nic dodawać. Kod dla właściwości niestandardowej powinien być zdefiniowany w projekcie programu Visual Studio Extensibility zdefiniowany jako składnik MEF. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md) lub [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Zdefiniuj właściwości niestandardowe**

Aby utworzyć niestandardową właściwość, zdefiniuj klasę podobną do tej:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Można zdefiniować właściwości na <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> lub dowolny z jej klas pochodnych, które obejmują:

- `ILayerModel` -modelu

- `ILayer` — Każda warstwa

- `ILayerDependencyLink` — łącza między warstwami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Przykład

Poniższy kod jest typową właściwością niestandardową deskryptora. Definiuje właściwość typu Boolean na modelu warstwy (`ILayerModel`) umożliwiający użytkownikowi podanie wartości dla niestandardowej metody walidacji.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
