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
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869310"
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
