---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726242"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Pobiera pole lub zmienną (jeśli istnieje), która może tworzyć kopię zapasową Właściwości reprezentowanej przez ten obiekt.

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
określoną Obiekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) opisujący pole zapasowe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) reprezentuje właściwość klasy kodu zarządzanego, czyli metodę z akcesorem get i/lub Set. Takie właściwości zwykle wymagają zmiennej, aby zawierała wartość manipulowaną przez właściwość. Ta zmienna jest znana jako pole zapasowe. Jeśli nie ma pola zapasowego dla obiektu, upewnij się, że zwracana jest wartość null: niektóre obiekty wywołujące mogą nie zwracać uwagi na wartość zwracaną, ale zamiast tego sprawdzają, czy wartość null została zwrócona w `ppObject` .

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
