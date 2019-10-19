---
title: 'IJsDebugDataTarget:: ReadNullTerminatedString — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572401"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString — Metoda
Odczytuje określoną liczbę znaków z obiektu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres, z którego ma zostać odczytany.  
  
 `characterSize`  
 [in] rozmiar każdego znaku w ciągu  
  
 `maxCharacters`  
 podczas Maksymalna liczba znaków do odczytania. Wartość elementu maxCharacters powinny być uzasadnione. Każde żądanie dotyczące ponad 128 MB pamięci zakończy się niepowodzeniem.  Jeśli ciąg jest większy niż wartość elementu maxCharacters, ciąg wynikowy zostanie obcięty po wartość elementu maxCharacters.  
  
 `pString`  
 określoną Element BSTR jest odczytywany z celu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca S_FALSE, jeśli został obcięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)