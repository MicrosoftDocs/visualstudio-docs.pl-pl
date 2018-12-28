---
title: Odwołania — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c5f7d82918924ddda4c70d6d86573fae9c58681
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561033"
---
# <a name="reference-element-visual-studio-templates"></a>Reference — element (szablony Visual Studio)
Określa odwołanie do zestawu do dodania, gdy element zostanie dodany do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Odwołania >  
 \<Odwołanie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
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
  
 `Reference` i `References` elementów należy używać tylko w *.vstemplate* plików, które mają `Type` wartość atrybutu `Item`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `TemplateContent` element szablon elementu. Poniższy kod XML dodaje odwołania do *System.dll* i *System.Data.dll* zestawów.  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
