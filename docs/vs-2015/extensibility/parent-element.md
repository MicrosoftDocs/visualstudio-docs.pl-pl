---
title: Element nadrzędny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194078"
---
# <a name="parent-element"></a>Element nadrzędny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element nadrzędny przycisku lub pola kombi może być tylko grupą. Element nadrzędny menu lub grupy może być dowolnym innym menu lub grupą. W [elemencie CommandPlacement](../extensibility/commandplacement-element.md), ten element jest wymagany; we wszystkich innych przypadkach jest to opcjonalne. Jeśli ten element zostanie pominięty, `Group_Undefined:0` zostanie implikowany element nadrzędny elementu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|  
|identyfikator|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które pakietu VSPackage zapewnia zintegrowane środowisko programistyczne (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy [elementu Button](../extensibility/button-element.md) .|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje pakietu VSPackage.|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy poleceń elementu pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
