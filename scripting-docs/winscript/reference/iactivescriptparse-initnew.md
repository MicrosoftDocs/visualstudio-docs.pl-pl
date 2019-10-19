---
title: 'IActiveScriptParse:: InitNew | Microsoft Docs'
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
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573511"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicjuje aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_FAIL`, jeśli wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Aby można było użyć aparatu skryptów, należy wywołać jedną z następujących metod: `IPersist*::Load`, `IPersist*::InitNew` lub `IActiveScriptParse::InitNew`. Semantyka tej metody jest taka sama jak `IPersistStreamInit::InitNew`, w którym ta metoda Instruuje aparat skryptów do zainicjowania samego siebie. Należy zauważyć, że nie można wywoływać zarówno `IPersist*::InitNew`, jak i `IActiveScriptParse::InitNew` i `IPersist*::Load`, ani nie jest prawidłowym wywołaniem `IPersist*::InitNew`, `IActiveScriptParse::InitNew` lub `IPersist*::Load` więcej niż raz.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)