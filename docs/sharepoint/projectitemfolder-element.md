---
title: Projectitemfolder — — element | Microsoft Docs
description: Pobierz informacje referencyjne na temat elementu Projectitemfolder —, który reprezentuje zamapowany folder w odwołaniu do schematu XML elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99a27f8e255aa17e8b9fa604b504109976c5d36a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440795"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder — element
  Reprezentuje zamapowany folder.

## <a name="syntax"></a>Składnia

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Typ
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**Obiektów**|Wymagany atrybut **xs: String** .<br /><br /> Ścieżka folderu w instalacji programu SharePoint, do której odnosi się zamapowany folder, względem folderu głównego wdrożenia. Folder główny wdrożenia jest określany przez typ wdrożenia określony przez atrybut **typu** .<br /><br /> Aby uzyskać więcej informacji, zobacz opisy dotyczące **ścieżki wdrożenia** i właściwości **głównych wdrożenia** elementów projektu programu SharePoint w temacie [opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagany atrybut **xs: String** .<br /><br /> Typ wdrożenia dla zamapowanego folderu. Aby uzyskać więcej informacji o możliwych wartościach, zobacz opis właściwości **typ wdrożenia** elementów projektu programu SharePoint w temacie [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element jest wymaganym elementem głównym pliku *. spdata* .|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji na temat mapowanych folderów, zobacz [jak: Dodawanie i usuwanie mapowanych folderów](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Obszaru**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Instrukcje: Dodawanie i usuwanie mapowanych folderów](../sharepoint/how-to-add-and-remove-mapped-folders.md)
