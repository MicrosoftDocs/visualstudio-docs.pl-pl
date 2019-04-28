---
title: IDiaSymbol::get_hasSecurityChecks | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e1096e137d3b8e634d404dd5e7158d37478d6fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410417"
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę określającą, czy compiland — lub funkcji został skompilowany przy użyciu sprawdzeń zabezpieczeń przepełnienia buforu (na przykład [/GS (Sprawdzanie zabezpieczeń bufora)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) przełącznika kompilatora).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Zwraca `TRUE` Jeśli funkcja ma żadnych kontroli zabezpieczeń; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (Sprawdzanie zabezpieczeń bufora)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e)
