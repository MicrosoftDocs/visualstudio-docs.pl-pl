---
title: SafeControls — — element | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e840f0040cf94fea408615525358580d207f07c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547904"
---
# <a name="safecontrols-element"></a>SafeControls — element
  Kolekcja formantów ASPX i składniki Web Part, które są wyznaczeni jako bezpieczne dla każdego użytkownika, który ma dostęp do dowolnej strony ASPX w witrynie programu SharePoint.

## <a name="syntax"></a>Składnia

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kontrolkę ASPX lub składnik Web Part, który jest oznaczony jako bezpieczny dla każdego użytkownika, aby mógł uzyskać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element jest wymaganym elementem głównym pliku *. spdata* .|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji o bezpiecznych kontrolkach, zobacz temat [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
