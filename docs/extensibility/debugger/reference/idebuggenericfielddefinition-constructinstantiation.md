---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f7ecfc79cc2a4279a8ca0fccfc527ef63e603b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313215"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Tworzy wystąpienie pola, biorąc pod uwagę tablicę argumentów typu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parametry
`cArgs`\
[in] Liczba argumentów w `ppArgs` tablicy.

`ppArgs`\
[in] Tablica, która zawiera argumenty typu. Argumenty typu muszą być zamknięte typy (Ogólne nieogólnego lub w pełni utworzona).

`ppConstructedField`\
[out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejs, który reprezentuje nowe pole.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ograniczenia nie są sprawdzane.

## <a name="see-also"></a>Zobacz także
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)