---
title: IJsDebugFrame, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa491a02d289a0a92a70348ec5ef483dd8f8467
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093305"
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
|[IJsDebugFrame::Evaluate, metoda](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Ocena wyrażenia w kontekście tej ramki stosu.|  
|[IJsDebugFrame::GetDebugProperty, metoda](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Zwraca przeglądarkę właściwości dla tej ramki stosu.|  
|[IJsDebugFrame::GetDocumentPositionWithId, metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Zwraca bieżącą pozycję ramki stosu w obrębie dokumentu poziomie użytkownika.|  
|[IJsDebugFrame::GetDocumentPositionWithName, metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Zwraca bieżącą pozycję ramki stosu w obrębie dokumentu poziomie użytkownika.|  
|[IJsDebugFrame::GetName, metoda](../../winscript/reference/ijsdebugframe-getname-method.md)|Pobiera nazwę przyjazną dla użytkownika ramki stosu.|  
|[IJsDebugFrame::GetReturnAddress, metoda](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Pobiera adres zwrotny wypychany na "początku" (zobacz GetStackRange) klatki.|  
|[IJsDebugFrame::GetStackRange, metoda](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Zwraca bezwzględny zakres adresów dla logicznej ramki stosu JavaScript.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)