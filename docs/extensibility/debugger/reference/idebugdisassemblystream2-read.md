---
description: Odczytuje instrukcje zaczynające się od bieżącej pozycji w strumieniu demontażu.
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcabd0cc42f013b579ee32deeb33d68cd9d45f5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066922"
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
podczas Liczba instrukcji do rozbudowy. Ta wartość jest również maksymalną długością `prgDisassembly` tablicy.

`dwFields`\
podczas Kombinacja flag z wyliczenia [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , która wskazuje, które pola `prgDisassembly` są wypełniane.

`pdwInstructionsRead`\
określoną Zwraca liczbę instrukcji, które są w rzeczywistości odłączone.

`prgDisassembly`\
określoną Tablica struktur [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) , które są wypełniane za pomocą rozbudowanego kodu, jednej struktury na odłączonej instrukcji. Długość tej tablicy jest określana przez `dwInstructions` parametr.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Maksymalną liczbę instrukcji, które są dostępne w bieżącym zakresie, można uzyskać przez wywołanie metody [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .

 Bieżącą pozycję, z której ma zostać odczytana Następna instrukcja, można zmienić, wywołując metodę [wyszukiwania](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

 `DSF_OPERANDS_SYMBOLS`Flagę można dodać do `DSF_OPERANDS` flagi w `dwFields` parametrze, aby wskazać, że nazwy symboli mają być używane podczas odbudowy instrukcji.

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
