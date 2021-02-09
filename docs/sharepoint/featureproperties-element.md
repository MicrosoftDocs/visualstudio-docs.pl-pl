---
title: FeatureProperties — — element | Microsoft Docs
description: Wyświetl informacje referencyjne na temat elementu FeatureProperties —, który jest elementem w schemacie elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8756feaf08de9b01904309177f5e19c122da714d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876722"
---
# <a name="featureproperties-element"></a>FeatureProperties — element
  Kolekcja wartości właściwości, które są dołączone do funkcji podczas jej wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do wartości właściwości w kodzie.

## <a name="syntax"></a>Składnia

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Element opcjonalny.<br /><br /> Reprezentuje właściwość niestandardową w formacie klucz/wartość.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaga elementu głównego `.spdata` pliku.|

## <a name="remarks"></a>Uwagi
 Więcej informacji o właściwościach funkcji znajduje się [w temacie zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elemencie

|Element|Opis|
|-------------|-----------------|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
