---
title: Customparameters — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4366201e47e6ec682039b5d2a4cd33a8213f7f0
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561395"
---
# <a name="customparameters-element-visual-studio-templates"></a>Customparameters — element (szablony Visual Studio)
Grupy niestandardowe parametry, które mają być przekazane do Kreatora szablonów, gdy Kreator przeprowadza zamiany parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Zawiera nazwę niestandardowego parametru i wartości do użycia podczas projektu lub elementu jest tworzone na podstawie szablonu. Może wynosić zero lub więcej `CustomParameter` elementów w `CustomParameters` elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z kilku niestandardowych parametrów w szablonie. Podczas tworzenia projektu lub elementu za pomocą następujących parametrów niestandardowych, wszystkie wystąpienia szablonu `$color1$` i `$color2$` w szablonie zostanie zastąpiona pliki `Red` i `Blue`, odpowiednio.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [CustomParameter, element (szablony Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)