---
title: MaxFrameworkVersion, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194327"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa maksymalną wersję .NET Framework wymaganą przez szablon. Określa, czy szablon jest wyświetlany w sekcji **Szablony** okna dialogowego **Dodaj nowy projekt** na podstawie wartości wybranej w polu **docelowa wersja struktury** okna dialogowego **Dodawanie nowego projektu** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób jego wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być najwyższym numerem wersji .NET Framework, który jest dozwolony przez szablon.  
  
## <a name="remarks"></a>Uwagi  
 `MaxFrameworkVersion` jest elementem opcjonalnym. Element w `TemplateData` sekcji pliku. vstemplate działa jako filtr dla sekcji **Szablony** okna dialogowego **Dodaj nowy projekt** . Tylko szablony, których wymagania .NET Framework są mniejsze niż `MaxFrameworkVersion` wartości elementów, będą wyświetlane na podstawie wartości wybranej w polu **docelowa wersja struktury** okna dialogowego **Dodaj nowy projekt** . `MaxFrameworkVersion`Element powinien być pominięty, chyba że jest to wymagane, więc nie powoduje przypadkowego wyświetlenia szablonów, gdy są one używane z nowszymi wersjami .NET Framework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje metadane dla standardowego [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonu klasy.  
  
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
  
 W tym przykładzie Maksymalna wersja .NET Framework, która jest wymagana przez szablon, reprezentowana przez `MaxFrameworkVersion` , to 3,5. Powyższy szablon zostanie wyświetlony tylko w przypadku wybrania opcji 3,0 lub 3,5 w polu **wersja platformy docelowej** w oknie dialogowym **Dodawanie nowego projektu** .  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
