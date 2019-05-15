---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12be8b3999639c69d479412e673b0e049629172
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615153"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Pobiera identyfikator procesu, który jest właścicielem obiektu reprezentowanego przez to [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Parametry
`pProcID`\
[out] Identyfikator procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)