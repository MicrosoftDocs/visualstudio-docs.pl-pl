---
title: 'IDiaSourceFile:: get_uniqueId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5237d8a524bd77f67c86a650bb4c8f075e407fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190628"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera prostą wartość klucza liczb całkowitych, która jest unikatowa dla tego obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca prostą wartość klucza liczb całkowitych, która jest unikatowa dla tego obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Porównanie kluczy zamiast ciągów może przyspieszyć przetwarzanie numerów wierszy.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
