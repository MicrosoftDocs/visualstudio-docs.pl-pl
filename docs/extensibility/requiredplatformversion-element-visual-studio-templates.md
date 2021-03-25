---
description: Określa minimalną wersję systemu operacyjnego wymaganą przez szablon projektu do poprawnego działania.
title: RequiredPlatformVersion, element (szablony Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b1d7e3b8cc67f839977eb1e53d80731e59c064e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068430"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion, element (szablony Visual Studio)

Określa minimalną wersję systemu operacyjnego wymaganą przez szablon projektu do poprawnego działania. Ten element jest używany do szablonów projektów tworzących [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje.

 `RequiredPlatformVersion`Wartość jest porównywana bezpośrednio z wersją systemu operacyjnego. Jeśli `RequiredPlatformVersion` jest wyższa niż wersja systemu operacyjnego, szablon nie jest wyświetlany w oknie dialogowym **Nowy projekt** . Aby określić szablon dla [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub wyższy, ustaw wartość `RequiredPlatformVersion` 6.2.0. Aby określić szablon dla [!INCLUDE[win81](../debugger/includes/win81_md.md)] lub wyższy, ustaw wartość `RequiredPlatformVersion` 6.3.0.

 Szablony określające wartość `RequiredPlatformVersion` = 8 są zgodne z poprzednimi [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] szablonami klientów.

 VSTemplate TemplateData.... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Składnia

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 Brak.

### <a name="attributes"></a>Atrybuty

 Brak.

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Określa platformę, do której należy szablon projektu.|

## <a name="text-value"></a>Wartość tekstowa

 Wartość tekstowa jest wymagana.

## <a name="remarks"></a>Uwagi

 Ten tekst Określa minimalną wersję systemu operacyjnego wymaganą przez szablon.

## <a name="example"></a>Przykład

 Ten przykład określa, że szablon projektu jest obiektem docelowym [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszym.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też

- [TargetPlatformName, element (szablony Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
