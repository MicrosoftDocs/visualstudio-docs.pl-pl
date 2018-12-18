---
title: Odwołania — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6f0d4dc2d73d62c9a223d92f353093206e2aab1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725930"
---
# <a name="reference-element-visual-studio-templates"></a>Reference — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa odwołanie do zestawu do dodania, gdy element zostanie dodany do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Odwołania >  
 \<Odwołanie >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa informacje o zestawie używany w tym szablonie, aby dodać odwołanie do tego zestawu do projektów. Musi zawierać jeden `Assembly` elementu w każdym `Reference` elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Odwołania](../extensibility/references-element-visual-studio-templates.md)|Grupuje odwołania do zestawów, które szablon dodaje się do projektów.|  
  
## <a name="remarks"></a>Uwagi  
 `Reference` jest wymaganym elementem podrzędnym elementu `References`.  
  
 `Reference` i `References` elementów należy używać tylko w plikach .vstemplate, które mają `Type` wartość atrybutu `Item`.  
  
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

