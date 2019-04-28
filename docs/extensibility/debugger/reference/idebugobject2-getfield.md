---
title: IDebugObject2::GetField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 797a18b678e815411b7ea7860e44ea6159caa2b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872410"
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
Pobiera typ tego obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetField(
 IDebugField** ppField
);
```

```csharp
int GetField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parametry
 `ppField`

 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu w przeciwnym razie wartość null.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pole opisuje typ obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)