---
title: Supportsmasterpage — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba409c831dd508dae796bca1ea2837674459690d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316683"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage — Element (szablony Visual Studio)
Określa, czy nie **wybierz stronę wzorcową** pole wyboru jest włączona na **Dodaj nowy element** okno dialogowe.

 \<VSTemplate> \<TemplateData> \<SupportsMasterPage>

## <a name="syntax"></a>Składnia

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Określa dane, która klasyfikuje szablon i definiuje sposób wyświetlania w **nowy projekt** lub **nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być albo `true` lub `false`oznaczający czy **wybierz stronę wzorcową** pole wyboru jest włączona na **Dodaj nowy element** okno dialogowe.

## <a name="remarks"></a>Uwagi
 `SupportsMasterPage` element jest opcjonalny. Wartość domyślna to `false`.

 `SupportsMasterPage` Element jest dostępny tylko dla szablonów elementów sieci Web.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadanych dla projektu sieci Web, który zawiera obsługę dla strony wzorcowej.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)