---
title: Extensiondataitem — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f5a547194de87a7fe151c3530720a078ca01438
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873083"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem — element
  Element danych niestandardowych, który jest skojarzony z elementu projektu programu SharePoint w formacie klucz/wartość. Klucz i wartość muszą być ciągami.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Key**|Wymagane **xs: ciąg** atrybutu.<br /><br /> Klucz, który jest używany do przechowywania i pobierania elementu danych.|  
|**Wartość**|Wymagane **xs:string** atrybutu.<br /><br /> Wartość elementu danych.|  
  
### <a name="child-elements"></a>Elementy podrzędne
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne
  
|Element|Opis|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy Skojarz dane niestandardowe z elementu projektu programu SharePoint przy użyciu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu, program Visual Studio zapisuje dane na nowe **extensiondataitem —** elementu w `.spdata` plik Element projektu. Aby uzyskać więcej informacji, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informacje o elementach
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Plik walidacji**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz także
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
