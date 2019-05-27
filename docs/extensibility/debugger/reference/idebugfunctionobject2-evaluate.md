---
title: IDebugFunctionObject2::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cd9aafd9157f6d14bb7d37f4ba0301485a35991
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200683"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Wywołuje funkcję i zwraca wartość wynikowa jako obiekt.

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
[in] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów, które reprezentuje parametrów wejściowych. Każdy z tych parametrów, który został utworzony przy użyciu jednej z metod tworzenia w tym interfejsie.

`dwParams`\
[in] Liczba parametrów w `ppParams` tablicy.

`dwEvalFlags`\
[in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie określające sposób oceny ma zostać wykonane.

`dwTimeout`\
[in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj **NIESKOŃCZONEJ** czekanie w nieskończoność.

`ppResult`\
[out] Zwraca **IDebugObject** reprezentujący wartość funkcji jako obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)