---
title: 'IActiveScriptAuthor:: GetChars | Microsoft Docs'
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
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576250"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Zwraca zestaw znaków zakończenia dla żądanego kontekstu uzupełniania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fRequestedList`  
 podczas Żądany kontekst uzupełniania.  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Żąda wyliczenia po lewej stronie.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Żąda kontekstu uzupełniania elementu członkowskiego.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Żąda listy parametrów.|  
|SCRIPT_CMPL_COMMIT|0x0004|Żąda wykonania listy parametrów.|  
  
 `pbstrChars`  
 określoną Znaki, które odnoszą się do żądanego kontekstu uzupełniania.  
  
|`fRequestedList` parametr|Zwrócone znaki|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)