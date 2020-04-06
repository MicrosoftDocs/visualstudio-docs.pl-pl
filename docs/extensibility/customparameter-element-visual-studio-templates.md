---
title: Element CustomParameter (szablony programu Visual Studio) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739428"
---
# <a name="customparameter-element-visual-studio-templates"></a>Element CustomParameter (szablony programu Visual Studio)
Zawiera niestandardową nazwę parametru i wartość do użycia podczas tworzenia projektu lub elementu na podstawie szablonu.

## <a name="syntax"></a>Składnia

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagany. Nazwa parametru. Format parametrów to $*name*$.|
|`Value`|Wymagany. Wartość zastępcza parametru.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Grupuje parametry niestandardowe, które mają być przekazywane do kreatora szablonów, gdy kreator wykonuje zastępowanie parametrów.|

## <a name="remarks"></a>Uwagi
 Gdy szablon `CustomParameter` zawiera elementy, `Name` każde wystąpienie atrybutu jest zastępowany atrybutem `Value` w utworzonych plikach projektu lub elementu.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, jak używać kilku parametrów niestandardowych w szablonie. Gdy projekt lub element jest tworzony na podstawie szablonu z `$color1$` `$color2$` następującymi parametrami niestandardowymi, wszystkie wystąpienia i w plikach szablonów zostaną zastąpione `Red` odpowiednio i `Blue`, odpowiednio.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Zobacz też
- [Element CustomParameters (szablony programu Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
