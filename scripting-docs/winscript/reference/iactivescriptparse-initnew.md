---
title: IActiveScriptParse::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148951"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicjuje aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Przed użyciem silnik wykonywania skryptów, jedną z następujących metod musi zostać wywołana: `IPersist*::Load`, `IPersist*::InitNew`, lub `IActiveScriptParse::InitNew`. Semantyka tej metody są takie same jak `IPersistStreamInit::InitNew`, w tym, że ta metoda informuje silnik wykonywania skryptów do zainicjowania. Należy pamiętać, że nie można wywołać oba `IPersist*::InitNew` lub `IActiveScriptParse::InitNew` i `IPersist*::Load`, ani nie jest prawidłowy do wywołania `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, lub `IPersist*::Load` więcej niż jeden raz.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)