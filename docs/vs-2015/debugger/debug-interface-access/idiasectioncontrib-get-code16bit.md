---
title: 'IDiaSectionContrib:: get_code16bit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aceb4956b7ce2517087511676ebeff2b061b673
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576991"
---
# <a name="idiasectioncontribget_code16bit"></a>IDiaSectionContrib::get_code16bit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę wskazującą, czy sekcja zawiera kod 16-bitowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca `TRUE` czy kod w sekcji jest 16-bitowy; w przeciwnym razie zwraca `FALSE` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje tylko, czy kod jest 16-bitowy. Jeśli kod nie jest 16-bitowy, może to być coś innego, takiego jak 32-bitowy lub 64-bitowy kod.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
