---
title: Idiastackwalkhelper::imageforva — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36ad6529f28701d0e6d83550636382be773f0ec1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794337"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca początek obrazu pliku wykonywalnego w pamięci podany wirtualny adres gdzieś w obszarze pamięci pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vaContext`  
 [in] Wirtualny adres znajduje się gdzieś w miejscu do pliku wykonywalnego.  
  
 `pvaImageStart`  
 [out] Zwraca adres początkowy wirtualnego obrazu pliku wykonywalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
