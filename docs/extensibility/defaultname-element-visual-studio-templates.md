---
title: DefaultName, element (szablony Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712303"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName, element (szablony Visual Studio)
Określa nazwę, która zostanie wygenerowana przez system projektu programu Visual Studio dla projektu lub elementu podczas jego tworzenia.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst Określa domyślną nazwę projektu lub elementu.

## <a name="remarks"></a>Uwagi
 `DefaultName` jest elementem opcjonalnym.

 W przypadku projektów ten element określa nazwę katalogu, w którym jest przechowywany projekt na dysku. Dla elementów określa nazwę pliku źródłowego.

 Podczas tworzenia projektu lub elementu można zmodyfikować nazwę domyślną przy użyciu opcji **Nazwa** , która jest dostępna w oknie dialogowym **Nowy projekt** lub okno dialogowe **Dodaj nowy element** .

 Jeśli nie chcesz, aby system projektu generował nazwę domyślną dla projektu lub elementu, a następnie ustaw element [ProvideDefaultName —](../extensibility/providedefaultname-element-visual-studio-templates.md) na `False` .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla szablonu elementu standardowego dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.

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
