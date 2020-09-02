---
title: 'IDiaSymbol:: get_baseType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df922cbbe1c065f4df79fa62b7b4b0213dd7f487
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807491"
---
# <a name="idiasymbolget_basetype"></a>IDiaSymbol::get_baseType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera typ podstawowy dla tego symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_baseType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca wartość z wyliczenia [basictype](../../debugger/debug-interface-access/basictype.md) , określając typ podstawowy symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Typ podstawowy dla symbolu można określić, najpierw pobierając typ symbolu, a następnie interrogating, który zwraca typ dla typu podstawowego. Należy zauważyć, że niektóre symbole nie mogą mieć typu podstawowego — na przykład nazwa struktury.  
  
## <a name="example"></a>Przykład  
  
```cpp#  
IDiaSymbol* pType;  
CComPtr<IDiaSymbol> pBaseType;  
if (pType->get_type( &pBaseType ) == S_OK)  
{  
    BasicType btBaseType;  
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)  
    {  
        // Do something with basic type.  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówki|dia2. h|  
|Wersja:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Basictype — Wyliczenie](../../debugger/debug-interface-access/basictype.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
