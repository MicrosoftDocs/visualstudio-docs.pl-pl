---
title: TemplateId — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1f992d9f501b965fc300b97613a3d6f3bd4e35d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680584"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID — Element (szablony Visual Studio)
Określa identyfikator szablonu elementu, który dzieli się na grupę szablonów elementów przez [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) elementu.

 \<VSTemplate> \<TemplateData> \<TemplateID>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 A `string` reprezentujący identyfikator szablonu elementu, który dzieli się na grupę szablonów elementów przez `TemplateGroupID` elementu.

## <a name="remarks"></a>Uwagi
 `TemplateID` element jest opcjonalny.

 Jeżeli pominięto plik .vstemplate `TemplateID` elementu, a następnie [nazwa](../extensibility/name-element-visual-studio-templates.md) element jest używany jako identyfikator szablonu.

 Wartość `TemplateID` element jest używany razem z rejestracji systemu projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) do filtru szablonów, które pojawiają się w **Dodaj nowy element** okno dialogowe.

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)