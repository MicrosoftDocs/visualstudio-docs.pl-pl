---
title: CustomParameter, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555973"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera niestandardową nazwę i wartość parametru, która ma być używana podczas tworzenia projektu lub elementu z szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Nazwa parametru. Format parametrów to $*name*$.|  
|`Value`|Wymagany. Wartość zastępcza parametru.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Grupuje parametry niestandardowe, które mają być przenoszone do Kreatora szablonów, gdy Kreator przejdzie do parametrów.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy szablon zawiera `CustomParameter` elementy, każde wystąpienie `Name` atrybutu jest zastępowane `Value` atrybutem w utworzonym pliku projektu lub elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać kilku parametrów niestandardowych w szablonie. Gdy projekt lub element jest tworzony na podstawie szablonu o następujących parametrach niestandardowych, wszystkie wystąpienia `$color1$` i `$color2$` w plikach szablonów zostaną zastąpione `Red` `Blue` odpowiednio i.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CustomParameters —, element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
