---
title: IDebugProgram2::EnumCodeContexts | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77d92a65b77cbec94a6c74852393627af6763bad
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685394"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Pobiera listę konteksty kodu dla danego stanowiska w pliku źródłowym.

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

#### <a name="parameters"></a>Parametry
 `pDocPos`

 [in] [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) obiekt reprezentujący abstrakcyjne pozycji w pliku źródłowym, wiadomo, że środowisko IDE.

 `ppEnum`

 [out] Zwraca [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) obiekt, który zawiera listę konteksty kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia debugowania sesji manager (SDM) lub mapy pozycji w pliku źródłowego w miejscu kodu w środowisku IDE. Więcej niż jeden kontekst kodu jest zwracany, jeśli źródło generuje wiele bloków kodu (na przykład, szablony języka C++).

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)