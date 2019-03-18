---
title: IDispError::QueryErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32d887cad92de28df7e84f71fe6b991ada9067e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160355"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Pobiera informacje o błędzie określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidErrorType`  
 [in] Identyfikator GUID Określanie typu błędu.  
  
 `ppde`  
 [out] Określa obiekt IDispError.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `QueryErrorInfo` Metoda pobiera informacje o błędzie określonego typu.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDispError, interfejs](../../winscript/reference/idisperror-interface.md)