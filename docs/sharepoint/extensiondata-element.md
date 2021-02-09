---
title: ExtensionData — — element | Microsoft Docs
description: Wyświetl informacje referencyjne na temat elementu ExtensionData —, który jest elementem w schemacie elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd82aaec96eff3cf3d20fd9d0607ac5aae6b3472
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876839"
---
# <a name="extensiondata-element"></a>ExtensionData — element
  Reprezentuje kolekcję niestandardowych elementów danych, które są skojarzone z elementem projektu programu SharePoint.

## <a name="syntax"></a>Składnia

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ExtensionDataItem —](../sharepoint/extensiondataitem-element.md)|Element opcjonalny.<br /><br /> Reprezentuje niestandardowy element danych skojarzony z elementem projektu programu SharePoint w formacie klucz/wartość. Zarówno klucz, jak i wartość muszą być ciągami.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaga elementu głównego `.spdata` pliku.|

## <a name="remarks"></a>Uwagi
 W przypadku kojarzenia danych niestandardowych z elementem projektu programu SharePoint przy użyciu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu program Visual Studio zapisuje dane do elementu **ExtensionData —** w `.spdata` pliku dla elementu projektu. Aby uzyskać więcej informacji, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
