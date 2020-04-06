---
title: Identyfikator IDebugDisassemblyStream2::GetCodeLocationId | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732252"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Zwraca identyfikator lokalizacji kodu dla określonego kontekstu kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parametry
`pCodeContext`\
[w] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt do konwersji na identyfikator.

`puCodeLocationId`[na zewnątrz] Zwraca identyfikator lokalizacji kodu. Zobacz uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca, `E_CODE_CONTEXT_OUT_OF_SCOPE` jeśli kontekst kodu jest prawidłowy, ale poza zakresem.

## <a name="remarks"></a>Uwagi
 Identyfikator lokalizacji kodu jest specyficzny dla aparatu debugowania (DE) obsługującego demontaż. Ten identyfikator lokalizacji jest używany wewnętrznie przez DE do śledzenia pozycji w kodzie i jest zazwyczaj adresem lub przesunięciem pewnego rodzaju. Jedynym wymaganiem jest to, że jeśli kontekst kodu jednej lokalizacji jest mniejsza niż kontekst kodu innej lokalizacji, odpowiedni identyfikator lokalizacji kodu pierwszego kontekstu kodu musi być również mniejszy niż identyfikator lokalizacji kodu drugiego kontekstu kodu.

 Aby pobrać kontekst kodu identyfikatora lokalizacji kodu, należy wywołać [Metodę GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
