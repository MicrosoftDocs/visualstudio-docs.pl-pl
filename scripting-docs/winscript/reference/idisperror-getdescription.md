---
title: 'IDispError:: GetDescription | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573142"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Zwraca tekstowy opis błędu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrDescription`  
 określoną Ciąg zawierający krótki opis błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Tekst jest zwracany w języku określonym przez identyfikator ustawień regionalnych (LCID), który został przekazano do `IDispatchEx::InvokeEx` dla metody, która napotkała błąd.  
  
> [!NOTE]
> Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz także  
 [IDispError   interfejsu](../../winscript/reference/idisperror-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)