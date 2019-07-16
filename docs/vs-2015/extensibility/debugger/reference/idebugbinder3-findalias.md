---
title: IDebugBinder3::FindAlias | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47aaaec73d2c364e974b7430335404bf8caf406c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142959"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
