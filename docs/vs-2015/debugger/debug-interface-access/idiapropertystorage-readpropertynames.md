---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537423"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera odpowiednie nazwy ciągów dla danego identyfikatora właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpropid`  
 podczas Liczba identyfikatorów właściwości w `rgpropid` .  
  
 `rgpropid`  
 podczas Tablica identyfikatorów właściwości, dla których mają zostać pobrane nazwy ( `PROPID` jest definiowana w WTypes. h jako `ULONG` ).  
  
 `rglpwstrName`  
 [in. out] Tablica nazw właściwości dla określonych identyfikatorów właściwości. Tablica musi być wstępnie przydzieloną, aby można było przechowywać żądaną liczbę nazw właściwości i musi być w stanie przechowywać co najmniej `cpropid``BSTR` ciągi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwracane nazwy właściwości muszą być zwolnione (przez wywołanie `SysFreeString` funkcji), gdy nie są już potrzebne.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
