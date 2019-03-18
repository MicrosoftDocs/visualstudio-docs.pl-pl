---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154481"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informuje, że hosta o błąd czasu wykonywania skryptu po procesie debugowanie Menedżera nie znajdzie debugera skryptów Just In Time.  
  
 Aby zaimplementować debugera w hoście, powinien obsługiwać [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Oparte na akcję użytkownika, host albo można dołączyć debuger i zwracają lub zwrócić uruchamiania w debugerze programu OnScriptErrorDebug `pfEnterDebugger` parametru. Należy także zaimplementować ten interfejs, aby otrzymywać powiadomienia o błędzie czasu wykonywania, nawet jeśli nie ma żadnych zewnętrznych debugery, które mogą być interpretowane przez Menedżer debugowania procesów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [in] Błąd w czasie wykonywania, który wystąpił.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Czy wywołać [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) Jeśli użytkownik zdecyduje kontynuować bez debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy także zaimplementować ten interfejs, aby otrzymać powiadomienie.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteDebugEx, interfejs](../../winscript/reference/iactivescriptsitedebugex-interface.md)