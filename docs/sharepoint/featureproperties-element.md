---
title: Featureproperties — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6860a91067daa6da1d4223ae5060385087ad3433
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967334"
---
# <a name="featureproperties-element"></a>FeatureProperties — element
  Kolekcja wartości właściwości, które są uwzględniane przy użyciu funkcji, gdy aplikacja jest wdrożona w programie SharePoint. Po wdrożeniu funkcji wartości właściwości są dostępne w kodzie.

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
|[FeatureProperty —](../sharepoint/featureproperty-element.md)|Element opcjonalny.<br /><br /> Reprezentuje właściwość niestandardową, w formacie klucz/wartość.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaganego głównego elementu z `.spdata` pliku.|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji na temat właściwości funkcji, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elementach

|Element|Opis|
|-------------|-----------------|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
