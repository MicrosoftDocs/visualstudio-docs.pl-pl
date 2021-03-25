---
description: Ta metoda pobiera interfejs IDebugPortNotify2 dla tego portu.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077476"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Ta metoda pobiera interfejs [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) dla tego portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametry
`ppPortNotify`\
określoną Obiekt [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle `QueryInterface` Metoda jest wywoływana na obiekcie implementującym Interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , aby uzyskać Interfejs [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Jednak istnieją sytuacje, w których żądany interfejs jest implementowany w innym obiekcie. Ta metoda ukrywa te sytuacje i zwraca `IDebugPortNotify2` interfejs z najbardziej odpowiedniego obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
