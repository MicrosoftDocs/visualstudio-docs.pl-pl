---
description: Porównuje jedno odwołanie z drugim.
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 017dfa60c1f854a36f1087bef87203f0b22ae4dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083638"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Porównuje jedno odwołanie z drugim. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parametry
`dwCompare`\
podczas Wartość z wyliczenia [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) , która określa operacje porównania, na przykład równe, mniejsze niż lub większe niż.

`pReference`\
podczas Obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) reprezentujący odwołanie, które ma zostać porównane z.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
