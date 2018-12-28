---
title: Ensurevstocomponent — funkcja
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39dcdcc5e3b8e6e5bc5834e7e05ea22516d8c7e6
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648616"
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
  
  