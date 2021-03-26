---
description: Pobiera identyfikator GUID dla tego procesu.
title: 'IDebugProcess2:: GetProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b42b6f029ee6bbffdb1c59c55a2781d87d450d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081753"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Pobiera identyfikator GUID dla tego procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parametry
`pguidProcessId`\
określoną Zwraca identyfikator GUID dla tego procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Unikatowy identyfikator globalny (GUID) identyfikuje ten proces ze wszystkich innych procesów uruchomionych w systemie.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
