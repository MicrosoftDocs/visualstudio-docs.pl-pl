---
title: IManagedAddin::Unload
description: Wywoływana tuż przed załadowaniem zarządzanego dodatku VSTO.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469713"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wywoływana tuż przed załadowaniem zarządzanego dodatku VSTO.

## <a name="syntax"></a>Składnia

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Wartość zwracana
 Wartość HRESULT wskazująca, czy metoda została ukończona pomyślnie.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest wywoływana przez bieżące wersje Microsoft Office. Ta metoda jest zarezerwowana do użytku w przyszłości.

## <a name="see-also"></a>Zobacz też
- [IManagedAddin —, interfejs](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
