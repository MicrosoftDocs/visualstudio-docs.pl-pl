---
title: Assembly — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40bb0b99bfe22c7842296c2fbaa2b868ca1ef259
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802034"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o zestawie używany w tym szablonie, aby dodać odwołanie do tego zestawu do projektów.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Odwołania >  
 \<Odwołanie >  
 \<Zestaw >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Assembly> AssemblyName </Assembly>  
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
|[Dokumentacja](../extensibility/reference-element-visual-studio-templates.md)|Określa odwołanie do zestawu do dodania, gdy element zostanie dodany do projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ten tekst Określa zestaw do dodania do projektu przy tworzeniu wystąpienia szablonu elementu. Ta nazwa zestawu musi być określona w jednym z następujących sposobów:  
  
-   Jako nazwę pełnego zestawu. Na przykład:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Jako odwołanie do zwykłego tekstu. Na przykład:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Uwagi  
 `Assembly` jest wymaganym elementem podrzędnym elementu `Reference`.  
  
 `Reference`, `References,` i `Assembly` elementów należy używać tylko w plikach .vstemplate, które mają `Type` wartość atrybutu `Item`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `TemplateContent` element szablon elementu. Poniższy kod XML dodaje odwołania do zestawów: System.dll i System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

