---
title: CustomParameters —, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie CustomParameters — i sposobie grupowania przez niego parametrów niestandardowych, które mają być przenoszone do Kreatora szablonów, gdy Kreator przejdzie do parametrów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927135"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters —, element (szablony Visual Studio)
Grupuje parametry niestandardowe, które mają być przenoszone do Kreatora szablonów, gdy Kreator przejdzie do parametrów.

## <a name="syntax"></a>Składnia

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Zawiera niestandardową nazwę i wartość parametru, która ma być używana podczas tworzenia projektu lub elementu z szablonu. Element może mieć zero lub więcej `CustomParameter` elementów `CustomParameters` .|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać kilku parametrów niestandardowych w szablonie. Gdy projekt lub element jest tworzony na podstawie szablonu o następujących parametrach niestandardowych, wszystkie wystąpienia `$color1$` i `$color2$` w plikach szablonów zostaną zastąpione `Red` `Blue` odpowiednio i.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Zobacz też
- [CustomParameter, element (szablony Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
