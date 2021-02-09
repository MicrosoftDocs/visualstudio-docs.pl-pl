---
title: GetValidCompatibleFramework, funkcja
description: Dowiedz się, jak interfejs API GetValidCompatibleFramework obsługuje infrastrukturę pakietu Office i nie jest przeznaczony do użycia bezpośrednio w kodzie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b089f954c59219461c8e267ee6e88e47015fc794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860623"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework, funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczony do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Nie używaj.|
|*pbstrValidFrameworkTag*|Nie używaj.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja nie powiedzie się, zwraca kod błędu.
