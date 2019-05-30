---
title: IDebugEngine2::SetRegistryRoot | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f30a2fe4a239b76d9eb984cdc4cea6485b8dd5d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352503"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Ustawia katalog główny rejestru dla aparatu debugowania (DE).

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>Parametry
`pszRegistryRoot`\
[in] Katalog główny rejestru do użycia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Aby określić alternatywne Rejestr główny, który DE powinna być używana do uzyskania ustawień rejestru; na przykład "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)