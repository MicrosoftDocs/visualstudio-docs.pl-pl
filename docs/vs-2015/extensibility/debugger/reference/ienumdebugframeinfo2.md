---
title: IEnumDebugFrameInfo2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6938641b2ec274d23928742bbaa014c43c02dc48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728279"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

