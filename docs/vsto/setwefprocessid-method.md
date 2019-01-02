---
title: SetWefProcessId, metoda
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3ccce49992073f11245929bf7af0b966537bd079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886153"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId, metoda
  Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*dwProcessId*|Identyfikator procesu, który będzie służyć do uruchamiania WEF zawartości.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda musi zostać wywołana, po utworzeniu procesu zawartości WEF, ale przed uruchomieniem żadnej zawartości WEF.  
  
 Jeśli chcesz dołączyć debuger do procesu zawartości WEF przez środowisko deweloperskie, środowisko musi wykonać tej operacji w danej implementacji tej metody.  
