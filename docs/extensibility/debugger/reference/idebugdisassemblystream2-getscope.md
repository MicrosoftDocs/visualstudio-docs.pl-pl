---
title: 'IDebugDisassemblyStream2:: GetScope | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 222a3b2c6110f1998a4848f382694b6b999cd632
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732131"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
Pobiera zakres strumienia demontażu.

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
określoną Zwraca wartość z wyliczenia [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , która opisuje zakres tego strumienia rozdzielania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakresem demontażu może być funkcja lub cały moduł, na przykład.

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
