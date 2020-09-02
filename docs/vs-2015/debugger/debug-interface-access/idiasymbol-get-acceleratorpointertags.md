---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149843"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca wszystkie wartości tagów wskaźnika akceleratora, które odpowiadają funkcji zastępczej akceleratora C++ AMP.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cnt`  
 podczas Rozmiar tablicy wyjściowej `pPointerTags` .  
  
 `pcnt`  
 określoną Liczba tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ AMP.  
  
 `pPointerTags`  
 określoną `DWORD` Wskaźnik tablicy, który jest wypełniony wartościami tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ amp.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w `IDiaSymbol` interfejsie, który odpowiada funkcji zastępczej akceleratora C++ amp.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
