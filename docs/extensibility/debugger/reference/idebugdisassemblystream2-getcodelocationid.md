---
title: IDebugDisassemblyStream2::GetCodeLocationId | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58e3b12ecbc75b7d07d60ac399412dc5b0deb73b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351687"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Zwraca identyfikator lokalizacji kodu dla kontekstu określonego kodu.

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
[in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt ma zostać przekonwertowany na identyfikator.

`puCodeLocationId` [out] Zwraca identyfikator lokalizacji kodu. Zobacz uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_CODE_CONTEXT_OUT_OF_SCOPE` jeśli kontekst kodu jest prawidłowy, ale poza zakresem.

## <a name="remarks"></a>Uwagi
 Aparat debugowania (DE), obsługa demontaż dotyczy identyfikator lokalizacji kodu. Ten identyfikator lokalizacji jest używana wewnętrznie przez DE śledzenie pozycji w kodzie i jest zwykle adres lub przesunięcie pewnego rodzaju. Jedynym wymaganiem jest to, że jeśli kontekst kodu z jednej lokalizacji jest mniejsza niż kontekst kodu z innej lokalizacji, a następnie odpowiedni identyfikator kodu w lokalizacji, pierwszy kontekstu kodu również musi być mniejsza niż identyfikator lokalizacji kodu drugi kontekst kodu.

 Aby uzyskać kontekst kodu identyfikatora lokalizacji kodu, należy wywołać [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)