---
title: IActiveScriptAuthor::GetChars | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69cdeb16fa0791b3ff8c0cce4a4e67fe110eefc2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151066"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Zwraca zestaw znaków zakończenia dla kontekstu żądanego zakończenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fRequestedList`  
 [in] Kontekst żądanego zakończenia.  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Żądanie wyliczenia po lewej stronie.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Żąda kontekstu zakończenia elementu członkowskiego.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Żąda listy parametrów.|  
|SCRIPT_CMPL_COMMIT|0x0004|Ukończenie żądania listy parametrów.|  
  
 `pbstrChars`  
 [out] Znaki, które odnoszą się do kontekstu żądanego zakończenia.  
  
|`fRequestedList` Parametr|Znaki zwrócone|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)