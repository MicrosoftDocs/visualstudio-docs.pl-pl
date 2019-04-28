---
title: IJsDebugDataTarget::GetTlsValue, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582813"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue — Metoda
Dla debugowanego wątku pobiera wartość w gnieździe magazynu lokalnego (TLS) wątku dla określonego indeksu TLS.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Wątek działający w procesie docelowym do odczytu.  
  
 `tlsIndex`  
 [in] Indeks TLS, na który została przydzielony podczas procesu docelowego wywołanego przez funkcję TlsAlloc.  
  
 `pValue`  
 [out] Wartość wskaźnika wielkości, która została zapisana w gnieździe TLS wątku. Jeśli wątek docelowy jest 32-bitowy, górne 32 bity tej wartości będą równe zeru.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Każdy wątek procesu ma własne gniazdo dla każdego indeksu TLS.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)