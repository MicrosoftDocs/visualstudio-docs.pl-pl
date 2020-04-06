---
title: IDebugFunctionObject2::Ocena | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728448"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Wywołuje funkcję i zwraca wynikową wartość jako obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[w] Tablica [obiektów IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) która reprezentuje parametry wejściowe. Każdy z tych parametrów został utworzony przy użyciu jednej z Metody Tworzenia w tym interfejsie.

`dwParams`\
[w] Liczba parametrów w `ppParams` tablicy.

`dwEvalFlags`\
[w] Kombinacja flag z [wyliczenia EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) które określają sposób wykonywania oceny.

`dwTimeout`\
[w] Określa maksymalny czas oczekiwania w milisekundach przed zwróceniem z tej metody. Użyj **INFINITE** czekać przez czas nieokreślony.

`ppResult`\
[na zewnątrz] Zwraca **obiekt IDebugObject** reprezentujący wartość funkcji jako obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
