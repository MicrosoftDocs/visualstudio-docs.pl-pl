---
description: Pobiera liczbę ciągów wartości do wyświetlenia dla określonej właściwości lub pola.
title: 'IEEVisualizerService:: GetValueDisplayStringCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f48ff7d513b211396c0eec28f5670bbe648f01b4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080245"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Pobiera liczbę ciągów wartości do wyświetlenia dla określonej właściwości lub pola.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parametry
`displayKind`\
podczas Wartość z wyliczenia [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) .

`propertyOrField`\
podczas Interfejs [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje właściwość lub pole.

`pcelt`\
określoną Zwraca liczbę ciągów wartości do wyświetlenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
