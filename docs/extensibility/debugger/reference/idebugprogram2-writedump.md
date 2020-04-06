---
title: IDebugProgram2::WriteDump | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722738"
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
[w] Wartość z wyliczenia [DUMPTYPE,](../../../extensibility/debugger/reference/dumptype.md) która określa typ zrzutu, na przykład krótki lub długi.

`pszDumpUrl`\
[w] Adres URL, do który chcesz zapisać zrzut. Zazwyczaj jest to w formie `file://c:\path\filename.ext`, ale może być dowolny prawidłowy adres URL.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zrzut programu zazwyczaj obejmują bieżącą ramkę stosu, sam stos, listę wątków uruchomionych w programie i ewentualnie dowolną pamięć, która jest właścicielem programu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
