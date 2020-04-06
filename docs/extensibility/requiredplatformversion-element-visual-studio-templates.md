---
title: Wymagany element platformformversion (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701495"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Wymagany element PlatformformVersion (szablony programu Visual Studio)
Określa minimalną wersję systemu operacyjnego, która wymaga prawidłowego działania szablonu projektu. Ten element jest używany do szablonów projektów, które tworzą [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje.

 Wartość `RequiredPlatformVersion` jest porównywana bezpośrednio z wersją systemu operacyjnego. Jeśli `RequiredPlatformVersion` jest wyższa niż wersja systemu operacyjnego, szablon nie pojawia się w oknie dialogowym **Nowy projekt.** Aby określić [!INCLUDE[win8](../debugger/includes/win8_md.md)] szablon dla `RequiredPlatformVersion` lub wyższy, należy ustawić na 6.2.0. Aby określić [!INCLUDE[win81](../debugger/includes/win81_md.md)] szablon dla `RequiredPlatformVersion` lub wyższy, należy ustawić na 6.3.0.

 Szablony określające `RequiredPlatformVersion`=8 są [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] zgodne z poprzednimi szablonami klientów.

 VsTemplate TemplateData ..... Wymagana wersja na platformie targetplatformName

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
|[Nazwa templateplatformname](../extensibility/templatedata-element-visual-studio-templates.md)|Określa platformę, na którą kieruje szablon projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

## <a name="remarks"></a>Uwagi
 Ten tekst określa minimalną wersję systemu operacyjnego wymaganą przez szablon.

## <a name="example"></a>Przykład
 W tym przykładzie określono, [!INCLUDE[win8](../debugger/includes/win8_md.md)] że cele szablonu projektu lub później.

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
- [Element TargetPlatformName (szablony programu Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
