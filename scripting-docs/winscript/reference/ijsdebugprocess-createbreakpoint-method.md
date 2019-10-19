---
title: 'IJsDebugProcess:: ispunk — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575093"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint — Metoda
Ustawia punkt przerwania w określonym położeniu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `documentId`  
 podczas Wskaźnik do IDebugDocumentText.  
  
 `characterOffset`  
 podczas Przesunięcie znaku od początku pliku.  
  
 `characterCount`  
 podczas Długość tekstu dokumentu, w którym należy wstawić punkt przerwania.  
  
 `isEnabled`  
 podczas Określa, czy punkt przerwania jest włączony.  
  
 `ppDebugBreakPoint`  
 określoną Obiekt reprezentujący utworzony punkt przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugProcess, interfejs](../../winscript/reference/ijsdebugprocess-interface.md)