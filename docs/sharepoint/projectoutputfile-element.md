---
title: Projectoutputfile — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2673b22bf502f019f0a10361c9d0cef9d5ac1b8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816840"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile — element
  Reprezentuje dane wyjściowe w osobnym projekcie do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.

## <a name="syntax"></a>Składnia

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Typ
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**ProjectId**|Wymagane **xs:string** atrybutu.<br /><br /> Identyfikator GUID projektu zależnego, która generuje dane wyjściowe, które mają zostać uwzględnione. Odpowiada to **ProjectGuid** elementu w pliku projektu zależnego.|
|**ProjectPath**|Wymagane **xs:string** atrybutu.<br /><br /> Ścieżka względna, łącznie z nazwą pliku projektu, projektu zależnego, który generuje dane wyjściowe, które mają zostać uwzględnione. Ta ścieżka jest określana względem folderu głównego projektu programu SharePoint, który zawiera element projektu programu SharePoint.|
|**Docelowy**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Ścieżka, w którym ma zostać wdrożona na serwerze programu SharePoint względną wobec folderu głównego wdrożenia wyjściowy projektu zależnego. Folder główny wdrożenia jest określana przez typ wdrożenia, określony przez **typu** atrybutu.<br /><br /> Aby uzyskać więcej informacji, zobacz opisy **Ścieżka rozmieszczania** i **główny wdrożenia** właściwości programu SharePoint projektu elementów w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Typ wdrożenia do użycia dla danych wyjściowych projektu zależnego. Aby uzyskać więcej informacji na temat możliwych wartości, zobacz opis **typu wdrożenia** właściwości elementów projektu programu SharePoint w [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Pliki](../sharepoint/files-element.md)|Określa pliki do uwzględnienia przy użyciu elementu projektu programu SharePoint, gdy aplikacja jest wdrożona w programie SharePoint.|

## <a name="remarks"></a>Uwagi
 Użyj **projectoutputfile —** element, aby dołączyć dane wyjściowe projektu w ramach wdrożenia elementu projektu programu SharePoint. Możesz określić inny projekt lub tym samym projekcie, który zawiera element projektu. Aby uzyskać więcej informacji, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elementach

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
