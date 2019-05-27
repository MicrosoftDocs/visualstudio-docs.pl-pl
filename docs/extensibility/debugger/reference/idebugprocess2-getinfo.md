---
title: IDebugProcess2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2970a4d2c65c56ab2e16ca51dbca6556bee1d040
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202622"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Pobiera opis procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parametry
`Fields`\
[in] Kombinacja wartości z [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) wyliczenie, które określa, które pola `pProcessInfo` parametru są wypełniane.

`pProcessInfo`\
[out] A [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) strukturę, która jest wypełniane opis procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)