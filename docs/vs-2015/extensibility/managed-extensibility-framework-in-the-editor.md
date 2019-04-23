---
title: Managed Extensibility Framework, w edytorze | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae47942e9b686ac02623e4b3f2d0681babf879f9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084031"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Struktura Managed Extensibility Framework (MEF) w edytorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor została stworzona przy użyciu składników Managed Extensibility Framework (MEF). Możesz tworzyć własne składniki MEF do rozszerzenia edytora, a Twój kod może zużywać także składniki edytora.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework — omówienie  
 MEF jest bibliotekę .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, który jest zgodna z modelu programowania MEF. Edytor programu Visual Studio można, zarówno zapewniają i wykorzystują części MEF.  
  
 MEF znajduje się w zestawie System.ComponentModel.Composition.dll programu .NET Framework w wersji 4.  
  
 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Składniki i tworzenia kontenerów  
 Część jest klasa lub członek klasy, które można wykonać jedną (lub obie) z następujących czynności:  
  
- Używanie innego składnika  
  
- Być wykorzystane przez inny składnik  
  
  Na przykład należy wziąć pod uwagę zakupów aplikacja, która ma składnik wpisu zamówienia, który jest zależny od danych dostępności produktu, dostarczone przez składnik spisu magazynu. W warunkach MEF, część spisu można *wyeksportować* dane dostępności produktów i będzie można część wpisu zamówienia *zaimportować* danych. Wpis kolejności i część magazynu nie trzeba wiedzieć o *pojemnik składu* (udostępniany przez aplikację hosta) jest odpowiedzialny za utrzymanie zbiór eksporty i rozpoznawanie polecenie eksportuje, a następnie importuje.  
  
  Kontener kompozycji <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, zwykle jest własnością hosta. Kontener kompozycji przechowuje *katalogu* wyeksportowanego składniki.  
  
### <a name="exporting-and-importing-component-parts"></a>Eksportowanie i Importowanie części składowe  
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
  
### <a name="importing-a-mef-export"></a>Importowanie Eksport MEF  
 Umożliwia używanie Eksport MEF, musisz znać kontraktu (zazwyczaj typu), za pomocą którego on został wyeksportowany, a następnie dodaj <xref:System.ComponentModel.Composition.ImportAttribute> atrybut, który ma tę wartość. Domyślnie atrybut importu przyjmuje jeden parametr, który jest typem klasy, która modyfikuje. Następujące wiersze kodu importu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typu.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Wprowadzenie edytora z część MEF  
 Jeśli istniejący kod jest część MEF, można użyć metadanych MEF z części składnika edytora.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Korzystanie z funkcji edytora część MEF  
  
1. Dodaj odwołania do System.Composition.ComponentModel.dll, który znajduje się w globalnej pamięci podręcznej zestawów (GAC), do zestawów w edytorze.  
  
2. Dodaj odpowiednie instrukcje using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. Dodaj `[Import]` atrybutu do interfejsu usługi, w następujący sposób.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. Po uzyskaniu usługi mogą wykorzystywać jeden z jego składników.  
  
5. Kiedy została wykonana zestawu, w jakich go umieszczono... \Common7\IDE\Components\ folder instalacji programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
