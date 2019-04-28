---
title: IDebugProperty::GetParent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aeac5e23ec38aa79e5ff5057847429ac97dbb23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979139"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Pobiera właściwość nadrzędna właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParent`  
 [out] Zwraca `IDebugProperty` interfejs, który reprezentuje element nadrzędny właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)