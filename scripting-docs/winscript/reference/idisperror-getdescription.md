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
ms.openlocfilehash: aff28f0f552bcad6792e4d252a92e45e9a6fd38c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146698"
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
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispError](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)