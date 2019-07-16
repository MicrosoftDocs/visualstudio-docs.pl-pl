---
title: IDebugProgram2::EnumCodePaths | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202772"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera listę ścieżek kodu dla danego stanowiska w pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszHint`  
 [in] Word pod kursorem w **źródła** lub **dezasemblacji** widoku w środowisku IDE.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt reprezentujący bieżący kontekst kodu.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt reprezentujący ramkę stosu skojarzone z bieżącym punktu przerwania.  
  
 `fSource`  
 [in] Wartość różną od zera (`TRUE`) Jeśli w **źródła** widoku lub zero (`FALSE`) Jeśli w **dezasemblacji** widoku.  
  
 `ppEnum`  
 [out] Zwraca [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obiekt, który zawiera listę ścieżek kodu.  
  
 `ppSafety`  
 [out] Zwraca [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektów reprezentującą kontekst dodatkowy kod ma być ustawiona jako punkt przerwania, w przypadku, gdy wybrana kodu ścieżka zostanie pominięta. Może to nastąpić w przypadku zwartym wyrażenie logiczne, np.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ścieżka kodu w tym artykule opisano nazwę metody lub funkcji, która została wywołana, aby uzyskać dostęp do bieżącego punktu podczas wykonywania programu. Lista ścieżek kodu przedstawia stos wywołań.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
