---
title: GuidSymbol — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204221"
---
# <a name="guidsymbol-element"></a>GuidSymbol, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`Element zawiera identyfikator GUID pary GUID: ID, która reprezentuje menu, grupę lub polecenie. Identyfikator pochodzi od `IDSymbol` elementu w `GuidSymbol` elemencie. `GuidSymbol`Element ma `name` atrybut, który zawiera przyjazną nazwę dla identyfikatora GUID, który jest zawarty w `value` atrybucie.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|name|Wymagany. Nazwa symbolu GUID.|  
|value|Wymagany. Identyfikator GUID symbolu GUID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[IDSymbol, element](../extensibility/idsymbol-element.md)|Zawiera identyfikator pary GUID: ID, która reprezentuje menu, grupę lub polecenie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Symbols, element](../extensibility/symbols-element.md)|Grupuje `GuidSymbol` elementy w pliku. vsct.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle plik. vsct zawiera trzy `GuidSymbol` elementy w `Symbols` sekcji, jeden dla samego pakietu, jeden dla zestawu poleceń (Kolekcja menu, grup i poleceń udostępnianych przez pakiet), a drugi dla map bitowych, które udostępniają ikony przycisków i innych elementów wizualnych. Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatową wartość `value` . Jednak `IDSymbol` elementy mające identyczne wartości mogą istnieć w pakiecie, o ile mają różne obiekty nadrzędne.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
