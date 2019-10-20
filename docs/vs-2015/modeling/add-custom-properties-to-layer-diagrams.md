---
title: Dodawanie właściwości niestandardowych do diagramów warstw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec1c7c94c8a0e6aa233cf21f9b57e093cc430d48
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655287"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Dodawanie właściwości niestandardowych do diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas pisania kodu rozszerzenia dla diagramów warstw można przechowywać wartości z dowolnym elementem na diagramie warstwowym. Wartości będą utrwalane po zapisaniu i ponownym otwarciu diagramu. Możesz również mieć te właściwości, które są wyświetlane w oknie **Właściwości** , aby użytkownicy mogli je zobaczyć i edytować. Na przykład możesz zezwolić użytkownikom na określenie wyrażenia regularnego dla każdej warstwy i napisać kod sprawdzania poprawności, aby sprawdzić, czy nazwy klas w poszczególnych warstwach są zgodne ze wzorcem określonym przez użytkownika.

## <a name="properties-not-visible-to-the-user"></a>Właściwości, które nie są widoczne dla użytkownika
 Jeśli chcesz, aby kod dołączył wartości do dowolnego elementu w diagramie warstwowym, nie musisz definiować składnika MEF. Istnieje słownik o nazwie `Properties` w [ILayerElement](/previous-versions/ff644511(v=vs.140)). Po prostu Dodaj wartości, które można zorganizować do słownika dowolnego elementu warstwy. Zostaną one zapisane w ramach diagramu warstwowego. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Właściwości, które użytkownik może edytować
 **Wstępne przygotowanie**

> [!IMPORTANT]
> Aby wyświetlić właściwości, należy wprowadzić następujące zmiany na każdym komputerze, na którym właściwości warstwy mają być widoczne.
>
>  1. Uruchom program Notepad przy użyciu polecenia **Uruchom jako administrator**. Otwórz `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`
>
>  2. Wewnątrz elementu `Content` Dodaj:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. W sekcji **Visual Studio Tools** w menu Start aplikacji Visual Studio otwórz pozycję **wiersz polecenia dla deweloperów**.
>
>     Wejść
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Uruchom ponownie program Visual Studio.

 **Upewnij się, że kod znajduje się w projekcie VSIX**

 Jeśli właściwość jest częścią polecenia, gestu lub projektu walidacji, nie trzeba dodawać żadnych elementów. Kod właściwości niestandardowej powinien być zdefiniowany w projekcie rozszerzalności programu Visual Studio zdefiniowanym jako składnik MEF. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń i gestów do diagramów warstwowych](../modeling/add-commands-and-gestures-to-layer-diagrams.md) lub [Dodawanie niestandardowej walidacji architektury do diagramów warstwowych](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Zdefiniuj właściwość niestandardową**

 Aby utworzyć niestandardową właściwość, zdefiniuj klasę taką jak ta:

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

 Można zdefiniować właściwości [ILayerElement](/previous-versions/ff644511(v=vs.140)) lub dowolnej z klas pochodnych, które obejmują:

- `ILayerModel` — model

- `ILayer` — każda warstwa

- `ILayerDependencyLink` — linki między warstwami

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Przykład
 Poniższy kod jest typowym deskryptorem właściwości niestandardowych. Definiuje Właściwość Boolean modelu warstwy (`ILayerModel`), która umożliwia użytkownikowi podanie wartości dla niestandardowej metody walidacji.

```
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
 [Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)
