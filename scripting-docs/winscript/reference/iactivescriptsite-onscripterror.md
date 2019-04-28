---
title: IActiveScriptSite::OnScriptError | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d76aa46cbbcdab9a3c5c7b561b91ee58cfcac4ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992607"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informuje hosta, że wystąpił błąd wykonania, gdy aparat był uruchomiony skrypt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pase`  
 [in] Adres obiektu błąd [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfejsu. Host może używać tego interfejsu, aby uzyskać informacje na temat błędu wykonania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` czy błąd został prawidłowo obsłużony, OLE zdefiniowany kod błędu, w przeciwnym razie.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)