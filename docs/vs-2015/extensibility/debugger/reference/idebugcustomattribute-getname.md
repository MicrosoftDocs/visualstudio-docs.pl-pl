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
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62569273"
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

#### <a name="parameters"></a>Parametry
 `bstrName`

 [out] Zwraca ciąg zawierający nazwę atrybutu niestandardowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwracany przez tę metodę o nazwie odpowiada nazwie klasy używane do deklarowania atrybutu. Może nie dokładnie odpowiadać Nazwa klasy atrybutów niestandardowych, sama jak C# umożliwia sufiks "Atrybutu", który będzie można usunąć z nazwy atrybutu niestandardowego, gdy jest używany w deklaracji.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)