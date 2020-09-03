---
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f918b9895975554534ef1702334d7a006112f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202731"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera strumień demontażu dla tego programu lub części tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwScope`  
 podczas Określa wartość z wyliczenia [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , która definiuje zakres strumienia demontażu.  
  
 `pCodeContext`  
 podczas Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który reprezentuje położenie lokalizacji, w której ma zostać rozpoczęty strumień.  
  
 `ppDisassemblyStream`  
 określoną Zwraca obiekt [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , który reprezentuje strumień deasemblera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_DISASM_NOTSUPPORTED` Jeśli demontaż nie jest obsługiwany dla tej konkretnej architektury.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `dwScopes` parametr ma `DSS_HUGE` flagę zestawu [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , wówczas demontaż powinien zwrócić dużą liczbę instrukcji odnoszących się do zestawu, na przykład dla całego pliku lub modułu. Jeśli `DSS_HUGE` flaga nie jest ustawiona, demontaż powinien być ograniczony do małego regionu, zazwyczaj w przypadku pojedynczej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
