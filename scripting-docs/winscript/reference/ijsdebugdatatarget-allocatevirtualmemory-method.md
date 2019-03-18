---
title: IJsDebugDataTarget::AllocateVirtualMemory, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148467"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory — Metoda
Rezerwuje i/lub zwalnia region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.  
  
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
 [in] Adres w ramach procesu docelowego, gdzie przekazana lub zarezerwowana pamięć. Ta wartość zazwyczaj wynosi zero, w których przypadku system wybiera adres.  
  
 `size`  
 [in] Rozmiar obszaru pamięci do przydzielenia, w bajtach. System będzie automatycznie zaokrąglał w górę do następnej granicy strony.  
  
 `allocationType`  
 [in] Wskazuje typ przydziału do wykonania. Zazwyczaj jest to MEM_COMMIT &#124; MEM_RESERVE (0x3000), która rezerwuje i zatwierdza alokację w jednym kroku.  
  
 `pageProtection`  
 [in] Ochrona pamięci dla obszaru stron do przypisania. Jeśli strony są zatwierdzane, można określić jednej ze stałych ochrony pamięci (na przykład PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Adres podstawowy przydzielonego zakresu stron.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Funkcja inicjuje pamięć, którą przydziela do zera, chyba że jest mem_reset. Aby uzyskać dodatkowe informacje Zobacz VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)