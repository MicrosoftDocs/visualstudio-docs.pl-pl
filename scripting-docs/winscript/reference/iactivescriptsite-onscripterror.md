---
title: 'IActiveScriptSite:: OnScriptError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570270"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informuje hosta, że wystąpił błąd wykonywania, gdy aparat uruchomił skrypt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pase`  
 podczas Adres interfejsu [IActiveScriptError](../../winscript/reference/iactivescripterror.md) obiektu błędu. Host może użyć tego interfejsu, aby uzyskać informacje o błędzie wykonania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli błąd został poprawnie obsłużony, lub w przeciwnym razie kod błędu zdefiniowany przez OLE.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)