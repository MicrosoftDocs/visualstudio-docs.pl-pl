---
title: Nadrzędny Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c025957bd0d3cf06bf73e1b35b5faa661386a0a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902440"
---
# <a name="parent-element"></a>Element nadrzędny
Element nadrzędny przycisk lub pola kombi mogą być tylko grupy. Nadrzędny menu lub grupa może być dowolnego menu lub grupę. W [CommandPlacement, element](../extensibility/commandplacement-element.md), ten element jest wymagany; w innych wystąpieniach jest opcjonalne. W przypadku pominięcia tego elementu nadrzędnego `Group_Undefined:0` będzie wynikać.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
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
|[Buttons, element](../extensibility/buttons-element.md)|Grupy [Button element](../extensibility/button-element.md) elementów.|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|  
|[Element grupy](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)