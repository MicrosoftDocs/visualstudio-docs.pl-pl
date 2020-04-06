---
title: IDebugDisassemblyStream2::Czytaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732094"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Odczytuje instrukcje zaczynające się od bieżącej pozycji w strumieniu demontażu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parametry
`dwInstructions`\
[w] Liczba instrukcji do demontażu. Ta wartość jest również maksymalną długością tablicy. `prgDisassembly`

`dwFields`\
[w] Kombinacja flag z wyliczenia [DISASSEMBLY_STREAM_FIELDS,](../../../extensibility/debugger/reference/disassembly-stream-fields.md) które wskazują, `prgDisassembly` które pola mają być wypełnione.

`pdwInstructionsRead`\
[na zewnątrz] Zwraca liczbę instrukcji faktycznie zdemontowanych.

`prgDisassembly`\
[na zewnątrz] Tablica [disassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktur, który jest wypełniony zdemontowany kod, jedna struktura na zdemontowane instrukcji. Długość tej tablicy jest podyktowana parametrem. `dwInstructions`

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Maksymalną liczbę instrukcji, które są dostępne w bieżącym zakresie można uzyskać, wywołując [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) metody.

 Bieżąca pozycja, w której odczytywana jest następna instrukcja, można zmienić, wywołując [metodę Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

 Flagę `DSF_OPERANDS_SYMBOLS` można dodać `DSF_OPERANDS` do flagi `dwFields` w parametrze, aby wskazać, że nazwy symboli powinny być używane podczas demontażu instrukcji.

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
