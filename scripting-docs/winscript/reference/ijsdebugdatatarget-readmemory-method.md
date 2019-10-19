---
title: 'IJsDebugDataTarget:: ReadMemory — — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572435"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory — Metoda
Odczytuje pamięć procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres podstawowy, z którego ma zostać odczytana pamięć procesu docelowego.  
  
 `flags`  
 podczas Flagi kontrolujące zachowanie ReadMemory —.  
  
 `pBuffer`  
 określoną Bufor, który odbiera zawartość z przestrzeni adresowej procesu docelowego. W przypadku niepowodzenia zawartość tego buforu jest nieokreślona.  
  
 `size`  
 podczas Liczba bajtów, które mają zostać odczytane z procesu.  
  
 `pBytesRead`  
 określoną Wskazuje liczbę bajtów odczytanych z procesu docelowego. Jeśli atrybut JsDebugAllowPartialRead jest jasne, po pomyślnym wykonaniu tej wartości zawsze będzie ona dokładnie równa rozmiarowi danych wejściowych. Jeśli atrybut JsDebugAllowPartialRead jest określony, po powodzeniu, ta wartość będzie większa od zera.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca S_OK na sukcesie, a kody błędów są używane dla dowolnego błędu. Zwraca E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli adres jest nieprawidłowy. Aby uzyskać więcej informacji, zobacz atrybut JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)