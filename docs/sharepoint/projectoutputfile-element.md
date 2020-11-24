---
title: ProjectOutputFile — — element | Microsoft Docs
description: Pobierz informacje referencyjne na temat elementu ProjectOutputFile —, który reprezentuje dane wyjściowe oddzielnego projektu w odwołaniu do schematu XML elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ffe6f95bdfd7795c837aaaa25ec7ef2a35a7ae76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442031"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile — element
  Przedstawia dane wyjściowe oddzielnego projektu do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.

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
|**Identyfikator projectID**|Wymagany atrybut **xs: String** .<br /><br /> Identyfikator GUID zależnego projektu, który zawiera dane wyjściowe, które mają zostać uwzględnione. Odnosi się to do elementu **ProjectGuid** w pliku projektu zależnego.|
|**ProjectPath**|Wymagany atrybut **xs: String** .<br /><br /> Ścieżka względna, w tym nazwa pliku projektu, zależnego projektu zawierającego dane wyjściowe, które mają zostać uwzględnione. Ta ścieżka jest określana względem folderu głównego projektu programu SharePoint, który zawiera element projektu programu SharePoint.|
|**Obiektów**|Opcjonalny atrybut **xs: String** .<br /><br /> Ścieżka, w której zależne dane wyjściowe projektu mają zostać wdrożone na serwerze programu SharePoint, względem folderu głównego wdrożenia. Folder główny wdrożenia jest określany przez typ wdrożenia określony przez atrybut **typu** .<br /><br /> Aby uzyskać więcej informacji, zobacz opisy dotyczące **ścieżki wdrożenia** i właściwości **głównych wdrożenia** elementów projektu programu SharePoint w temacie [opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Typ**|Wymagany atrybut **xs: String** .<br /><br /> Typ wdrożenia do użycia dla danych wyjściowych projektu zależnego. Aby uzyskać więcej informacji o możliwych wartościach, zobacz opis właściwości **typ wdrożenia** elementów projektu programu SharePoint w temacie [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Files](../sharepoint/files-element.md)|Określa pliki do dołączenia do elementu projektu programu SharePoint po wdrożeniu w programie SharePoint.|

## <a name="remarks"></a>Uwagi
 Użyj elementu **ProjectOutputFile —** , aby uwzględnić dane wyjściowe projektu we wdrożeniu elementu projektu programu SharePoint. Możesz określić inny projekt lub ten sam projekt, który zawiera element projektu. Aby uzyskać więcej informacji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Obszaru**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
