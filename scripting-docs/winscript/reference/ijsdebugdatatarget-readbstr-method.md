---
title: IJsDebugDataTarget::ReadBSTR, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e821893318cfe1d8f0b4239a077fc91c26be47f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582345"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR — Metoda
Odczytuje ciąg BSTR z docelowego programu debug.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres do odczytu.  
  
 `pString`  
 [out] Odczyt BSTR z docelowego programu debug.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli adres nie jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)