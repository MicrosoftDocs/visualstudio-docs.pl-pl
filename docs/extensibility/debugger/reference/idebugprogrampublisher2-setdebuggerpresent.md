---
title: IDebugProgramPublisher2::SetDebuggerPresent | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 402a9a65344af02dd4c321f4a1e449b012af36ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343304"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Informuje wydawca programu, że debuger jest obecna i uruchomiona.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Parametry
`fDebuggerPresent`\
[in] Niezerowa Koniunkcja (`TRUE`) jest obecny debuger, wartość zero (`FALSE`) Jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obecność lub brak debugera jest widoczny w danych zwracanych przez [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metoda: wartość zwracana jest ustawiony lub wyczyścić przy wywołaniu `SetDebuggerPresent` metody.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)