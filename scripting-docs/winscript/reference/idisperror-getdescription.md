---
title: IDispError::GetDescription | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5505113ee650c6618be5a95bc77244daf90cfcb7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446950"
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
 [out] Ciąg zawierający krótki opis błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracany jest tekst w języku określonym przez identyfikator ustawień regionalnych (LCID), który został przekazany do `IDispatchEx::InvokeEx` metodę, która napotkała błąd.  
  
> [!NOTE]
> Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispError](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)