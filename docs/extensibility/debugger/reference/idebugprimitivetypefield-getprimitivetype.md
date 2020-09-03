---
title: 'IDebugPrimitiveTypeField:: getpierwotntype | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a66c7c2e312795fa4303c8702e70cd509536de98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724280"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Pobiera typ pierwotny, który jest skojarzony z tym polem.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPrimitiveType (
   DWORD* pdwType
);
```

```csharp
int GetPrimitiveType (
   out uint pdwType
);
```

## <a name="parameters"></a>Parametry
`pdwType`\
określoną Wartość z [wyliczenia CorElementType —](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , która reprezentuje typ pierwotny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` .

## <a name="see-also"></a>Zobacz też
- [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
