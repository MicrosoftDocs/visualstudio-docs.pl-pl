---
title: Managed Extensibility Framework, w edytorze | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a272c01f76787e60e7796173b52b563f8e8718
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702047"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework, w edytorze
Edytor została stworzona przy użyciu składników Managed Extensibility Framework (MEF). Możesz tworzyć własne składniki MEF do rozszerzenia edytora, a Twój kod może zużywać także składniki edytora.

## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework — omówienie
 MEF jest bibliotekę .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, który jest zgodna z modelu programowania MEF. Edytor programu Visual Studio można, zarówno zapewniają i wykorzystują części MEF.

 MEF jest zawarty w .NET Framework w wersji 4 *System.ComponentModel.Composition.dll* zestawu.

 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Składniki i tworzenia kontenerów
 Część jest klasa lub członek klasy, które można wykonać jedną (lub obie) z następujących czynności:

- Używanie innego składnika

- Być wykorzystane przez inny składnik

  Na przykład należy wziąć pod uwagę zakupów aplikacja, która ma składnik wpisu zamówienia, który jest zależny od danych dostępności produktu, dostarczone przez składnik spisu magazynu. W warunkach MEF, część spisu można *wyeksportować* dane dostępności produktów i będzie można część wpisu zamówienia *zaimportować* danych. Wpis kolejności i część magazynu nie trzeba wiedzieć o *pojemnik składu* (udostępniany przez aplikację hosta) jest odpowiedzialny za utrzymanie zbiór eksporty i rozpoznawanie polecenie eksportuje, a następnie importuje.

  Kontener kompozycji <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, zwykle jest własnością hosta. Kontener kompozycji przechowuje *katalogu* wyeksportowanego składniki.

### <a name="export-and-import-component-parts"></a>Eksportowanie i Importowanie części składowe
 Możesz wyeksportować żadnej funkcji, tak długo, jak są one zaimplementowane jako klasę publiczną lub publicznego elementu członkowskiego klasy (właściwość lub metoda). Nie masz do wyprowadzenia użytkownika część z <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Zamiast tego należy dodać <xref:System.ComponentModel.Composition.ExportAttribute> atrybutów do klasy lub składowej klasy, który chcesz wyeksportować. Ten atrybut określa *kontraktu* , który składnik innej części można zaimportować własne funkcje.

### <a name="the-export-contract"></a>Kontrakt eksportu
 <xref:System.ComponentModel.Composition.ExportAttribute> Definiuje jednostki (klasy, interfejsu lub struktury), która jest eksportowany. Zazwyczaj atrybut eksportu przyjmuje parametr, który określa typ operacji eksportu.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Domyślnie <xref:System.ComponentModel.Composition.ExportAttribute> atrybut definiuje kontrakt, który jest typem klasy eksportowania.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 W tym przykładzie domyślne `[Export]` atrybut jest odpowiednikiem `[Export(typeof(TestAdornmentLayerDefinition))]`.

 Jak pokazano w poniższym przykładzie, można wyeksportować właściwości lub metody.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importowanie/eksportowanie MEF
 Umożliwia używanie Eksport MEF, musisz znać kontraktu (zazwyczaj typu), za pomocą którego on został wyeksportowany, a następnie dodaj <xref:System.ComponentModel.Composition.ImportAttribute> atrybut, który ma tę wartość. Domyślnie atrybut importu przyjmuje jeden parametr, który jest typem klasy, która modyfikuje. Następujące wiersze kodu importu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typu.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Uzyskiwanie edytora część MEF
 Jeśli istniejący kod jest część MEF, można użyć metadanych MEF z części składnika edytora.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Korzystanie z funkcji edytora część MEF

1.  Dodaj odwołania do *System.Composition.ComponentModel.dll*, który jest w globalnej pamięci podręcznej zestawów (GAC), a także do zestawów w edytorze.

2.  Dodaj odpowiednie instrukcje using.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3.  Dodaj `[Import]` atrybutu do interfejsu usługi, w następujący sposób.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4.  Po uzyskaniu usługi mogą wykorzystywać jeden z jego składników.

5.  Kiedy została wykonana zestawu, w jakich go umieszczono *... \Common7\IDE\Components\* folder instalacji programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)