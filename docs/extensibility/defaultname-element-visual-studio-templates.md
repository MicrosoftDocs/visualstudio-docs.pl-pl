---
title: Defaultname — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dbb720bf04c36b2d9f018be5418a25088e259f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348151"
---
# <a name="defaultname-element-visual-studio-templates"></a>Defaultname — element (szablony Visual Studio)
Określa nazwę, który zostanie wygenerowany przez system projektu programu Visual Studio dla projektu lub elementu, podczas jego tworzenia.

 \<VSTemplate > \<TemplateData > \<defaultname — >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst Określa domyślną nazwę projektu lub elementu.

## <a name="remarks"></a>Uwagi
 `DefaultName` element jest opcjonalny.

 W przypadku projektów ten element Określa nazwę katalogu, który przechowuje projektu na dysku. Dla elementów Określa nazwę pliku w pliku źródłowym.

 Podczas tworzenia projektu lub elementu, można modyfikować przy użyciu nazwy domyślnej **nazwa** opcja, która jest dostępna z poziomu **nowy projekt** okno dialogowe lub **Dodaj nowy element** okno dialogowe.

 Jeśli użytkownik nie chce, aby system projektu ma generować domyślna nazwa projektu lub elementu, wartość [providedefaultname —](../extensibility/providedefaultname-element-visual-studio-templates.md) elementu `False`.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metadanych dla szablonu elementu standardowego dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)