---
title: Nadrzędny Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62096a713e84353ab79206c5edc7003ab443adbb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765875"
---
# <a name="parent-element"></a>Element nadrzędny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element nadrzędny przycisk lub pola kombi mogą być tylko grupy. Nadrzędny menu lub grupa może być dowolnego menu lub grupę. W [CommandPlacement, Element](../extensibility/commandplacement-element.md), ten element jest wymagany; w innych wystąpieniach jest opcjonalne. W przypadku pominięcia tego elementu nadrzędnego `Group_Undefined:0` będzie wynikać.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator polecenia dla identyfikatora GUID/identyfikator GUID.|  
|identyfikator|Wymagana. Identyfikator polecenia identyfikator GUID/ID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń, które zapewnia pakietu VSPackage do zintegrowanego środowiska programistycznego (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupy [Button Element](../extensibility/button-element.md) elementów.|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

