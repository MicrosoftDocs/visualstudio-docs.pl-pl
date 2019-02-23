---
title: IEnumDebugObjects::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ec21965c90680837c021a6bac8cafabd2a7ecb0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679624"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Ta metoda zwraca liczbę elementów w wyliczeniu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

#### <a name="parameters"></a>Parametry
 `pcelt`

 [out] Zwraca liczbę elementów w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest częścią zwyczajowego interfejsu wyliczenie COM, który określa, że tylko dalej, klonowania, Pomiń i resetowania muszą zostać zaimplementowane.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)