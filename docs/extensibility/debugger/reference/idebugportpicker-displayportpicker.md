---
description: Wyświetla określone okno dialogowe, które umożliwia użytkownikowi wybranie portu.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072315"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Wyświetla określone okno dialogowe, które umożliwia użytkownikowi wybranie portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parametry
`hwndParentDialog`\
podczas Uchwyt dla nadrzędnego okna dialogowego.

`pbstrPortId`\
określoną Ciąg identyfikatora portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwracana wartość `S_FALSE` (lub wartość zwrotna z `S_OK` `BSTR` ustawioną na `NULL` ) wskazuje, że użytkownik kliknął **przycisk Anuluj**.

## <a name="see-also"></a>Zobacz też
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
