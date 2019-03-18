---
title: IDebugApplication::FCanJitDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d5dc03d7d2511f5b50969c062104759e78fcf03
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159013"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Określa, czy debuger just in time (JIT) jest zarejestrowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, a zarejestrowany jest debugera JIT, metoda zwraca `TRUE`. W przeciwnym razie zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy jest zarejestrowany debugera JIT.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)