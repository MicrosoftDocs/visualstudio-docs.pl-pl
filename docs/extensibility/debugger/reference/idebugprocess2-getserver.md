---
description: Pobiera serwer, na którym jest uruchomiony ten proces.
title: 'IDebugProcess2:: getserver | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2bf0528526e20fc3eae7acf46dfc2b706be94eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081636"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Pobiera serwer, na którym jest uruchomiony ten proces.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetServer( 
   IDebugCoreServer2** ppServer
);
```

```csharp
int GetServer( 
   out IDebugCoreServer2 ppServer
);
```

## <a name="parameters"></a>Parametry
`ppServer`\
określoną Zwraca obiekt [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , który reprezentuje serwer, na którym jest uruchomiony ten proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Na jednej maszynie może działać więcej niż jeden serwer.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
