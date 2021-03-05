---
description: Wyświetla określone okno dialogowe, które umożliwia użytkownikowi wybranie portu.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c07e95343521692d41d045a89a4038f5ff64e7b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142560"
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
