---
title: IDebugEngine2::GetEngineID | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29b6f219447e3c58bce9f5b4696697163ab4f6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318473"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Pobiera identyfikator GUID aparat debugowania (DE).

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametry
`pguidEngine`\
[out] Zwraca identyfikator GUID DE.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Oto kilka przykładów typowych identyfikatorów GUID `guidScriptEng`, `guidNativeEng`, lub `guidSQLEng`. Nowe aparaty debugowania spowoduje utworzenie własnych identyfikator GUID do identyfikacji.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CEngine` obiekt, który implementuje [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
