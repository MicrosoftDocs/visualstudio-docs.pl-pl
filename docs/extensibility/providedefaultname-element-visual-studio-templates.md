---
title: Providedefaultname — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54f55731cd76fdeb1090eacfa42d3433ec5b323b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010028"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Providedefaultname — element (szablony Visual Studio)
Określa, czy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] system projektu spowoduje wygenerowanie domyślna nazwa szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` lub `false`, wskazującą, czy mają być Generowanie domyślna nazwa szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `ProvideDefaultName` element jest opcjonalny. Wartość domyślna to `true`.  
  
 Jeśli `ProvideDefaultName` element jest `false`, **nazwa** pola **Dodaj nowy element** i **nowy projekt** okna dialogowe zawierają wartość `<Enter_name>`.  
  
 Użyj [defaultname —](../extensibility/defaultname-element-visual-studio-templates.md) element, aby określić domyślną nazwę projektu lub elementu w **Dodaj nowy element** i **nowy projekt** okien dialogowych. Gdy wartość `ProvideDefaultName` element jest `true`, pominięcie `DefaultName` elementu dla projektów wypełni okno dialogowe z nazwą tego szablonu, oznacza to, że wartość z [nazwa](../extensibility/name-element-visual-studio-templates.md) elementu.
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia przykład `ProvideDefaultName` elementu `false`.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
