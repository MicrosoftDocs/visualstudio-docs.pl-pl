---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 844d93a6752538c6b7239b6c10688fdfbd98b401
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695188"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM) do wyprowadzania ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, aby wysłać ciąg do okna **dane wyjściowe** IDE. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Po utworzeniu i wysłaniu tego obiektu zdarzenia w celu wysłania ciągu do okna **danych wyjściowych** . Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metodę `IDebugOutputStringEvent2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Pobiera komunikat, który ma być odtwarzany.|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład w kodzie niezarządzanym ciąg, który ma być wynikiem, może pochodzić, gdy debugowany program wysyła ciąg do `OutputDebugString` funkcji Win32. Ten ciąg jest przechwytywany przez DE i wysłane do modelu SDM jako `IDebugOutputStringEvent2` zdarzenie.  
  
 Użyj [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) , aby wysłać komunikat wymagający odpowiedzi użytkownika.  
  
 Użyj [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) , aby wysłać komunikat o błędzie, który nie wymaga odpowiedzi.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
