---
title: IDebugApplication::HandleRuntimeError | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412439"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o błędzie do debugera w IDE.  
  
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
 [in] Błąd, który wystąpił.  
  
 `pScriptSite`  
 [in] Witryna skryptu wątku.  
  
 `pbra`  
 [out] Akcja do wykonania, gdy debuger wznawia działanie aplikacji.  
  
 `perra`  
 [out] Akcja do wykonania, gdy debuger wznawia działanie aplikacji, jeśli występuje błąd.  
  
 `pfCallOnScriptError`  
 [out] Flaga, która jest `TRUE` Jeśli silnik powinny wywoływać `IActiveScriptSite::OnScriptError` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, która powoduje występowanie błędów czasu wykonywania. Ta metoda powoduje, że bieżący wątek zablokować i wysyła powiadomienia o błędzie do wysłania do debugera w IDE. Gdy debuger IDE powraca do aplikacji, ta metoda zwraca za pomocą akcji do wykonania.  
  
> [!NOTE]
> Podczas pracy w błędów czasu wykonywania, aparat języka może zostać wywołana przez wątek do wykonywania zadań, takich jak wyliczanie ramek stosu lub oceny wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION, wyliczenie](../../winscript/reference/errorresumeaction-enumeration.md)