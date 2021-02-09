---
title: Files — element | Microsoft Docs
description: Wyświetl informacje referencyjne na temat elementu Files, który jest elementem w schemacie elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 653e48a2e9b6a68db94fd66660da85f4dec20927
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876650"
---
# <a name="files-element"></a>Element Pliki
  Określa pliki do wdrożenia za pomocą elementu projektu programu SharePoint, takich jak pliki elementów funkcji i dane wyjściowe zależnych projektów spoza programu SharePoint.

## <a name="syntax"></a>Składnia

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Typ
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItemFile —](../sharepoint/projectitemfile-element.md)|Opcjonalny element **ProjectItemFileType** .<br /><br /> Reprezentuje plik programu SharePoint, taki jak plik elementu funkcji, do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.|
|[ProjectOutputFile —](../sharepoint/projectoutputfile-element.md)|Opcjonalny element **ProjectOutputFileType** .<br /><br /> Przedstawia dane wyjściowe projektu do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaga elementu głównego `.spdata` pliku.|

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
