---
title: IDebugFunctionObject::CreateArrayObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7ee5d4a59442238b461361522b06087650547b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685147"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Tworzy obiekt, tablica. Ta tablica mogą zawierać albo podstawowego lub wartości wystąpienia obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parametry
 `ot`

 [in] Określa wartość z zakresu od [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Wyliczenie wskazujące typ obiektu nowej tablicy.

 `pClassField`

 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący klasę obiektu, w przypadku tworzenia tablicę obiektów, wartości wystąpień. W przypadku tworzenia tablicy obiektów pierwotnych, ten parametr jest wartością null.

 `dwRank`

 [in] Ranga lub liczba wymiarów tablicy.

 `dwDims`

 [in] Rozmiary każdego wymiaru tablicy.

 `dwLowBounds`

 [in] Źródło każdego wymiaru (zazwyczaj 0 lub 1).

 `ppObject`

 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący nowo utworzona tablica. Jest to rzeczywiście [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje parametr tablicowy do funkcji, która jest reprezentowana przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)