---
title: Assembly — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d2c1482f419153d14ad2d319f4581b1e14de7c6
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561071"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly — element (szablony Visual Studio)
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
  
 `Reference`, `References,` i `Assembly` elementów należy używać tylko w *.vstemplate* plików, które mają `Type` wartość atrybutu `Item`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `TemplateContent` element szablon elementu. Poniższy kod XML dodaje odwołania do *System.dll* i *System.Data.dll* zestawów.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)