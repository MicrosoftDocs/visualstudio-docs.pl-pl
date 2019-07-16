---
title: IDSymbol, Element | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203965"
---
# <a name="idsymbol-element"></a>IDSymbol, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol` Element zawiera identyfikator pary GUID:ID, który reprezentuje menu, grupy lub polecenia. Identyfikator GUID, który jest dostarczany z obiektu nadrzędnego `GuidSymbol` elementu. `IDSymbol` Element ma `name` atrybut, który zawiera przyjazną nazwę dla Identyfikatora, który jest zawarty w `value` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagane. Nazwa symbolu identyfikator.|  
|value|Wymagane. Wartość liczbowa Identyfikatora symbolu identyfikator.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[GuidSymbol, element](../extensibility/guidsymbol-element.md)|Zawiera unikatowy identyfikator GUID pary GUID:ID, który reprezentuje menu, grupy lub polecenia. Grupy `IDSymbol` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `IDSymbol` elementu w danym `GuidSymbol` element musi mieć unikatową `value`. Jednak `IDSymbol` elementy, które ma takie same wartości może znajdować się w pakiecie, tak długo, jak długo mają różne elementy nadrzędne.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
