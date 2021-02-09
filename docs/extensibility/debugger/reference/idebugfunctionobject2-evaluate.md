---
title: 'IDebugFunctionObject2:: oszacowanie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b7d69434a6bd6aefb073a252ee35c07fccbee6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920972"
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
podczas Tablica obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , która reprezentuje parametry wejściowe. Każdy z tych parametrów został utworzony przy użyciu jednej z metod tworzenia w tym interfejsie.

`dwParams`\
podczas Liczba parametrów w `ppParams` tablicy.

`dwEvalFlags`\
podczas Kombinacja flag z wyliczenia [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , która określa, w jaki sposób ma być przeprowadzana Ocena.

`dwTimeout`\
podczas Określa maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Używaj **nieskończoności** , aby czekać w nieskończoność.

`ppResult`\
określoną Zwraca element **IDebugObject** , który reprezentuje wartość funkcji jako obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
