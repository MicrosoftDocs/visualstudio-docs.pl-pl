---
title: IJsDebug::OpenVirtualProcess, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093993"
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