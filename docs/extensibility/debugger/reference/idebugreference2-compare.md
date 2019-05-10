---
title: IDebugReference2::Compare | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df878cc59a47a8d3cc7079f8b919f87d9bb60f43
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457481"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Porównuje jedno odwołanie do innego. Zarezerwowane do użytku w przyszłości.

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

 [in] Wartość z zakresu od [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) wyliczenie, które określa operacji porównania, na przykład taki sam, mniej niż lub równy.

 `pReference`\

 [in] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt reprezentujący odwołania do porównania.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)