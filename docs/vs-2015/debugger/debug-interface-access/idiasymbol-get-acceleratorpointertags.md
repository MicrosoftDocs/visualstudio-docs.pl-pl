---
title: IDiaSymbol::get_acceleratorPointerTags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efad3aeaf0d8a30d521d16612639d0b663ee8ebe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720671"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca wszystkie akceleratora wskaźnik wartości tagów, które odpowiadają do funkcji klasy zastępczej akceleratora C++ AMP.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cnt`  
 [in] Rozmiar tablicy danych wyjściowych `pPointerTags`.  
  
 `pcnt`  
 [out] Liczba tagów wskaźnika akceleratora w funkcji klasy zastępczej akceleratora C++ AMP.  
  
 `pPointerTags`  
 [out] A `DWORD` wskaźnika tablicy, który zostanie wypełniony kolorem wartości tagów wskaźnika akceleratora w funkcji klasy zastępczej akceleratora C++ AMP.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora C++ AMP.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



