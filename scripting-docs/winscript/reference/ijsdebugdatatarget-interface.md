---
title: IJsDebugDataTarget, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cbb4b0b54fb9a3821d3033ef0e65fd0bafbc246
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582501"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget — Interfejs
Implementowany przez debugera w celu udostępnienia funkcji dostępu i zmiany stanu docelowego procesu debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory, metoda](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Rezerwuje i/lub zwalnia region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator, metoda](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Tworzy moduł wyliczający ramek stosu.|  
|[IJsDebugDataTarget::FreeVirtualMemory, metoda](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Zwalnia i/lub anuluje region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::GetThreadContext, metoda](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Pobiera kontekst dla podanego wątku.|  
|[IJsDebugDataTarget::GetTlsValue, metoda](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Dla debugowanego wątku pobiera wartość w gnieździe magazynu lokalnego (TLS) wątku dla określonego indeksu TLS.|  
|[IJsDebugDataTarget::ReadBSTR, metoda](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Odczytuje ciąg BSTR z docelowego programu debug.|  
|[IJsDebugDataTarget::ReadMemory, metoda](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Odczytuje pamięć procesu docelowego.|  
|[IJsDebugDataTarget::ReadNullTerminatedString, metoda](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Odczytuje określoną liczbę znaków z obiektu docelowego.|  
|[IJsDebugDataTarget::WriteMemory, metoda](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Odczytuje pamięć procesu docelowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)