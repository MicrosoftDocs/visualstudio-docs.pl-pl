---
title: 'IJsDebugDataTarget:: FreeVirtualMemory — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577620"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory — Metoda
Zwalnia i/lub anuluje region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres w ramach procesu docelowego, gdzie pamięć powinna zostać zwolniona.  
  
 `size`  
 podczas Liczba bajtów do anulowania zatwierdzenia. Aby zwolnić region pamięci, ta wartość musi być równa zero.  
  
 `freeType`  
 podczas Wskazuje typ bezpłatnej operacji do wykonania. Jest to zazwyczaj MEM_RELEASE (0x8000), który zwalnia określony region stron. Po wykonaniu tej operacji strony są w stanie wolnym. MEM_DECOMMIT (0x4000) można zamiast tego użyć do anulowania zatwierdzeń stron bez ich zwolnienia.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać dodatkowe informacje, zobacz VirtualFree Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)