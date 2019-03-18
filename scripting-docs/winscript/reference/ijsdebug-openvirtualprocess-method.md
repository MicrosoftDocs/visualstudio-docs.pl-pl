---
title: IJsDebug::OpenVirtualProcess, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151950"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess — Metoda
Metoda fabryki użyty do utworzenia nowego obiektu wirtualnego procesu.  
  
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
 [in] Identyfikator procesu, aby dołączyć debuger.  
  
 `runtimeJsBaseAddress`  
 [in] Adres podstawowy, w którym środowisko uruchomieniowe JavaScript został załadowany do procesu docelowego.  
  
 `pDataTarget`  
 [in] Debuger dostarczony interfejs do wykonywania kwerend dotyczących stanu procesu.  
  
 `ppProcess`  
 [out] Nowy obiekt proces debugowania  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość E_JsDEBUG_MISMATCHED_RUNTIME, jeśli Jscript9diag i Jscript9 są niezgodne.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebug, interfejs](../../winscript/reference/ijsdebug-interface.md)