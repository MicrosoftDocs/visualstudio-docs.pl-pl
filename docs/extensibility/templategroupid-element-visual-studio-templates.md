---
title: TemplateGroupID, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f710a73d8b9c4e31c8189d3322c518f20def5bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718654"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID — Element (szablony Visual Studio)
Określa rodzaj projektu, w którym będą wyświetlane szablony elementów. Ten element jest znaczący, gdy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) jest ustawiony na `false`. Gdy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) jest ustawiony na `true`, wówczas szablon elementu jest dostępny we wszystkich typach projektów.

 \<VSTemplate > \<TemplateData > \<TemplateGroupID >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst Określa identyfikator kategorii szablonów elementów.

## <a name="remarks"></a>Uwagi
 `TemplateGroupID` jest elementem.

 Wartość `TemplateGroupID` elementu jest używana wraz z rejestracją systemu projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<version number >* \Projects \\) do filtrowania szablonów, które pojawiają się w **Dodaj nowy element.** okno dialogowe.

|Wartość C++ wizualna|Znaczenie|
|------------------------|-------------|
|VC — natywny|Używane dla projektów natywnych. Również wartość domyślna, jeśli nie można określić typu projektu.|
|Zarządzany przez VC|Używane dla projektów zarządzanych (/CLR)|
|VC — Windows|Używane dla wszystkich projektów przeznaczonych dla platformy Windows (natywny/zarządzany/magazyn)|
|WinRT-Native-UAP|Używane w projektach ze sklepu Windows 10|
|CodeSharing — natywny|Używane na potrzeby projektów elementów współużytkowanych|
|WinRT-Native-6,3|Używane na potrzeby projektów magazynu Windows 8.1owego|
|WinRT-Native-Phone-6,3|Używane dla projektów Windows Phone 8,1|
|WinRT — natywny|Używane dla projektów sklepu Windows 8,0|
|VC — Android|Używane dla projektów systemu Android|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)