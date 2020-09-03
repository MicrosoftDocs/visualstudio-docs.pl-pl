---
title: 'IDebugMemoryContext2:: Odejmij | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727436"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Odejmuje określoną wartość z bieżącego kontekstu i zwraca nowy kontekst.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
podczas Liczba bajtów pamięci do zmniejszenia.

`ppMemCxt`\
określoną Zwraca nowy obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst pamięci to adres, więc odjęcie wartości od adresu powoduje utworzenie nowego adresu, który wymaga nowego interfejsu kontekstu.

 Ta metoda musi zawsze generować nowy kontekst, nawet jeśli otrzymany adres znajduje się poza przestrzenią pamięci skojarzoną z tym kontekstem. Jedynym wyjątkiem jest to, że nie można przydzielić pamięci dla nowego kontekstu lub jeśli `ppMemCxt` jest wartością null (która jest błędem).

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
