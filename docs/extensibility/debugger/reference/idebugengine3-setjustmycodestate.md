---
title: 'IDebugEngine3:: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e706d0fd23bc0c5388ee3bd6bb82323309725c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887188"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Ta metoda informuje aparat debugowania o informacjach o stanie JustMyCode.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametry
`fUpdate`\
podczas Różna od zera ( `TRUE` ) w celu zaktualizowania bieżących informacji, zero ( `FALSE` ) w celu zresetowania wszystkich informacji (ignorowanie wcześniej ustawionych).

`dwModules`\
podczas Liczba struktur informacji w `rgJMCSpec.`

`rgJMCSpec`\
podczas Tablica struktur [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) do użycia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 JustMyCode to koncepcja debugowania tylko kodu, który należy do użytkownika, i ignorowanie całego kodu pośredniego, takiego jak kod systemowy — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.

## <a name="see-also"></a>Zobacz też
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
