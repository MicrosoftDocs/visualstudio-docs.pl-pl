---
title: 'IJsDebug:: OpenVirtualProcess — — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577743"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess — Metoda
Metoda fabryki użyta do utworzenia nowego obiektu procesu wirtualnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `processId`  
 podczas Identyfikator procesu, do którego ma zostać dołączony debuger.  
  
 `runtimeJsBaseAddress`  
 podczas Adres podstawowy, pod którym środowisko uruchomieniowe języka JavaScript zostało załadowane do procesu docelowego.  
  
 `pDataTarget`  
 podczas Debuger dostarczył interfejs do wykonywania zapytań dotyczących stanu procesu.  
  
 `ppProcess`  
 określoną Nowy obiekt procesu debugowania  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca E_JsDEBUG_MISMATCHED_RUNTIME, jeśli Jscript9diag i jscript9 nie są zgodne.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebug, interfejs](../../winscript/reference/ijsdebug-interface.md)