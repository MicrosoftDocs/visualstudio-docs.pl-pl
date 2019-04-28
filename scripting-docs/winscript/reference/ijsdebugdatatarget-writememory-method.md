---
title: IJsDebugDataTarget::WriteMemory, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 622de16cc5f755c5d69059a0e0f28d881121861c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558180"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory — Metoda
Odczytuje pamięć procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres podstawowy, z którego można zapisywać pamięć procesu docelowego.  
  
 `pMemory`  
 [in] Dane do zapisania w przestrzeni adresowej określonego procesu.  
  
 `size`  
 [in] Liczba bajtów do zapisu do procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zanim nastąpi transfer danych, system sprawdza, czy wszystkie dane w adresie podstawowym i pamięci o określonym rozmiarze są dostępne do zapisu, a jeśli nie jest dostępny, funkcja zgłasza błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)