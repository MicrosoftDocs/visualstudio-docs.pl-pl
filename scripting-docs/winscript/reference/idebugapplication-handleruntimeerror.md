---
title: 'IDebugApplication:: HandleRuntimeError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574329"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Powoduje, że bieżący wątek blokuje i wysyła powiadomienie o błędzie do środowiska IDE debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 podczas Błąd, który wystąpił.  
  
 `pScriptSite`  
 podczas Lokacja skryptu wątku.  
  
 `pbra`  
 określoną Akcja podejmowana, gdy debuger wznawia działanie aplikacji.  
  
 `perra`  
 określoną Akcja podejmowana, gdy debuger wznawia działanie aplikacji, jeśli wystąpi błąd.  
  
 `pfCallOnScriptError`  
 określoną Flaga, która jest `TRUE`, jeśli aparat powinien wywołać metodę `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, który powoduje błąd w czasie wykonywania. Ta metoda powoduje, że bieżący wątek blokuje i wysyła powiadomienie o błędzie do wysłania do środowiska IDE debugera. Gdy środowisko IDE debugera wznawia działanie aplikacji, Metoda ta zwraca z akcją, która ma zostać wykonana.  
  
> [!NOTE]
> Podczas gdy błąd czasu wykonywania, Aparat języka może być wywoływany przez wątek w celu wykonywania takich zadań jak Wyliczenie ramek stosu lub obliczenia wyrażeń.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication  interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IActiveScriptErrorDebug  interfejsu](../../winscript/reference/iactivescripterrordebug-interface.md)  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
   [Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION, wyliczenie](../../winscript/reference/errorresumeaction-enumeration.md)