---
title: IDiaPropertyStorage::Enum | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0244aca54ffe7b68ea4cfd82be465c28524758ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973489"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Pobiera moduł wyliczający dla właściwości, w tym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
 [out] Zwraca `IEnumSTATPROPSTG` obiektu (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) reprezentujący wyliczenie właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)