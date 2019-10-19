---
title: 'IActiveScriptSiteDebugEx:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
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
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572182"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informuje hosta o błędzie wykonywania skryptu, gdy Menedżer debugowania procesów nie znalazł debugera skryptów just in Time.  
  
 Aby zaimplementować debuger na hoście, należy obsłużyć [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Na podstawie akcji użytkownika host może dołączyć debuger i zwrócić lub zwrócić początkowy debuger w parametrze OnScriptErrorDebug `pfEnterDebugger`. Należy również zaimplementować ten interfejs, aby otrzymać powiadomienie dotyczące błędu czasu wykonywania nawet wtedy, gdy nie ma żadnych zewnętrznych debugerów, które mogą być interpretowane przez Menedżera debugowania procesów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 podczas Wystąpił błąd czasu wykonywania.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 określoną Określa, czy należy wywołać [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) , jeśli użytkownik zdecyduje się kontynuować bez debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy również zaimplementować ten interfejs, aby otrzymać powiadomienie.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteDebugEx, interfejs](../../winscript/reference/iactivescriptsitedebugex-interface.md)