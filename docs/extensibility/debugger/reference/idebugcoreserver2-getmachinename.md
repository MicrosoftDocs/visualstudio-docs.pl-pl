---
description: Pobiera nazwę komputera, na którym jest uruchomiony serwer podstawowy.
title: 'IDebugCoreServer2:: GetMachineName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetName
helpviewer_keywords:
- IDebugCoreServer2::GetName
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1577ca12ca2fa0ed7d626907e925ec6c3fcddc31
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077892"
---
# <a name="idebugcoreserver2getmachinename"></a>IDebugCoreServer2::GetMachineName
Pobiera nazwę komputera, na którym jest uruchomiony serwer podstawowy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
określoną Zwraca ciąg zawierający nazwę komputera.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
