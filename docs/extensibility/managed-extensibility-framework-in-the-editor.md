---
title: Managed Extensibility Framework w edytorze | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632611"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework w edytorze
Edytor jest skompilowany przy użyciu składników Managed Extensibility Framework (MEF). Możesz utworzyć własne składniki MEF w celu rozbudowy edytora, a kod może również zużywać składniki edytora.

## <a name="overview-of-the-managed-extensibility-framework"></a>Przegląd Managed Extensibility Framework
 MEF to biblioteka platformy .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, które są zgodne z modelem programowania MEF. Edytor programu Visual Studio może jednocześnie udostępniać i korzystać z części składnika MEF.

 MEF jest zawarty w zestawie .NET Framework wersja 4 *System. ComponentModel. kompozycji. dll* .

 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Części składników i kontenery kompozycji
 Część składnika jest klasą lub składową klasy, która może wykonać jedną (lub obie) z następujących czynności:

- Korzystanie z innego składnika

- Być używane przez inny składnik

  Rozważmy na przykład aplikację do kupowania, która ma składnik wprowadzania zamówienia, który zależy od danych o dostępności produktu dostarczonych przez składnik magazynu magazynu. W warunkach MEF część spisu może *eksportować* dane dostępności produktu, a część wprowadzanie zamówienia może *importować* dane. Część Order Entry i część spisu nie muszą znać siebie nawzajem. *kontener kompozycji* (udostępniany przez aplikację hosta) jest odpowiedzialny za utrzymanie zestawu eksportu i rozpuszczenie eksportu i importu.

  Kontener kompozycji, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, zazwyczaj należy do hosta. Kontener kompozycji utrzymuje *katalog* wyeksportowanych części składnika.

### <a name="export-and-import-component-parts"></a>Eksportuj i Importuj części składników
 Można eksportować dowolne funkcje, o ile są one implementowane jako Klasa publiczna lub publiczny element członkowski klasy (właściwość lub metoda). Nie ma potrzeby wyprowadzania części składnika z <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Zamiast tego należy dodać atrybut <xref:System.ComponentModel.Composition.ExportAttribute> do klasy lub składowej klasy, która ma zostać wyeksportowana. Ten atrybut określa *kontrakt* , przez który inna część składnika może zaimportować swoją funkcję.

### <a name="the-export-contract"></a>Kontrakt eksportu
 @No__t_0 definiuje jednostki (klasy, interfejsu lub struktury), która jest eksportowana. Zazwyczaj atrybut Export przyjmuje parametr, który określa typ eksportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Domyślnie atrybut <xref:System.ComponentModel.Composition.ExportAttribute> definiuje kontrakt, który jest typem klasy eksportu.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 W przykładzie domyślny atrybut `[Export]` jest równoważny `[Export(typeof(TestAdornmentLayerDefinition))]`.

 Możesz również wyeksportować właściwość lub metodę, jak pokazano w poniższym przykładzie.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importowanie eksportu MEF
 Jeśli chcesz korzystać z eksportu MEF, musisz znać kontrakt (zazwyczaj typ), za pomocą którego została wyeksportowana, i dodać atrybut <xref:System.ComponentModel.Composition.ImportAttribute>, który ma tę wartość. Domyślnie atrybut import przyjmuje jeden parametr, który jest typem klasy, którą modyfikuje. Poniższe wiersze kodu importują typ <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Uzyskaj funkcjonalność edytora z części składnika MEF
 Jeśli istniejący kod jest częścią składnika MEF, można użyć metadanych MEF do użycia części składnika edytora.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Aby korzystać z funkcjonalności edytora z części składnika MEF

1. Dodaj odwołania do *System. kompozycji. ComponentModel. dll*, który znajduje się w globalnej pamięci podręcznej zestawów (GAC), i do zestawów edytora.

2. Dodaj odpowiednie dyrektywy using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Dodaj atrybut `[Import]` do interfejsu usługi w następujący sposób.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Po uzyskaniu usługi można użyć jednego z jej składników.

5. Po skompilowaniu zestawu należy umieścić go w *.. \Common7\IDE\Components \* folderze instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
