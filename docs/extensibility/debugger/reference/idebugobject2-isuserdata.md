---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33b6815f5d216e4259c7e43dad11ca93ab1a3776
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015631"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Określa, czy obiekt reprezentuje dane użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfUser`  
 [out] Zwraca wartość różną od zera (`TRUE`) obiekt reprezentuje dane użytkownika; wartość zero (`FALSE`) Jeśli nie jest.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Dane użytkownika są dowolnego obiektu, który jest częścią modułu wyznaczony jako JustMyCode (konfigurowanych przez użytkownika opcji oznaczający moduł jako kod użytkownika i dlatego są widoczne w śladzie stosu).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)