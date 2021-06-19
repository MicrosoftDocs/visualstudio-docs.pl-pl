---
title: Dodawanie właściwości niestandardowych do diagramów zależności
description: Dowiedz się, jak przechowywać wartości z dowolnym elementem na diagramie zależności podczas pisania kodu rozszerzenia dla diagramów zależności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70588a2d472a1170b58911eece4fa70831064f72
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389855"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Dodawanie właściwości niestandardowych do diagramów zależności

Podczas pisania kodu rozszerzenia dla diagramów zależności można przechowywać wartości z dowolnym elementem na diagramie zależności. Wartości zostaną utrwalone, gdy diagram zostanie zapisany i ponownie otwarty. Te właściwości mogą być również wyświetlane w **oknie** Właściwości, dzięki czemu użytkownicy mogą je wyświetlać i edytować. Można na przykład pozwolić użytkownikom na określenie wyrażenia regularnego dla każdej warstwy i napisanie kodu weryfikacji w celu sprawdzenia, czy nazwy klas w każdej warstwie są zgodne ze wzorcem określonym przez użytkownika.

## <a name="non-visible-properties"></a>Właściwości niewidoczne

Jeśli chcesz, aby kod dołączał wartości do dowolnego elementu na diagramie zależności, nie musisz definiować składnika MEF. Istnieje słownik o nazwie w `Properties` [ILayerElement](/previous-versions/ff644511(v=vs.140)). Wystarczy dodać wartości z marshalable do słownika dowolnego elementu warstwy. Zostaną one zapisane w ramach diagramu zależności.

## <a name="editable-properties"></a>Właściwości edytowalne

**Wstępne przygotowanie**

> [!IMPORTANT]
> Aby właściwości były wyświetlane, należy wprowadzić następujące zmiany na każdym komputerze, na którym mają być widoczne właściwości warstwy:
>
> 1. Uruchom Notatnik przy użyciu funkcji **Uruchom jako administrator.** Otwórz *plik %ProgramFiles%\Microsoft Visual Studio [wersja]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest.*
> 2. W **elemencie Content** dodaj:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. W **sekcji Visual Studio Tools** menu Start aplikacji Visual Studio otwórz **wiersz polecenia dla deweloperów**. Wprowadź:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Uruchom ponownie program Visual Studio.

**Upewnij się, że kod znajduje się w projekcie VSIX**

Jeśli właściwość jest częścią projektu polecenia, gestu lub walidacji, nie trzeba niczego dodawać. Kod właściwości niestandardowej powinien być zdefiniowany w projekcie rozszerzalności Visual Studio zdefiniowanym jako składnik MEF. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń i gestów](../modeling/add-commands-and-gestures-to-layer-diagrams.md) do diagramów zależności lub Dodawanie niestandardowej weryfikacji architektury do [diagramów zależności.](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

**Definiowanie właściwości niestandardowej**

Aby utworzyć właściwość niestandardową, zdefiniuj klasę w ten sposób:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Można zdefiniować właściwości elementu [ILayerElement](/previous-versions/ff644511(v=vs.140)) lub dowolnej z jego klas pochodnych, takich jak:

- `ILayerModel` — model

- `ILayer` — każda warstwa

- `ILayerDependencyLink` — łącza między warstwami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Przykład

Poniższy kod jest typowym deskryptorem właściwości niestandardowych. Definiuje właściwość logiczną w modelu warstwy ( ), która umożliwia użytkownikowi podanie wartości `ILayerModel` dla niestandardowej metody weryfikacji.

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

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
