---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955094"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Dodaje bibliotekę typów przestrzeń nazw dla skryptu. Jest to podobne do `#include` dyrektywy języka C/C++. Umożliwia zestaw wstępnie zdefiniowanych elementów, takich jak definicje klas `typedefs`i o nazwie stałych, które mają zostać dodane do środowiska wykonawczego dla skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidTypeLib`  
 [in] Identyfikator CLSID biblioteki typów do dodania.  
  
 `dwMaj`  
 [in] Główny numer wersji.  
  
 `dwMin`  
 [in] Pomocniczy numer wersji.  
  
 `dwFlags`  
 [in] Flagi opcji. Mogą być następujące:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Biblioteka typów zawiera opis kontrolki ActiveX, który jest używany przez hosta.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować określonej biblioteki typu.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)