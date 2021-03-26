---
title: SDKReference, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu SDKReference i sposobu, w jaki określa, że szablon elementu używa odwołania do zestawu SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ea070cf466782a1da09e1ba48d08a6965fd041a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063711"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference, element (szablony Visual Studio)
Określa, że szablon elementu używa odwołania do zestawu SDK.

## <a name="syntax"></a>Składnia

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Odwołanie](../extensibility/reference-element-visual-studio-templates.md)|Określa odwołanie do zestawu, które ma zostać dodane, gdy element zostanie dodany do projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

## <a name="remarks"></a>Uwagi
 Ten tekst określa odwołanie do zestawu SDK, które ma zostać dodane do projektu po utworzeniu wystąpienia szablonu elementu.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>Zobacz też
- [References, element (szablony Visual Studio)](../extensibility/references-element-visual-studio-templates.md)
- [Reference, element (szablony Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
