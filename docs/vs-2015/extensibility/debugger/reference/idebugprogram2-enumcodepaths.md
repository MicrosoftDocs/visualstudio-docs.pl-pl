---
title: IDebugProgram2::EnumCodePaths | Dokumentacja firmy Microsoft
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
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a6ee294a94c59209cd50513a91664d27a7f94bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720616"
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

