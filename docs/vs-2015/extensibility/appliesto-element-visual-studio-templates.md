---
title: AppliesTo — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6622c4774be5188aced606ce4b73dffe544aea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698939"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa opcjonalne wyrażenie porównywania z jedną lub kilkoma funkcjami (zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> ). Możliwości są udostępniane przez typy projektów za pośrednictwem hierarchii jako właściwości <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> . W ten sposób szablon może być współużytkowany przez wiele typów projektów, które mają wspólne odnośne funkcje.  
  
 Ten element jest opcjonalny. Plik szablonu może zawierać maksymalnie jedno jego wystąpienie. Element umożliwia jedynie potwierdzenie zgodności szablonu elementu z funkcjami aktualnie zaznaczonego aktywnego projektu. Nie można za jego pomocą ustawić niezgodności szablonu. Jeśli `AppliesTo` jest nieobecny lub wyrażenie nie powiodło się w, a `TemplateID` następnie `TemplateGroupID` jest używane w celu zastosowania szablonu, tak jak w poprzednich wersjach produktu.  
  
 Wprowadzono w Visual Studio 2013 Update 2. Aby odwołać się do odpowiedniej wersji, zobacz [odwołania do zestawów dostarczonych w Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<AppliesTo>  
  
## <a name="syntax"></a>Składnia  
  
```  
<AppliesTo>Capability1</AppliesTo>   
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Nadawanie szablonowi kategorii.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana. Tekst określa funkcje projektu.  
  
 Prawidłową składnię wyrażeń definiuje się następująco:  
  
- Wyrażenie możliwości, takie jak "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".  
  
- "&#124;" jest operatorem OR.  
  
- Znaki "&" i "+" są zarówno operatorami, jak i.  
  
- Znak „!” jest operatorem NIE.  
  
- Nawiasy wymuszają kolejność pierwszeństwa w ocenie.  
  
- Wyrażenie o wartości null lub puste jest interpretowane jako zgodność.  
  
- Możliwości projektu mogą być dowolnego znaku z wyjątkiem tych, które są zarezerwowane: "' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r  
  
## <a name="example"></a>Przykład  
 W przykładzie poniżej widać trzy różne szablony. `Template1` stosuje się do wszystkich typów projektów C# lub dowolnego innego typu projektu, który obsługuje tę `WindowsAppContainer` funkcję. `Template2` dotyczy wszystkich projektów w języku C# dowolnego rodzaju. `Template3` dotyczy projektów języka C#, które nie są `WindowsAppContainer` projektami.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
