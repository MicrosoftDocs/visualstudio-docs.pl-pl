---
title: Element ProvideDefaultName (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701715"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Element ProvideDefaultName (szablony programu Visual Studio)
Określa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] czy system projektu wygeneruje domyślną nazwę szablonu w oknie dialogowym **Dodawanie nowego elementu** lub nowego **projektu.**

 \<>> \<TemplateData \<> ProvideDefaultName

## <a name="syntax"></a>Składnia

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`, wskazując, czy wygenerować domyślną nazwę szablonu w oknie dialogowym **Dodawanie nowego elementu** lub nowego **projektu.**

## <a name="remarks"></a>Uwagi
 `ProvideDefaultName`jest elementem opcjonalnym. Wartością domyślną jest `true`.

 Jeśli `ProvideDefaultName` element `false`jest , pola **Nazwa** okna dialogowego **Dodaj nowy** `<Enter_name>`element i Nowy **projekt** zawierają wartość .

 Użyj elementu [DefaultName,](../extensibility/defaultname-element-visual-studio-templates.md) aby określić domyślną nazwę projektu lub elementu w oknach dialogowych **Dodawanie nowego elementu** i nowego **projektu.** Gdy `ProvideDefaultName` wartość elementu jest `true`, pominięcie `DefaultName` elementu dla projektów wypełnia okno dialogowe z nazwą szablonu, czyli wartość z [Name](../extensibility/name-element-visual-studio-templates.md) elementu.

## <a name="example"></a>Przykład
 Poniższy przykład kodu `ProvideDefaultName` ustawia `false`element na .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
