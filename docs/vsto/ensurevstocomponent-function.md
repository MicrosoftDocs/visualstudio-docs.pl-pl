---
title: Ensurevstocomponent — funkcja
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f99ccb4cb76f942852716abf1fcb0c0f280decbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797615"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent — funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pProject*|Nie należy używać.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja zawiedzie, zwraca kod błędu.
