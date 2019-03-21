---
title: Projectitemfolder — Element | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 124716f8c40a8adc0a0ae1a28cda21dcb5e00ddf
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322833"
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
|**Docelowy**|Wymagane **xs: ciąg** atrybutu.<br /><br /> Ścieżka folderu, w instalacji programu SharePoint, który odpowiada zamapowany folder, względem folderu głównego wdrożenia. Folder główny wdrożenia jest określana przez typ wdrożenia, określony przez **typu** atrybutu.<br /><br /> Aby uzyskać więcej informacji, zobacz opisy **Ścieżka rozmieszczania** i **główny wdrożenia** właściwości programu SharePoint projektu elementów w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Typ wdrożenia dla zamapowany folder. Aby uzyskać więcej informacji na temat możliwych wartości, zobacz opis **typu wdrożenia** właściwości elementów projektu programu SharePoint w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element jest wymaganego głównego elementu *spdata* pliku.|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji na temat folderów mapowanych zobacz [porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informacje o elementach

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md)
