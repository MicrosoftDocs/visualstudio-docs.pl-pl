---
description: Przenosi wskaźnik odczytu w strumieniu demontażu przez daną liczbę instrukcji względem określonego położenia.
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02277bf84bdc12e904b2651ef5ba9fc2356d9090
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066935"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Przenosi wskaźnik odczytu w strumieniu demontażu przez daną liczbę instrukcji względem określonego położenia.

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
podczas Wartość z wyliczenia [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) , która określa położenie względne, aby rozpocząć proces wyszukiwania.

`pCodeContext`\
podczas Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący kontekst kodu, do którego odnosi się operacja wyszukiwania. Ten parametr jest używany tylko wtedy `dwSeekStart`  =  `SEEK_START_CODECONTEXT` , gdy; w przeciwnym razie ten parametr jest ignorowany i może być wartością null.

`uCodeLocationId`\
podczas Identyfikator lokalizacji kodu, względem której odnosi się operacja wyszukiwania. Ten parametr jest używany `dwSeekStart`  =  `SEEK_START_CODELOCID` , jeśli; w przeciwnym razie ten parametr jest ignorowany i może być ustawiony na 0. Zapoznaj się z sekcją spostrzeżenia metody [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) , aby uzyskać opis identyfikatora lokalizacji kodu.

`iInstructions`\
podczas Liczba instrukcji do przeniesienia względem położenia określonego w `dwSeekStart` . Ta wartość może być ujemna, aby przenieść do tyłu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy pozycja wyszukiwania była w punkcie poza listą dostępnych instrukcji. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli wyszukiwanie dotyczyło pozycji przed początkiem listy, pozycja odczytu jest ustawiana na pierwszą instrukcję na liście. Jeśli punkt widzenia był w pozycji po końcu listy, pozycja odczytu jest ustawiana na ostatnią instrukcję na liście.

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
