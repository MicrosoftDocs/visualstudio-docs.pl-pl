---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835709"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicjuje aparat skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość `S_OK` , jeśli powodzenie lub `E_FAIL` Wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Aby można było użyć aparatu skryptów, należy wywołać jedną z następujących metod: `IPersist*::Load` , `IPersist*::InitNew` , lub `IActiveScriptParse32::InitNew` . Semantyka tej metody jest taka sama jak `IPersistStreamInit::InitNew` w przypadku, gdy ta metoda Instruuje aparat skryptów do zainicjowania samego siebie. Należy zauważyć, że nie jest prawidłowe wywoływanie metody `IPersist*::InitNew` lub `IActiveScriptParse32::InitNew` i, ani nie jest to dozwolone `IPersist*::Load` `IPersist*::InitNew` , `IActiveScriptParse32::InitNew` lub `IPersist*::Load` więcej niż jeden raz.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)