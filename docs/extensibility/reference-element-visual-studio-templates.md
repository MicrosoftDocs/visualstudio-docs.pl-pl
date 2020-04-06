---
title: Element referencyjny (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701629"
---
# <a name="reference-element-visual-studio-templates"></a>Element odwołania (szablony programu Visual Studio)
Określa odwołanie do złożenia, które należy dodać po dodaniu elementu do projektu.

 \<> \<odwołania do>> \< \<>>

## <a name="syntax"></a>Składnia

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Zestaw](../extensibility/assembly-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa informacje o zestawie, którego szablon używa do dodania odwołania tego zestawu do projektów. Musi istnieć `Assembly` jeden `Reference` element w każdym elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Dokumentacja](../extensibility/references-element-visual-studio-templates.md)|Grupuje odwołania do zestawu, które szablon dodaje do projektów.|

## <a name="remarks"></a>Uwagi
 `Reference`jest wymaganym elementem `References`podrzędnym .

 Elementy `Reference` `References` i elementy mogą być używane tylko w plikach `Type` *vstemplate,* które mają wartość atrybutu `Item`.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje `TemplateContent` element szablonu elementu. Ten kod XML dodaje odwołania do zestawów *System.dll* i *System.Data.dll.*

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
