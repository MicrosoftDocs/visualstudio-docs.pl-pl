---
title: Interfejs IJsDebugDataTarget | Microsoft Docs
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
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572451"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget — Interfejs
Zaimplementowane przez debuger, aby zapewnić funkcjonalność dostępu i zmiany stanu docelowego procesu debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory, metoda](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Rezerwuje i/lub zatwierdza region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator, metoda](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Tworzy moduł wyliczający dla ramek stosu.|  
|[IJsDebugDataTarget::FreeVirtualMemory, metoda](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Zwalnia i/lub anuluje region pamięci w wirtualnej przestrzeni adresowej procesu docelowego.|  
|[IJsDebugDataTarget::GetThreadContext, metoda](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Pobiera kontekst dla danego wątku.|  
|[IJsDebugDataTarget::GetTlsValue, metoda](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Dla debugowanego wątku Pobiera wartość w gnieździe lokalnego magazynu wątków (TLS) dla określonego indeksu protokołu TLS.|  
|[IJsDebugDataTarget::ReadBSTR, metoda](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Odczytuje element BSTR z elementu docelowego debugowania.|  
|[IJsDebugDataTarget::ReadMemory, metoda](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Odczytuje pamięć procesu docelowego.|  
|[IJsDebugDataTarget::ReadNullTerminatedString, metoda](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Odczytuje określoną liczbę znaków z obiektu docelowego.|  
|[IJsDebugDataTarget::WriteMemory, metoda](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Odczytuje pamięć procesu docelowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)