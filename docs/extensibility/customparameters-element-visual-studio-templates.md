---
title: Element CustomParameters (szablony programu Visual Studio) | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739412"
---
# <a name="customparameters-element-visual-studio-templates"></a>Element CustomParameters (szablony programu Visual Studio)
Grupuje parametry niestandardowe, które mają być przekazywane do kreatora szablonów, gdy kreator wykonuje zastępowanie parametrów.

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
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Zawiera niestandardową nazwę parametru i wartość do użycia podczas tworzenia projektu lub elementu na podstawie szablonu. Może istnieć zero `CustomParameter` lub `CustomParameters` więcej elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, jak używać kilku parametrów niestandardowych w szablonie. Gdy projekt lub element jest tworzony na podstawie szablonu z `$color1$` `$color2$` następującymi parametrami niestandardowymi, wszystkie wystąpienia i w plikach szablonów zostaną zastąpione `Red` odpowiednio i `Blue`, odpowiednio.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Zobacz też
- [Element CustomParameter (szablony programu Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
