---
title: CustomParameter, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbf76edec01cce52768f36dc534d50b580b64230
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322276"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter, element (szablony Visual Studio)
Zawiera nazwę niestandardowego parametru i wartości do użycia podczas projektu lub elementu jest tworzone na podstawie szablonu.

## <a name="syntax"></a>Składnia

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagana. Nazwa parametru. Format parametrów jest $*nazwa*$.|
|`Value`|Wymagana. Wartość zastąpienia dla parametru.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Customparameters —](../extensibility/customparameters-element-visual-studio-templates.md)|Grupy niestandardowe parametry, które mają być przekazane do Kreatora szablonów, gdy Kreator przeprowadza zamiany parametru.|

## <a name="remarks"></a>Uwagi
 Gdy szablon zawiera `CustomParameter` elementy, każde wystąpienie `Name` atrybutu zostaje zastąpiona opcją `Value` atrybutu w utworzone pliki projektu lub elementu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak korzystać z kilku niestandardowych parametrów w szablonie. Podczas tworzenia projektu lub elementu za pomocą następujących parametrów niestandardowych, wszystkie wystąpienia szablonu `$color1$` i `$color2$` w szablonie zostanie zastąpiona pliki `Red` i `Blue`, odpowiednio.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Zobacz także
- [Customparameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)