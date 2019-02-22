---
title: GetValidCompatibleFramework function
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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643512"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework function
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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
|*lpwszCompatibleFrameworksXML*|Nie należy używać.|
|*pbstrValidFrameworkTag*|Nie należy używać.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja zawiedzie, zwraca kod błędu.
