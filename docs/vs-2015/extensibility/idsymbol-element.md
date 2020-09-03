---
title: IDSymbol — element | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203965"
---
# <a name="idsymbol-element"></a>IDSymbol, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol`Element zawiera identyfikator pary GUID: ID, która reprezentuje menu, grupę lub polecenie. Identyfikator GUID pochodzi z elementu nadrzędnego `GuidSymbol` . `IDSymbol`Element ma `name` atrybut, który zawiera przyjazną nazwę dla identyfikatora, który jest zawarty w `value` atrybucie.  
  
## <a name="syntax"></a>Składnia  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Wymagany. Nazwa symbolu identyfikatora.|  
|value|Wymagany. Wartość identyfikatora numerycznego symbolu identyfikatora.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[GuidSymbol, element](../extensibility/guidsymbol-element.md)|Zawiera identyfikator GUID pary identyfikatora GUID:, która reprezentuje menu, grupę lub polecenie. Grupuje `IDSymbol` elementy.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `IDSymbol` element w danym `GuidSymbol` elemencie musi mieć unikatową wartość `value` . Jednak `IDSymbol` elementy mające identyczne wartości mogą istnieć w pakiecie, o ile mają różne obiekty nadrzędne.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
