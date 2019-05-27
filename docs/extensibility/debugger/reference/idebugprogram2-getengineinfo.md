---
title: IDebugProgram2::GetEngineInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1b03fe660cd6b909c1d86871556e4f0e6ecb945
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212298"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Pobiera nazwę i identyfikator GUID aparat debugowania (DE), program został uruchomiony.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>Parametry
`pbstrEngine`\
[out] Zwraca nazwę DE program został uruchomiony.

`pguidEngine`\
[out] Zwraca identyfikator GUID DE program został uruchomiony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 DE każdy definiuje swój własny identyfikator GUID do identyfikacji.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)