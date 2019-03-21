---
title: SafeControls — Element | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ce943416bba84c46ce7b709c3d2bdb6ddb3e4447
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322496"
---
# <a name="safecontrols-element"></a>SafeControls — element
  Kolekcja formantów ASPX i składniki Web Part, które zostały oznaczone jako bezpieczne dla każdego użytkownika, dostęp do w dowolnej strony ASPX w witrynie programu SharePoint.

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
|[SafeControl](../sharepoint/safecontrol-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kontrolki ASPX lub składnik Web Part, który jest wyznaczony jako bezpieczna opcja dla każdemu użytkownikowi dostęp do strony ASPX w witrynie programu SharePoint.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint. Ten element wymaganego głównego elementu z *spdata* pliku.|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji na temat bezpiecznych kontrolek, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
