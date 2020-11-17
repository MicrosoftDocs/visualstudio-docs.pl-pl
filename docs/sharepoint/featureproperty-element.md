---
title: FeatureProperty — element | Microsoft Docs
description: Wyświetl informacje referencyjne na temat elementu FeatureProperty, który jest elementem w schemacie elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8e6010ac45d0b760325c73c4bd754fbb0b422a77
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672759"
---
# <a name="featureproperty-element"></a>FeatureProperty — element
  Reprezentuje właściwość niestandardową, która jest dołączana do funkcji podczas jej wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do właściwości w kodzie.

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
|**Klucz**|Wymagany atrybut **xs: String** .<br /><br /> Klucz, który jest używany do przechowywania i pobierania wartości właściwości. Każda właściwość musi mieć klucz, który jest unikatowy w ramach tej funkcji.|
|**Wartość**|Wymagany atrybut **xs: String** .<br /><br /> Wartość właściwości.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[FeatureProperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji podczas jej wdrażania w programie SharePoint.|

## <a name="remarks"></a>Uwagi
 Więcej informacji o właściwościach funkcji znajduje się [w temacie dostarczanie informacji o pakiecie i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
