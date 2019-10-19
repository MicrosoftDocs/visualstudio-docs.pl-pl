---
title: 'IJsDebugDataTarget:: GetTLSValue — — Metoda | Microsoft Docs'
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
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577606"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue — Metoda
Dla debugowanego wątku Pobiera wartość w gnieździe lokalnego magazynu wątków (TLS) dla określonego indeksu protokołu TLS.  
  
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
 podczas Wątek działający w procesie docelowym, z którego ma zostać odczytany.  
  
 `tlsIndex`  
 podczas Indeks protokołu TLS, który został przydzielony podczas procesu docelowego o nazwie funkcja funkcja TlsAlloc.  
  
 `pValue`  
 określoną Wartość wskaźnika, która była przechowywana w gnieździe TLS wątku. Jeśli wątek docelowy jest 32-bitowy, górne 32 bity tej wartości będą równe zero.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Każdy wątek procesu ma własne miejsce dla każdego indeksu protokołu TLS.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)