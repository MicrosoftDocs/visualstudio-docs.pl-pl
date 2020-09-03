---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161011"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs wylicza struktury [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby udostępnić listę struktur, które opisują bieżący stos wywołań.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Program Visual Studio wywołuje [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , aby uzyskać ten interfejs za każdym razem, gdy punkt przerwania, wyjątek lub zatrzymanie występuje w debugowanym programie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IEnumDebugFrameInfo2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Pobiera określoną liczbę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) w sekwencji wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Pomija określoną liczbę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) w sekwencji wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Pobiera liczbę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) w module wyliczającym.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio uzyskuje ten interfejs jako pierwszy krok do obsługi punktu przerwania, wyjątku lub wstrzymania wygenerowanego przez użytkownika w debugowanym programie. Lista struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) reprezentuje bieżący stos wywołań i bieżące wywołanie funkcji na początku listy i najstarsze wywołanie funkcji na końcu listy. Każda `FRAMEINFO` reprezentuje ramkę stosu, kontekst, w którym można ocenić wyrażenia, a zmienne lokalne są oglądane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
