---
title: IDebugReference2::Porównaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720642"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Porównuje jedno odwołanie do drugiego. Zarezerwowane do użytku w przyszłości.

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
[w] Wartość z [wyliczenia REFERENCE_COMPARE,](../../../extensibility/debugger/reference/reference-compare.md) która określa operację porównania, na przykład, równa, mniejsza niż lub większa niż.

`pReference`\
[w] [Obiekt IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) reprezentujący odwołanie, z którego należy porównać.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
