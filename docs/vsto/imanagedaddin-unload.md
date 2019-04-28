---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956747"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wywoływana tuż przed zarządzanych dodatku narzędzi VSTO dla programów nie jest załadowany.

## <a name="syntax"></a>Składnia

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest wywoływana przez bieżącej wersji pakietu Microsoft Office. Ta metoda jest zarezerwowana do użytku w przyszłości.

## <a name="see-also"></a>Zobacz także
- [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
