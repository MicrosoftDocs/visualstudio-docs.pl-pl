---
title: Element DefaultName (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712303"
---
# <a name="defaultname-element-visual-studio-templates"></a>Element DefaultName (szablony programu Visual Studio)
Określa nazwę, którą system projektu visual studio wygeneruje dla projektu lub elementu podczas jego tworzenia.

 \<> \<templatedata> \<DefaultName>

## <a name="syntax"></a>Składnia

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Ten tekst określa domyślną nazwę projektu lub elementu.

## <a name="remarks"></a>Uwagi
 `DefaultName`jest elementem opcjonalnym.

 W przypadku projektów ten element określa nazwę katalogu, który przechowuje projekt na dysku. W przypadku elementów określa nazwę pliku źródłowego.

 Podczas tworzenia projektu lub elementu można zmodyfikować nazwę domyślną za pomocą opcji **Nazwa,** która jest dostępna w oknie dialogowym **Nowy projekt** lub Oknie Dialogowym Dodawanie **nowego elementu.**

 Jeśli system projektu nie ma generować domyślnej nazwy projektu lub elementu, należy ustawić element `False` [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) na .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu elementu standardowego dla klasy.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
