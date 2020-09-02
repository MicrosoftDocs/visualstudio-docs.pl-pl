---
title: 'IDiaSymbol:: get_type | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9bec7cdbf0641bbd1bba1e70c2f21ec232a18e6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787548"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera symbol reprezentujący typ dla tego symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_type (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje typ tego symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ symbolu, należy wywołać tę metodę i sprawdzić otrzymany obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Należy zauważyć, że istnieje możliwość, że symbol nie ma typu. Na przykład, nazwa struktury nie ma typu, ale może mieć symbole podrzędne (Użyj metody [IDiaSymbol:: findChildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md) , aby przejrzeć te elementy podrzędne).  
  
## <a name="example"></a>Przykład  
  
```cpp#  
IDiaSymbol*         pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (SUCCEEDED(pType->get_type( &pBaseType ))) {  
    BasicType btBaseType;  
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
