---
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732404"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Ta metoda pobiera interfejs [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) dla tego portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
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
