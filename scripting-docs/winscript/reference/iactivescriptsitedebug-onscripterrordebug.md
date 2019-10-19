---
title: 'IActiveScriptSiteDebug:: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572208"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Umożliwia inteligentnemu hostowi określenie, jak obsługiwać błędy w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 podczas Błąd czasu wykonywania, który wystąpił  
  
 `pfEnterDebugger`  
 określoną Flaga oznaczająca, czy przekazać błąd do debugera, aby przeprowadzić debugowanie JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 określoną Flaga oznaczająca, czy wywołać `IActiveScriptSite::OnScriptError`, gdy użytkownik zdecyduje się kontynuować bez debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Możliwe wartości to m.in., ale nie są ograniczone do wartości w poniższej tabeli.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Inteligentny host może użyć tej metody, aby określić, jak obsługiwać błędy w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteDebug, interfejs](../../winscript/reference/iactivescriptsitedebug-interface.md)