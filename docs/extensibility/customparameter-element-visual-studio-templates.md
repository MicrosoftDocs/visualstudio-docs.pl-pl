---
title: CustomParameter, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu CustomParameter i sposobu, w jaki zawiera niestandardową nazwę i wartość parametru, która ma być używana podczas tworzenia projektu lub elementu na podstawie szablonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c118bbc85064beb10b99641f0803af7af12d56
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671952"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter, element (szablony Visual Studio)
Zawiera niestandardową nazwę i wartość parametru, która ma być używana podczas tworzenia projektu lub elementu z szablonu.

## <a name="syntax"></a>Składnia

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagane. Nazwa parametru. Format parametrów to $*name*$.|
|`Value`|Wymagane. Wartość zastępcza parametru.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Grupuje parametry niestandardowe, które mają być przenoszone do Kreatora szablonów, gdy Kreator przejdzie do parametrów.|

## <a name="remarks"></a>Uwagi
 Gdy szablon zawiera `CustomParameter` elementy, każde wystąpienie `Name` atrybutu jest zastępowane `Value` atrybutem w utworzonym pliku projektu lub elementu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać kilku parametrów niestandardowych w szablonie. Gdy projekt lub element jest tworzony na podstawie szablonu o następujących parametrach niestandardowych, wszystkie wystąpienia `$color1$` i `$color2$` w plikach szablonów zostaną zastąpione `Red` `Blue` odpowiednio i.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Zobacz także
- [CustomParameters —, element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
