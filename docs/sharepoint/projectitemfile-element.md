---
title: Projectitemfile — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562365"
---
# <a name="projectitemfile-element"></a>ProjectItemFile — element
  Reprezentuje plik programu SharePoint, takich jak funkcja element pliku do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.

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
|**Element źródłowy**|Wymagane **xs:string** atrybutu.<br /><br /> Nazwa pliku, aby wdrożyć elementu projektu.|
|**Docelowy**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Ścieżka, w którym zostanie wdrożony plik w programie SharePoint, względem folderu głównego wdrożenia. Folder główny wdrożenia jest określana przez typ wdrożenia, określony przez **typu** atrybutu. Jeśli **docelowej** atrybut nie zostanie określony, plik zostanie wdrożony w folderze o nazwie określonej w **źródła** atrybutu.<br /><br /> Aby uzyskać więcej informacji, zobacz opisy **Ścieżka rozmieszczania** i **główny wdrożenia** właściwości programu SharePoint projektu elementów w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Typ wdrożenia dla pliku. Aby uzyskać więcej informacji na temat możliwych wartości, zobacz opis **typu wdrożenia** właściwości elementów projektu programu SharePoint w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Pliki](../sharepoint/files-element.md)|Określa pliki do uwzględnienia przy użyciu elementu projektu programu SharePoint, gdy aplikacja jest wdrożona w programie SharePoint.|

## <a name="remarks"></a>Uwagi
 Pliki programu SharePoint, które zazwyczaj odwołuje się **projectitemfile —** elementy obejmują pliki element funkcji (*Elements.xml*), pliki schematów do definicje list (*Schema.xml*) i pliki definicji składnika Web Part dla składników Web Part (*.webpart*).

## <a name="element-information"></a>Informacje o elementach

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
