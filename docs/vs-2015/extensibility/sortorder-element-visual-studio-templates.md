---
title: SortOrder — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec82bd69257e32afed0ded6d1486324fc370860f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755619"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa wartość, która jest służy do rozmieszczania szablonu, wśród innych szablonów w ramach tej samej kategorii, wyświetlaną w albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Składnia  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer` Reprezentujący wartość kolejności sortowania.  
  
## <a name="remarks"></a>Uwagi  
 `SortOrder` element jest opcjonalny. Wartość domyślna to 100, a wszystkie wartości musi być wielokrotnością liczby 10.  
  
 `SortOrder` Element jest ignorowany dla szablonów utworzonych przez użytkownika. Wszystkie szablony utworzone przez użytkownika są sortowane alfabetycznie.  
  
 Szablony, które mają wartości kolejności sortowania niski pojawiają się w jednym **nowy projekt** lub **nowego elementu Dodawanie** okno dialogowe przed szablonów, które mają wartości kolejności sortowania wysoka.  
  
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
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 W tym przykładzie `SortOrder` element jest stosunkowo wysoka. Istnieje prawdopodobieństwo, że inne [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonów elementów będzie miał `SortOrder` wartości mniejszej niż `290` i pojawi się przed tego szablonu w **nowy element** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

