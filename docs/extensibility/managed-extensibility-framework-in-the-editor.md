---
title: Managed Extensibility Framework w edytorze | Microsoft Docs
description: Dowiedz się więcej na temat Managed Extensibility Framework, który umożliwia tworzenie własnych składników w celu rozbudowy edytora w Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 881b0f4d112b7739ff33099b26a30ab073f55924
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073173"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework w edytorze
Edytor jest skompilowany przy użyciu składników Managed Extensibility Framework (MEF). Możesz utworzyć własne składniki MEF w celu rozbudowy edytora, a kod może również zużywać składniki edytora.

## <a name="overview-of-the-managed-extensibility-framework"></a>Przegląd Managed Extensibility Framework
 MEF to biblioteka platformy .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, które są zgodne z modelem programowania MEF. Edytor programu Visual Studio może jednocześnie udostępniać i korzystać z części składnika MEF.

 MEF jest zawarty w zestawie *System.ComponentModel.Composition.dll* .NET Framework w wersji 4.

 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Części składników i kontenery kompozycji
 Część składnika jest klasą lub składową klasy, która może wykonać jedną (lub obie) z następujących czynności:

- Korzystanie z innego składnika

- Być używane przez inny składnik

  Rozważmy na przykład aplikację do kupowania, która ma składnik wprowadzania zamówienia, który zależy od danych o dostępności produktu dostarczonych przez składnik magazynu magazynu. W warunkach MEF część spisu może *eksportować* dane dostępności produktu, a część wprowadzanie zamówienia może *importować* dane. Część Order Entry i część spisu nie muszą znać siebie nawzajem. *kontener kompozycji* (udostępniany przez aplikację hosta) jest odpowiedzialny za utrzymanie zestawu eksportu i rozpuszczenie eksportu i importu.

  Kontener kompozycji, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> ,, zazwyczaj należy do hosta. Kontener kompozycji utrzymuje *katalog* wyeksportowanych części składnika.

### <a name="export-and-import-component-parts"></a>Eksportuj i Importuj części składników
 Można eksportować dowolne funkcje, o ile są one implementowane jako Klasa publiczna lub publiczny element członkowski klasy (właściwość lub metoda). Nie ma potrzeby wyprowadzania części składnika z programu <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . Zamiast tego należy dodać <xref:System.ComponentModel.Composition.ExportAttribute> atrybut do klasy lub składowej klasy, która ma zostać wyeksportowana. Ten atrybut określa *kontrakt* , przez który inna część składnika może zaimportować swoją funkcję.

### <a name="the-export-contract"></a>Kontrakt eksportu
 <xref:System.ComponentModel.Composition.ExportAttribute>Definiuje jednostkę (klasę, interfejs lub strukturę), która jest eksportowana. Zazwyczaj atrybut Export przyjmuje parametr, który określa typ eksportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Domyślnie <xref:System.ComponentModel.Composition.ExportAttribute> atrybut definiuje kontrakt, który jest typem klasy eksportu.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 W przykładzie domyślnym `[Export]` atrybutem jest odpowiednik `[Export(typeof(TestAdornmentLayerDefinition))]` .

 Możesz również wyeksportować właściwość lub metodę, jak pokazano w poniższym przykładzie.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importowanie eksportu MEF
 Jeśli chcesz wykorzystać eksport MEF, musisz znać kontrakt (zazwyczaj typ), za pomocą którego została wyeksportowana, i dodać <xref:System.ComponentModel.Composition.ImportAttribute> atrybut, który ma tę wartość. Domyślnie atrybut import przyjmuje jeden parametr, który jest typem klasy, którą modyfikuje. Poniższe wiersze kodu importują <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> Typ.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Uzyskaj funkcjonalność edytora z części składnika MEF
 Jeśli istniejący kod jest częścią składnika MEF, można użyć metadanych MEF do użycia części składnika edytora.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Aby korzystać z funkcjonalności edytora z części składnika MEF

1. Dodaj odwołania do *System.Composition.ComponentModel.dll*, które znajduje się w globalnej pamięci podręcznej zestawów (GAC), oraz do zestawów edytora.

2. Dodaj odpowiednie dyrektywy using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Dodaj `[Import]` atrybut do interfejsu usługi w następujący sposób.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Po uzyskaniu usługi można użyć jednego z jej składników.

5. Po skompilowaniu zestawu należy umieścić go w *.. \* Folder \Common7\IDE\Components instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
