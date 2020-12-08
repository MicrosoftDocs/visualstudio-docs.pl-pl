---
title: EnsureVSTOComponent, funkcja
description: Dowiedz się, jak interfejs API EnsureVSTOComponent obsługuje infrastrukturę pakietu Office i nie jest przeznaczony do użycia bezpośrednio w kodzie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04cfc249efa4640df2b2e4b1c5f4b43ed52ace2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846119"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent, funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczony do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pProject*|Nie używaj.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja nie powiedzie się, zwraca kod błędu.
