---
title: IDebugObject2::GetBackingFieldForProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c74b99c1ca4895cb5e930fa7f17ec21a5db61cff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954517"
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
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Obiekt opisujący pola pomocniczego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) obiekt reprezentuje właściwość klasy kodu zarządzanego, oznacza to, że metoda pobieranie i/lub ustawiająca metoda dostępu. Takie właściwości zwykle wymagają zmiennej, by zawierała wartość manipulowane przez właściwość. Ta zmienna jest określany jako pola pomocniczego. W przypadku nie pole zapasowe dla obiektu, następnie upewnij się zwrócić wartość null: niektóre obiekty wywołujące nie może zwrócić uwagę na wartości zwracanej, ale zamiast tego będzie wyglądać aby zobaczyć, jeśli wartości null został zwrócony w `ppObject`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)