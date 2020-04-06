---
title: IDebugPortPicker::DisplayPortPicker | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724892"
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
[w] Uchwyt dla nadrzędnego okna dialogowego.

`pbstrPortId`\
[na zewnątrz] Ciąg identyfikatora portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwracana wartość `S_FALSE` (lub zwracana `S_OK` wartość `BSTR` z `NULL`ustawionym na) wskazuje, że użytkownik kliknął **przycisk Anuluj**.

## <a name="see-also"></a>Zobacz też
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
