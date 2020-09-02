---
title: TemplateID, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699058"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID — Element (szablony Visual Studio)
Określa identyfikator szablonu elementu, który jest kategoryzowany w grupie szablonów elementów przez element [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Składnia

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 `string`Reprezentuje identyfikator szablonu elementu, który jest kategoryzowany w grupie szablonów elementów według `TemplateGroupID` elementu.

## <a name="remarks"></a>Uwagi
 `TemplateID` jest elementem opcjonalnym.

 Jeśli plik. vstemplate pomija `TemplateID` element, wówczas element [name](../extensibility/name-element-visual-studio-templates.md) jest używany jako identyfikator szablonu.

 Wartość `TemplateID` elementu jest używana wraz z rejestracją systemu projektu (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\Projects \\ ) do filtrowania szablonów, które pojawiają się w oknie dialogowym **Dodaj nowy element** .

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
