---
title: IDebugPortSupplierLocale2::SetLocale | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678b4d2815d7a44afcc38211a0035ca3e17a10c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933883"
---
# <a name="idebugportsupplierlocale2setlocale"></a>IDebugPortSupplierLocale2::SetLocale
Ustawia ustawienia regionalne dla dostawcy portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wLangID`  
 Identyfikator ustawień regionalnych ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)