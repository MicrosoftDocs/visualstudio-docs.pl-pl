---
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896152"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Zapisuje zrzut do pliku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parametry
`DumpType`\
podczas Wartość z wyliczenia [dumptype](../../../extensibility/debugger/reference/dumptype.md) , która określa typ zrzutu, na przykład short lub Long.

`pszDumpUrl`\
podczas Adres URL, na który ma zostać zapisany zrzut. Zwykle jest to w postaci `file://c:\path\filename.ext` , ale może być dowolnym prawidłowym adresem URL.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zrzut programu zwykle obejmuje bieżącą ramkę stosu, sam stos, listę wątków uruchomionych w programie, a także dowolną ilość pamięci, której właścicielem jest program.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
