---
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202772"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera listę ścieżek kodu dla danego położenia w pliku źródłowym.  
  
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
 podczas Słowo pod kursorem w widoku **Źródło** lub **demontaż** w środowisku IDE.  
  
 `pStart`  
 podczas Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący bieżący kontekst kodu.  
  
 `pFrame`  
 podczas Obiekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) reprezentujący ramkę stosu skojarzoną z bieżącym punktem przerwania.  
  
 `fSource`  
 podczas Różna od zera ( `TRUE` ), jeśli znajduje się w widoku **źródła** lub zero ( `FALSE` ), jeśli znajduje się w widoku **demontażu** .  
  
 `ppEnum`  
 określoną Zwraca obiekt [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) zawierający listę ścieżek kodu.  
  
 `ppSafety`  
 określoną Zwraca obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący dodatkowy kontekst kodu, który ma być ustawiony jako punkt przerwania w przypadku pominięcia wybranej ścieżki kodu. Może się tak zdarzyć w przypadku krótko-obwodowego wyrażenia logicznego, na przykład.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ścieżka kodu opisuje nazwę metody lub funkcji, która została wywołana, aby przejść do bieżącego punktu w trakcie wykonywania programu. Lista ścieżek kodu reprezentuje stos wywołań.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
