---
title: SDKReference, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da11d9e01802bff8162b2767444c7a1d225200a0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338478"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference, element (szablony Visual Studio)
Określa, że szablon elementu używa odwołanie do zestawu SDK.

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
|[Dokumentacja](../extensibility/reference-element-visual-studio-templates.md)|Określa odwołanie do zestawu do dodania, gdy element zostanie dodany do projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

## <a name="remarks"></a>Uwagi
 Ten tekst Określa dokumentacja zestawu SDK, aby dodać do projektu przy tworzeniu wystąpienia szablonu elementu.

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