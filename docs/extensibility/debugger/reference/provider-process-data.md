---
title: PROVIDER_PROCESS_DATA | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18b60d68b8c36c1d0c4fcd2a90e25732108460ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347238"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Ta struktura zawiera informacje dotyczące procesów uruchomionych na maszynie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Elementy członkowskie
 `Fields`\
 Kombinacja flag z [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) wyliczenie, wskazujące, które pola są wypełniane.

 `ProgramNodes`\
 A [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) strukturę, która zawiera tablicę węzły programu.

 `fIsDebuggerPresent`\
 Wartość różną od zera (`TRUE`) Jeśli [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debuger działa zero (`FALSE`) Jeśli nie jest.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywany do [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metody, gdzie jest wypełnione.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)