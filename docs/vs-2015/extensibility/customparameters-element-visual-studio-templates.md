---
title: Customparameters — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
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
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 620d2131247f9a0b1dfba3b506548695a897ce66
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721948"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Zobacz też  
 [CustomParameter, Element (szablony Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

