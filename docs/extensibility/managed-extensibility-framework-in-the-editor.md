---
title: Zarządzane ramy rozszerzalności w edytorze | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702865"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Zarządzane ramy rozszerzalności w edytorze
Edytor jest zbudowany przy użyciu składników managed extensibility framework (MEF). Można utworzyć własne składniki MEF, aby rozszerzyć edytora, a kod może korzystać ze składników edytora, jak również.

## <a name="overview-of-the-managed-extensibility-framework"></a>Omówienie struktury zarządzanej rozszerzalności
 MEF to biblioteka .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, który następuje po modelu programowania MEF. Edytor programu Visual Studio może zarówno dostarczać i zużywać części składowe MEF.

 MeF jest zawarty w .NET Framework w wersji 4 *System.ComponentModel.Composition.dll* zestawu.

 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Części składowe i pojemniki na kompozycje
 Część składowa jest klasą lub członkiem klasy, która może wykonać jedną (lub obie) następujące czynności:

- Zużywają inny składnik

- Być zużywane przez inny składnik

  Rozważmy na przykład aplikację zakupów, która ma składnik wprowadzania zamówienia, który zależy od danych dostępności produktu dostarczonych przez składnik magazynu. W warunkach MEF część zapasów może *eksportować* dane o dostępności produktów, a część zapisu zamówienia może *importować* dane. Część zapisu zamówienia i część magazynowa nie muszą wiedzieć o sobie nawzajem; *kontener składowy* (dostarczony przez aplikację przyjmującą) jest odpowiedzialny za utrzymanie zestawu wywozu oraz rozwiązanie wywozu i przywozu.

  Kontener kompozycji, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>jest zazwyczaj własnością hosta. Kontener kompozycji przechowuje *katalog* eksportowanych części składowych.

### <a name="export-and-import-component-parts"></a>Eksportowanie i importowanie części składowych
 Można wyeksportować dowolną funkcjonalność, tak długo, jak jest zaimplementowana jako klasa publiczna lub publiczny element członkowski klasy (właściwość lub metoda). Nie trzeba wyprowadzać części składowego <xref:System.ComponentModel.Composition.Primitives.ComposablePart>z pliku . Zamiast tego należy dodać <xref:System.ComponentModel.Composition.ExportAttribute> atrybut do klasy lub elementu członkowskiego klasy, który chcesz wyeksportować. Ten atrybut określa *kontrakt,* za pomocą którego inna część komponentu może importować funkcje.

### <a name="the-export-contract"></a>Umowa eksportowa
 Definiuje <xref:System.ComponentModel.Composition.ExportAttribute> jednostkę (klasę, interfejs lub strukturę), która jest eksportowana. Zazwyczaj atrybut eksportu przyjmuje parametr określający typ eksportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Domyślnie <xref:System.ComponentModel.Composition.ExportAttribute> atrybut definiuje kontrakt, który jest typem klasy eksportującej.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 W tym przykładzie `[Export]` atrybut domyślny `[Export(typeof(TestAdornmentLayerDefinition))]`jest odpowiednikiem .

 Można również wyeksportować właściwość lub metodę, jak pokazano w poniższym przykładzie.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importowanie eksportu MEF
 Jeśli chcesz korzystać z eksportu MEF, musisz znać kontrakt (zazwyczaj typ), za pomocą <xref:System.ComponentModel.Composition.ImportAttribute> którego został wyeksportowany i dodać atrybut, który ma tę wartość. Domyślnie atrybut importu przyjmuje jeden parametr, który jest typem klasy, która modyfikuje. Następujące wiersze kodu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> importują typ.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Pobierz funkcjonalność edytora z części komponentu MEF
 Jeśli istniejący kod jest częścią składnika MEF, można użyć metadanych MEF do korzystania z części składowych edytora.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Aby korzystać z funkcji edytora z części komponentu MEF

1. Dodaj odwołania do *System.Composition.ComponentModel.dll*, który znajduje się w globalnej pamięci podręcznej zestawów (GAC) i do zestawów edytora.

2. Dodaj odpowiednie za pomocą dyrektyw.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Dodaj `[Import]` atrybut do interfejsu usługi w następujący sposób.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Po uzyskaniu usługi można korzystać z jednego z jej składników.

5. Po skompilowaniu zestawu umieść go w *.. folder \Common7\IDE\Components\* instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
