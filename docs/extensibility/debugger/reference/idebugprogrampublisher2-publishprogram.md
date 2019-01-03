---
title: IDebugProgramPublisher2::PublishProgram | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeaa86ae2a740a1a31147f7294fd91bdbf5872d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991048"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Ta metoda powoduje, że program jest dostępny dla silniki debugowania (DEs) i Menedżer debugowania sesji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Engines`  
 [in] Tablica identyfikatorów GUID do obsługi szyfrowania DEs, które można uruchomić lub dołączyć do tego programu.  
  
 `szFriendlyName`  
 [in] Przyjazna nazwa dla programu (pojawia się w menu i okien dialogowych, użytkownik widzi).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interfejsu programu (Ta wartość jest używana jako plik cookie do unikatowego identyfikowania program; ta sama wartość służy do "cofnąć publikację" program)  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby napisać program, który nie jest już dostępna do debugowania, należy wywołać [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)