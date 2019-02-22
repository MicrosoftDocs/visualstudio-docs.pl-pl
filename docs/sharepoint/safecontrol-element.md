---
title: SafeControl — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80606297c61d59d5670473755e667c6d3c538de
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601268"
---
# <a name="safecontrol-element"></a>SafeControl — element
  Reprezentuje kontrolki ASPX lub składnik Web Part, który jest wyznaczony jako bezpieczna opcja dla każdemu użytkownikowi dostęp do strony ASPX w witrynie programu SharePoint.

## <a name="syntax"></a>Składnia

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**Assembly**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Nazwa zestawu, w którym zdefiniowano kontroli ASPX lub składnik Web Part. Domyślnie ten atrybut używa **$SharePoint.Project.AssemblyFullName$** parametr do zastąpienia dla nazwy zestawu. Aby uzyskać więcej informacji, zobacz [parametrów zastępowalnych](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|Opcjonalnie **xs:boolean** atrybutu.<br /><br /> Określa, czy kontrolka ASPX lub składnik Web Part jest bezpieczne dla niezaufanch użytkowników do uzyskania dostępu.|
|**IsSafeAgainstScript**|Opcjonalnie **xs:boolean** atrybutu.<br /><br /> Określa, czy niezaufanym użytkownikom można wyświetlać lub edytować właściwości kontrolki ASPX lub składnik Web Part.|
|**Nazwa**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Nazwa tego wpisu bezpiecznej kontrolki w kolekcji.|
|**Namespace**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Przestrzeń nazw formantu ASPX lub składnik Web Part.|
|**TypeName**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Nazwa typu formantu ASPX lub składnik Web Part.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję formantów ASPX i składniki Web Part, które zostały oznaczone jako bezpieczne dla każdego użytkownika, dostęp do w dowolnej strony ASPX w witrynie programu SharePoint.|

## <a name="remarks"></a>Uwagi
 Aby uzyskać więcej informacji na temat bezpiecznych kontrolek, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informacje o elementach

|||
|-|-|
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
