---
title: MaxFrameworkVersion, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5201d42bddb02eade61546ee61ae99283347082
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778179"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa maksymalną wersję programu .NET Framework, która jest wymagana przez szablon. Określa, czy szablon jest wyświetlany w **szablony** części **Dodaj nowy projekt** okno dialogowe, na podstawie wartości, który wybrano w **wersji platformy docelowej** pole **Dodaj nowy projekt** okno dialogowe.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Składnia  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 Tekst musi być najwyższy numer wersji systemu .NET Framework, który jest dozwolony przez szablon.  
  
## <a name="remarks"></a>Uwagi  
 `MaxFrameworkVersion` element jest opcjonalny. Element w `TemplateData` sekcji w pliku .vstemplate działa jako filtr dla **szablony** części **Dodaj nowy projekt** okno dialogowe. Tylko szablony, których wymagania dotyczące systemu .NET Framework są mniej niż `MaxFrameworkVersion` wartości elementu pojawi się na podstawie wartości, który wybrano w **wersji platformy docelowej** pole **Dodaj nowy projekt**okno dialogowe. `MaxFrameworkVersion` Element należy pominąć, chyba że jest to wymagane, tak aby nie mogą przypadkowo spowodować szablony będą wyświetlane, gdy są one używane przy użyciu nowszych wersji programu .NET Framework.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych dla standardowego [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonu klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 W tym przykładzie maksymalna wersja systemu .NET Framework, która jest wymagana przez szablon, reprezentowane przez `MaxFrameworkVersion`, to 3.5. Powyższego szablonu będą wyświetlane tylko po wybraniu 3.0 lub 3.5 w **wersji platformy docelowej** pole w **Dodaj nowy projekt** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

