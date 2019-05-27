---
title: IDebugDisassemblyStream2::GetScope | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a9da518d36c570bd53fa44118972366f9bf6ab4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204944"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
Pobiera zakres strumienia dezasemblacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetScope( 
   DISASSEMBLY_STREAM_SCOPE* pdwScope
);
```

```csharp
int GetScope( 
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope
);
```

## <a name="parameters"></a>Parametry
`pdwScope`\
[out] Zwraca wartość z zakresu od [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) wyliczenie opisujące zakres ten strumień dezasemblacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakres dezasemblacji może być na przykład funkcję lub całego modułu.

## <a name="see-also"></a>Zobacz także
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)