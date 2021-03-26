---
description: Pobiera listę kontekstów kodu dla danego położenia w pliku źródłowym.
title: 'IDebugProgram2:: EnumCodeContexts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dbcc3f967f0569efcfc1287ba2b215760ce0b34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076059"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Pobiera listę kontekstów kodu dla danego położenia w pliku źródłowym.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`pDocPos`\
podczas Obiekt [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) reprezentujący pozycję abstrakcyjną w pliku źródłowym znanym przez IDE.

`ppEnum` określoną Zwraca obiekt [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) , który zawiera listę kontekstów kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia menedżerowi debugowania sesji (SDM) lub IDE mapowanie pozycji w pliku źródłowym na pozycję kodu. Jeśli źródło generuje wiele bloków kodu (na przykład szablonów C++), zwracany jest więcej niż jeden kontekst kodu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
