---
title: 'IDebugDisassemblyStream2:: GetCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6b3864528ee90c22a1e7122eeaf1969f613cc8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732284"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Zwraca obiekt kontekstu kodu odpowiadający określonemu identyfikatorowi lokalizacji kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametry
`uCodeLocationId`\
podczas Określa identyfikator lokalizacji kodu. Zapoznaj się z sekcją spostrzeżenia metody [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) , aby uzyskać opis identyfikatora lokalizacji kodu.

`ppCodeContext`\
określoną Zwraca obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który reprezentuje kontekst kodu skojarzonego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator lokalizacji kodu można zwrócić z wywołania metody [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) i może występować w strukturze [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

 Aby skonwertować kontekst kodu do identyfikatora lokalizacji kodu, wywołaj metodę [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
