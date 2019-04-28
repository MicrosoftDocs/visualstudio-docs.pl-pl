---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009427"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicjuje aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Przed użyciem silnik wykonywania skryptów, jedną z następujących metod musi zostać wywołana: `IPersist*::Load`, `IPersist*::InitNew`, lub `IActiveScriptParse32::InitNew`. Semantyka tej metody są takie same jak `IPersistStreamInit::InitNew`, w tym, że ta metoda informuje silnik wykonywania skryptów do zainicjowania. Należy pamiętać, że nie można wywołać oba `IPersist*::InitNew` lub `IActiveScriptParse32::InitNew` i `IPersist*::Load`, ani nie jest prawidłowy do wywołania `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, lub `IPersist*::Load` więcej niż jeden raz.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)