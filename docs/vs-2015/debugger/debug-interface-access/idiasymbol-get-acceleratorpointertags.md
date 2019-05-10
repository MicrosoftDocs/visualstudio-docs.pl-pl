---
title: IDiaSymbol::get_acceleratorPointerTags | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763874"
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
