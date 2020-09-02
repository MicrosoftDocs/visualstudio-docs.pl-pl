---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b23073c41f5da7d1563a6be46e0d114334527b35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153510"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje lokalizację punktu przerwania pod adresem w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `bstrContext`  
 Kontekst punktu przerwania, zazwyczaj nazwa metody lub funkcji, jak pokazano na stosie wywołań.  
  
 `bstrModuleUrl`  
 Adres URL modułu, który zawiera punkt przerwania.  
  
 `bstrFunction`  
 Nazwa funkcji, która zawiera punkt przerwania.  
  
 `bstrAddress`  
 Adres punktu przerwania, który jest analizowany przez ewaluatora wyrażeń, aby powiązać go z obiektem [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest składową struktury [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) w ramach Unii.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
