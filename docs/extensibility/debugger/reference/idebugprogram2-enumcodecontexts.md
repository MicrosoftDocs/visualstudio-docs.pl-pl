---
title: 'IDebugProgram2:: EnumCodeContexts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22a5ce398e76ee97b2f0448900fd4e38f996615
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723053"
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
