---
description: Zwraca odwołanie do wartości właściwości.
title: 'IDebugProperty2:: GetReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c103e8826266ddbaaa5b96f4a9aa32067893e45f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166790"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Zwraca odwołanie do wartości właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>Parametry
`ppRererence`\
określoną Zwraca obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) reprezentujący odwołanie do wartości właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu, zwykle `E_NOTIMPL` lub `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
