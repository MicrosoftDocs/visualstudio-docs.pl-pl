---
title: IJsDebugDataTarget::FreeVirtualMemory, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146308"
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
 [in] Adres w ramach procesu docelowego, gdzie pamięć powinna być zwolniona.  
  
 `size`  
 [in] Liczba bajtów przeznaczonych do anulowania. Aby zwolnić region pamięci, ta wartość musi mieć wartość zero.  
  
 `freeType`  
 [in] Wskazuje typ wolnych operacji do wykonania. Jest to zazwyczaj MEM_RELEASE (0x8000), która uwalnia określony region stron. Po tej operacji strony są w stanie wolnym. MEM_DECOMMIT (0x4000) można w zamian użyć do anulowania przydziałów stron bez ich zwalniania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać dodatkowe informacje Zobacz VirtualFree Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)