---
title: FeatureProperty — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c9407e78a32ad9f9d8ee4ecd1ae4462409decfc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867913"
---
# <a name="featureproperty-element"></a>FeatureProperty — element
  Reprezentuje właściwość niestandardowa, która jest uwzględniany w funkcji, gdy aplikacja jest wdrożona w programie SharePoint. Po wdrożeniu funkcji właściwości są dostępne w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Key**|Wymagane **xs:string** atrybutu.<br /><br /> Klucz, który jest używany do przechowywania i pobierania wartości właściwości. Każda właściwość musi mieć klucz, który jest unikatowy w obrębie funkcji.|  
|**Wartość**|Wymagane **xs:string** atrybutu.<br /><br /> Wartość właściwości.|  
  
### <a name="child-elements"></a>Elementy podrzędne
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne
  
|Element|Opis|  
|-------------|-----------------|  
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są uwzględniane przy użyciu funkcji, gdy aplikacja jest wdrożona w programie SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat właściwości funkcji, zobacz [wdrażanie pakietów i informacjami w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informacje o elementach
  
|||  
|-|-|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Plik walidacji**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz także
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
