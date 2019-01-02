---
title: IEnumDebugFrameInfo2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa2db1f249492702971eb311fe38f76eec3a5b3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857203"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Ten interfejs wylicza [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby udostępnić listę struktur, który opisuje bieżący stos wywołań.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) uzyskać ten interfejs, w każdym przypadku, gdy punkt przerwania, wyjątek lub zatrzymania występuje debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugFrameInfo2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Pobiera określoną liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktur w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Pomija określoną liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktur w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Pobiera liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio pobiera ten interfejs jako pierwszy krok do obsługi punktu przerwania, wyjątek lub wstrzymania wygenerowaną przez użytkowników na debugowanego programu. Lista [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury reprezentuje bieżący stos wywołań, przy użyciu bieżącego wywołania funkcji na początku listy i funkcja najstarsze wywołania na końcu listy. Każdy `FRAMEINFO` reprezentuje ramkę stosu, kontekst, w którym mogą być obliczane wyrażenia, oraz znasz zmiennych lokalnych.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)