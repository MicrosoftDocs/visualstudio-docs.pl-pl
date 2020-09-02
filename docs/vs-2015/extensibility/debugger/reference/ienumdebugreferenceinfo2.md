---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21c39c553a153707bad707d50cf5a13ae87973fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147749"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs wylicza [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi odwołań do obiektów w pamięci. Ten interfejs musi być zaimplementowany tylko w przypadku, gdy odwołania są obsługiwane.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Program Visual Studio wywołuje [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) , aby uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IEnumDebugReferenceInfo2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Pobiera określoną liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Pomija określoną liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Pobiera liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w module wyliczającym.|  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie jest zasadniczo typem i adresem, natomiast właściwość jest nazwą, typem i adresem. Odwołanie będzie utrwalane, o ile obiekt istnieje w pamięci. Aby uzyskać więcej informacji, zobacz [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
