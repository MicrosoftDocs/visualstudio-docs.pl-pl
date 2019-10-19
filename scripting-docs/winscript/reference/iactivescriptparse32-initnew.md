---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
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
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561660"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicjuje aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_FAIL`, jeśli wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Aby można było użyć aparatu skryptów, należy wywołać jedną z następujących metod: `IPersist*::Load`, `IPersist*::InitNew` lub `IActiveScriptParse32::InitNew`. Semantyka tej metody jest taka sama jak `IPersistStreamInit::InitNew`, w którym ta metoda Instruuje aparat skryptów do zainicjowania samego siebie. Należy zauważyć, że nie można wywoływać zarówno `IPersist*::InitNew`, jak i `IActiveScriptParse32::InitNew` i `IPersist*::Load`, ani nie jest prawidłowym wywołaniem `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` lub `IPersist*::Load` więcej niż raz.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)