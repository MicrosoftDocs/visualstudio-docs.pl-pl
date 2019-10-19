---
title: 'IJsDebugDataTarget:: AllocateVirtualMemory — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577641"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory — Metoda
Rezerwuje i/lub zatwierdza region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres w ramach procesu docelowego, gdzie pamięć powinna zostać zatwierdzona lub zarezerwowana. Ta wartość jest zwykle równa zero, w takim przypadku system wybiera adres.  
  
 `size`  
 podczas Rozmiar obszaru pamięci do przydzielenia w bajtach. System zostanie automatycznie zaokrąglony do następnej granicy strony.  
  
 `allocationType`  
 podczas Wskazuje typ alokacji do wykonania. Zwykle jest to MEM_COMMIT &#124; MEM_RESERVE (0x3000), które rezerwuje i zatwierdza alokację w jednym kroku.  
  
 `pageProtection`  
 podczas Ochrona pamięci dla regionu stron do przydzielenia. Jeśli strony są zatwierdzane, możesz określić dowolną ze stałych ochrony pamięci (na przykład PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 określoną Adres podstawowy przydzielonych regionów stron.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Funkcja inicjuje pamięć przydzielona do zera, chyba że zostanie użyta MEM_RESET. Aby uzyskać dodatkowe informacje, zobacz Funkcja VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)