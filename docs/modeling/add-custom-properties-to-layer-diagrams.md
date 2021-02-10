---
title: Dodawanie właściwości niestandardowych do diagramów zależności
description: Dowiedz się, w jaki sposób można przechowywać wartości z dowolnym elementem w diagramie zależności podczas pisania kodu rozszerzenia dla diagramów zależności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d63c6793290786499dd75ffd139f9905f46e7ab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946465"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Dodawanie właściwości niestandardowych do diagramów zależności

Podczas pisania kodu rozszerzenia dla diagramów zależności można przechowywać wartości z dowolnym elementem na diagramie zależności. Wartości będą utrwalane po zapisaniu i ponownym otwarciu diagramu. Możesz również mieć te właściwości, które są wyświetlane w oknie **Właściwości** , aby użytkownicy mogli je zobaczyć i edytować. Na przykład możesz zezwolić użytkownikom na określenie wyrażenia regularnego dla każdej warstwy i napisać kod sprawdzania poprawności, aby sprawdzić, czy nazwy klas w poszczególnych warstwach są zgodne ze wzorcem określonym przez użytkownika.

## <a name="non-visible-properties"></a>Niewidoczne właściwości

Jeśli chcesz, aby kod dołączył wartości do dowolnego elementu na diagramie zależności, nie musisz definiować składnika MEF. Istnieje słownik o nazwie `Properties` w [ILayerElement](/previous-versions/ff644511(v=vs.140)). Po prostu Dodaj wartości, które można zorganizować do słownika dowolnego elementu warstwy. Zostaną one zapisane w ramach diagramu zależności.

## <a name="editable-properties"></a>Właściwości edytowalne

**Wstępne przygotowanie**

> [!IMPORTANT]
> Aby wyświetlić właściwości, wprowadź następujące zmiany na każdym komputerze, na którym właściwości warstwy mają być widoczne:
>
> 1. Uruchom program Notepad przy użyciu polecenia **Uruchom jako administrator**. Otwórz *program%ProgramFiles%\Microsoft Visual Studio [wersja] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. W elemencie **Content (zawartość** ) Dodaj:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. W sekcji **Visual Studio Tools** w menu Start aplikacji Visual Studio otwórz pozycję **wiersz polecenia dla deweloperów**. Wprowadź:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Uruchom ponownie program Visual Studio.

**Upewnij się, że kod znajduje się w projekcie VSIX**

Jeśli właściwość jest częścią polecenia, gestu lub projektu walidacji, nie trzeba dodawać żadnych elementów. Kod właściwości niestandardowej powinien być zdefiniowany w projekcie rozszerzalności programu Visual Studio zdefiniowanym jako składnik MEF. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md) lub [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Zdefiniuj właściwość niestandardową**

Aby utworzyć niestandardową właściwość, zdefiniuj klasę taką jak ta:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Można zdefiniować właściwości [ILayerElement](/previous-versions/ff644511(v=vs.140)) lub dowolnej z klas pochodnych, które obejmują:

- `ILayerModel` — Model

- `ILayer` -Każda warstwa

- `ILayerDependencyLink` -linki między warstwami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Przykład

Poniższy kod jest typowym deskryptorem właściwości niestandardowych. Definiuje Właściwość Boolean modelu warstwy ( `ILayerModel` ), która umożliwia użytkownikowi podanie wartości dla niestandardowej metody walidacji.

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
