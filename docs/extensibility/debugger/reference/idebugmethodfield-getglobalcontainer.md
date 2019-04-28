---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40bbee4c00425c4f46ccde35b8a8c810e1d7c8e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872820"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Pobiera kontener globalnego metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

#### <a name="parameters"></a>Parametry
 `ppClass`

 [out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) modułu, w którym zdefiniowano tej metody reprezentująca.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócony [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentuje cały moduł i jest obiektem sztuczny, oznacza to, że moduł sam nie rzeczywista klasa ale może być reprezentowany przez `IDebugClassField` obiektu, dzięki czemu różne elementy modułu być wyliczone i odnalezione.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)