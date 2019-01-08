---
title: IJsDebugDataTarget::ReadMemory, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 66d3709dadfc8da2feb7e6845a7aeaa357235d9e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089183"
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
 [in] Adres podstawowy, z którego można odczytać pamięć procesu docelowego.  
  
 `flags`  
 [in] Flagi sterujące zachowaniem ReadMemory.  
  
 `pBuffer`  
 [out] Bufor, który odbiera zawartość z przestrzeni adresowej procesu docelowego. W przypadku awarii zawartość tego buforu jest nieokreślona.  
  
 `size`  
 [in] Liczba bajtów do odczytu z procesu.  
  
 `pBytesRead`  
 [out] Wskazuje liczbę bajtów odczytanych z procesu docelowego. Jeśli atrybut JsDebugAllowPartialRead jest pusty, w przypadku powodzenia, do których ta wartość będzie zawsze równa dokładnie rozmiarowi wejściowemu. Jeśli atrybut JsDebugAllowPartialRead jest określony w przypadku powodzenia ta wartość będzie większa niż zero.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość S_OK w przypadku powodzenia i kody błędów są stosowane do wszystkich błędów. Zwraca wartość E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli adres nie jest prawidłowy. Aby uzyskać więcej informacji zobacz JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)