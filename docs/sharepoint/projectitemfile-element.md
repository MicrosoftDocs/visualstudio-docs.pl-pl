---
title: ProjectItemFile — — element | Microsoft Docs
description: Pobierz informacje referencyjne na temat elementu ProjectItemFile —, który reprezentuje plik elementu projektu w odwołaniu do schematu XML elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7c6dd7fc46dc8616eddc164bcf2ec801657cb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955141"
---
# <a name="projectitemfile-element"></a>ProjectItemFile — element
  Reprezentuje plik programu SharePoint, taki jak plik elementu funkcji, do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.

## <a name="syntax"></a>Składnia

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Typ
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**Element źródłowy**|Wymagany atrybut **xs: String** .<br /><br /> Nazwa pliku do wdrożenia z elementem projektu.|
|**Cel**|Opcjonalny atrybut **xs: String** .<br /><br /> Ścieżka, w której plik zostanie wdrożony w programie SharePoint względem folderu głównego wdrożenia. Folder główny wdrożenia jest określany przez typ wdrożenia określony przez atrybut **typu** . Jeśli nie określono atrybutu **Target** , plik zostanie wdrożony w folderze o nazwie określonej w atrybucie **Source** .<br /><br /> Aby uzyskać więcej informacji, zobacz opisy dotyczące **ścieżki wdrożenia** i właściwości **głównych wdrożenia** elementów projektu programu SharePoint w temacie [opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagany atrybut **xs: String** .<br /><br /> Typ wdrożenia pliku. Aby uzyskać więcej informacji o możliwych wartościach, zobacz opis właściwości **typ wdrożenia** elementów projektu programu SharePoint w temacie [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Pliki](../sharepoint/files-element.md)|Określa pliki do dołączenia do elementu projektu programu SharePoint po wdrożeniu w programie SharePoint.|

## <a name="remarks"></a>Uwagi
 Pliki programu SharePoint, które są zwykle przywoływane w elementach **ProjectItemFile —** , obejmują pliki elementów funkcji (*Elements.xml*), pliki schematów dla definicji list (*Schema.xml*) i pliki definicji części sieci Web dla składniki Web Part (*. WebPart*).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
