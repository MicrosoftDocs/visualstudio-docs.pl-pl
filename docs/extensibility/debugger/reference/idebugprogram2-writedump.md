---
description: Zapisuje zrzut do pliku.
title: 'IDebugProgram2:: WriteDump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8eca50eb6e828841a247ed51d7f73f61cb63e0e9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084431"
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
