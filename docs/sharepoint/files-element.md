---
title: Pliki Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e27e3192ec0d9a312c3cfc0a3521daf534c68e9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922315"
---
# <a name="files-element"></a>Element Pliki
  Określa pliki do wdrożenia przy użyciu elementu projektu programu SharePoint, takich jak funkcja elementu pliki i dane wyjściowe projektów zależnych programu SharePoint.  
  
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
|[Projectitemfile —](../sharepoint/projectitemfile-element.md)|Opcjonalnie **ProjectItemFileType** elementu.<br /><br /> Reprezentuje plik programu SharePoint, takich jak funkcja element pliku do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.|  
|[Projectoutputfile —](../sharepoint/projectoutputfile-element.md)|Opcjonalnie **ProjectOutputFileType** elementu.<br /><br /> Reprezentuje dane wyjściowe projektu do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne
  
|Element|Opis|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaganego głównego elementu z `.spdata` pliku.|  
  
## <a name="element-information"></a>Informacje o elementach
  
|||  
|-|-|  
|**Namespace**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Plik walidacji**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz także
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
