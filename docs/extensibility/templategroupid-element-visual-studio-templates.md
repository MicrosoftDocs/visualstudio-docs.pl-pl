---
title: Element TemplateGroupID (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699075"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID — Element (szablony Visual Studio)
Określa, w jakim projekcie będą wyświetlane szablony elementów. Ten element jest istotny, gdy [showbydefault (szablony programu Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) jest ustawiona na `false`. Gdy [ShowByDefault (Szablony programu Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) jest ustawiona na `true`, a następnie szablon elementu jest dostępny we wszystkich typach projektu.

 \<>> \< \<templategroupID> TemplateData>

## <a name="syntax"></a>Składnia

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst określa identyfikator kategorii szablonów elementów.

## <a name="remarks"></a>Uwagi
 `TemplateGroupID`jest elementem.

 Wartość elementu `TemplateGroupID` jest używana wraz z rejestracją systemu projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numer *wersji\\>\Projekty ) do filtrowania szablonów wyświetlanych w oknie dialogowym **Dodawanie nowego elementu.**

|Wizualna wartość C++|Znaczenie|
|------------------------|-------------|
|Natywny vc|Używany dla projektów natywnych. Również wartość domyślna, jeśli nie można określić typu projektu.|
|Zarządzanie vc|Używane w przypadku projektów zarządzanych (/clr)|
|VC-Windows|Używane dla wszystkich projektów przeznaczonych na platformę systemu Windows (natywne/zarządzane/sklepowe)|
|WinRT-Native-UAP|Używane w projektach sklepu windows 10|
|Natywne udostępnianie kodu|Używane dla projektów elementów udostępnionych|
|WinRT-Native-6.3|Używane w projektach sklepu windows 8.1|
|WinRT-Native-Phone-6.3|Używane w projektach systemu Windows Phone 8.1|
|WinRT-Native|Używane w projektach Sklepu Windows 8.0|
|VC-Android|Używane w projektach systemu Android|

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
