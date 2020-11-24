---
title: SafeControls — — element | Microsoft Docs
description: Uzyskaj informacje na temat elementu SafeControls —, który zawiera kolekcję kontrolek ASPX lub składników Web Part oznaczonych jako bezpieczne dla dostępu na stronie ASPX witryny programu SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c3423d1b6efd106ef7f947bd8573dcd1aa548a66
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440678"
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
|**Obszaru**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
