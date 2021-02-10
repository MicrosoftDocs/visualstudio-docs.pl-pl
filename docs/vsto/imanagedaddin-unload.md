---
title: IManagedAddin::Unload
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
ms.openlocfilehash: 7a36599259a38d0b9b8eb814a457b3625d593b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934601"
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
