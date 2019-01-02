---
title: GuidSymbol, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a010a4ea3e135dab9d80cf84edf651df966bf271
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902282"
---
# <a name="guidsymbol-element"></a>GuidSymbol, element
`GuidSymbol` Element zawiera identyfikator GUID pary GUID:ID, który reprezentuje menu, grupy lub polecenia. Identyfikator pochodzi z `IDSymbol` element `GuidSymbol` elementu. `GuidSymbol` Element ma `name` atrybut, który zawiera przyjazną nazwę dla identyfikatora GUID, który jest zawarty w `value` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagana. Nazwa symbolu identyfikatora GUID.|  
|value|Wymagana. Identyfikator GUID symbolu identyfikatora GUID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[IDSymbol, element](../extensibility/idsymbol-element.md)|Zawiera identyfikator parą GUID:ID, która reprezentuje menu, grupy lub polecenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Symbols, element](../extensibility/symbols-element.md)|Grupy `GuidSymbol` elementów w *vsct* pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj *vsct* plik zawiera trzy `GuidSymbol` elementów w jego `Symbols` sekcji, w ramach pakietu, po jednym dla zestawu poleceń (kolekcja menu, grupy i polecenia udostępnia pakiet), a jeden dla mapy bitowe, które zapewniają ikon do przycisków i innych składników programu visual. Każdy `IDSymbol` elementu w danym `GuidSymbol` element musi mieć unikatową `value`. Jednak `IDSymbol` elementy, które ma takie same wartości może znajdować się w pakiecie, tak długo, jak długo mają różne elementy nadrzędne.  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)