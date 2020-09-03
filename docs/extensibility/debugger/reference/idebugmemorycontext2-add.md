---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727482"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Dodaje określoną wartość do bieżącego kontekstu i zwraca nowy kontekst.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
podczas Wartość, która ma zostać dodana do bieżącego kontekstu.

`ppMemCxt`\
określoną Zwraca nowy obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst pamięci jest adresem, więc dodanie wartości do adresu powoduje utworzenie nowego adresu, który wymaga nowego interfejsu kontekstu.

 Ta metoda musi zawsze generować nowy kontekst, nawet jeśli otrzymany adres znajduje się poza przestrzenią pamięci skojarzoną z tym kontekstem. Jedynym wyjątkiem jest to, że nie można przydzielić pamięci dla nowego kontekstu lub jeśli `ppMemCxt` jest wartością null (która jest błędem).

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
