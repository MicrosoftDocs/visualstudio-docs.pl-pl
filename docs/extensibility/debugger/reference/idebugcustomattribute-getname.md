---
title: IDebugCustomAttribute::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2556a424e5109e75b667e9f32ecac5cc26ca781b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205337"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Pobiera nazwę atrybutu niestandardowego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parametry
`bstrName`\
[out] Zwraca ciąg zawierający nazwę atrybutu niestandardowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwracany przez tę metodę o nazwie odpowiada nazwie klasy używane do deklarowania atrybutu. Może nie dokładnie odpowiadać Nazwa klasy atrybutów niestandardowych, sama jak C# umożliwia sufiks "Atrybutu", który będzie można usunąć z nazwy atrybutu niestandardowego, gdy jest używany w deklaracji.

## <a name="see-also"></a>Zobacz także
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)