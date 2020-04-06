---
title: IDebugDisassemblyStream2::Szukaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732087"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Przenosi wskaźnik odczytu w demontażu strumienia danej liczby instrukcji względem określonej pozycji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parametry
`dwSeekStart`\
[w] Wartość z [wyliczenia SEEK_START,](../../../extensibility/debugger/reference/seek-start.md) która określa względną pozycję, aby rozpocząć proces wyszukiwania.

`pCodeContext`\
[w] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt reprezentujący kontekst kodu, który operacja seek jest względem. Ten parametr jest `dwSeekStart`  =  `SEEK_START_CODECONTEXT`używany tylko wtedy, gdy ; w przeciwnym razie ten parametr jest ignorowany i może być wartością null.

`uCodeLocationId`\
[w] Identyfikator lokalizacji kodu, z którym jest wyjęła operacja wyszukiwania. Ten parametr jest `dwSeekStart`  =  `SEEK_START_CODELOCID`używany, jeśli ; w przeciwnym razie ten parametr jest ignorowany i można go ustawić na 0. Zobacz uwagi sekcji [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metody opis identyfikatora lokalizacji kodu.

`iInstructions`\
[w] Liczba instrukcji do przesuń względem `dwSeekStart`pozycji określonej w . Ta wartość może być ujemna, aby przejść do tyłu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . Zwraca, `S_FALSE` jeśli pozycja wyszukiwania była do punktu poza listą dostępnych instrukcji. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli seek był do pozycji przed rozpoczęciem listy, pozycja odczytu jest ustawiona na pierwszą instrukcję na liście. Jeśli see był do pozycji po zakończeniu listy, pozycja odczytu jest ustawiona na ostatnią instrukcję na liście.

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
