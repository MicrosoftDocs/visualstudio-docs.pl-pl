---
title: IDebugProgramHost2::GetHostName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 040602eeca784ac6265403f615f9234864715949
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923272"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwType`  
 [in] Wartość z zakresu od [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) wyliczenia.  
  
 `pbstrHostName`  
 [out] Zwraca nazwę żądanej procesu hostingu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W Typowa implementacja tej metody `dwType` parametr jest ignorowany i zwracany jest przyjazną nazwę komputera hosta. Inną możliwą implementację służy do przekazywania `dwType` parametr do wywołania [gethostname —](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metodę, aby uzyskać nazwę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)