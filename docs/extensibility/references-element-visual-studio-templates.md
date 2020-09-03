---
title: References — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701613"
---
# <a name="references-element-visual-studio-templates"></a>References — element (szablony Visual Studio)
Grupuje odwołania zestawu, które szablon dodaje do projektów.

 \<VSTemplate> \<TemplateContent>
 \<References>

## <a name="syntax"></a>Składnia

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Odwołanie](../extensibility/reference-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa odwołanie do zestawu, które ma zostać dodane, gdy element zostanie dodany do projektu. Element musi mieć jeden lub więcej `Reference` elementów `References` .|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|

## <a name="remarks"></a>Uwagi
 `References` jest opcjonalnym elementem podrzędnym `TemplateContent` .

 `Reference`Elementy i `References` mogą być używane tylko w plikach *. vstemplate* , które mają `Type` wartość atrybutu `Item` .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje `TemplateContent` element szablonu elementu. Ten kod XML dodaje odwołania do zestawów *System.dll* i *System.Data.dll* .

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
