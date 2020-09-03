---
title: GetValidCompatibleFramework, funkcja
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
ms.openlocfilehash: 2219417fe8ddae3d11d0e624ad12d3de80e290dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520227"
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
