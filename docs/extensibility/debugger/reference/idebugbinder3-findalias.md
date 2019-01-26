---
title: IDebugBinder3::FindAlias | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee84291be79127af4ded052f9c16e17f426bd134
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026440"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Ta metoda lokalizuje alias podanej nazwy. Przeszuka wszystkie aliasy w programie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcstrName`  
 [in] Nazwa aliasu, aby znaleźć.  
  
 `ppAlias`  
 [out] Alias znaleziono (jeśli istnieje) jest reprezentowane przez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` (Jeśli nie odnaleziono aliasu) lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje obiekt docelowy, na wartość null, przed wywołaniem; następnie sprawdza zawiera wartości null później określić, czy nie znaleziono aliasu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)