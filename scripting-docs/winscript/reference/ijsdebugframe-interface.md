---
title: Interfejs IJsDebugFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575103"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame — Interfejs
Reprezentuje ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate, metoda](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Oceń wyrażenie w kontekście tej ramki stosu.|  
|[IJsDebugFrame::GetDebugProperty, metoda](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Zwraca przeglądarkę właściwości dla tej ramki stosu.|  
|[IJsDebugFrame::GetDocumentPositionWithId, metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Zwraca bieżącą pozycję ramki stosu w dokumencie na poziomie użytkownika.|  
|[IJsDebugFrame::GetDocumentPositionWithName, metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Zwraca bieżącą pozycję ramki stosu w dokumencie na poziomie użytkownika.|  
|[IJsDebugFrame::GetName, metoda](../../winscript/reference/ijsdebugframe-getname-method.md)|Pobiera przyjazną dla użytkownika nazwę ramki stosu.|  
|[IJsDebugFrame::GetReturnAddress, metoda](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Pobiera adres zwrotny wypychany przy użyciu elementu "Start" (zobacz GetStackRange —) ramki.|  
|[IJsDebugFrame::GetStackRange, metoda](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Zwraca bezwzględny zakres adresów logicznej ramki stosu JavaScript.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)