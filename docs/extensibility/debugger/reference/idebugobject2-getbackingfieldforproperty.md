---
title: IDebugObject2::GetBackingFieldForProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9aaf4111670ad67f6a01bde60bf5f35c3b793983
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317348"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Pobiera pola lub zmiennej (jeśli istnieje), mogą tworzyć kopię właściwość reprezentowany przez ten obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
[out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Obiekt opisujący pola pomocniczego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) obiekt reprezentuje właściwość klasy kodu zarządzanego, oznacza to, że metoda pobieranie i/lub ustawiająca metoda dostępu. Takie właściwości zwykle wymagają zmiennej, by zawierała wartość manipulowane przez właściwość. Ta zmienna jest określany jako pola pomocniczego. W przypadku nie pole zapasowe dla obiektu, następnie upewnij się zwrócić wartość null: niektóre obiekty wywołujące nie może zwrócić uwagę na wartości zwracanej, ale zamiast tego będzie wyglądać aby zobaczyć, jeśli wartości null został zwrócony w `ppObject`.

## <a name="see-also"></a>Zobacz także
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)