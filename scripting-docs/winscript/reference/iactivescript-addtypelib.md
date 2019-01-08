---
title: IActiveScript::AddTypeLib | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 695edbd6f5356959785e54dc38f28b68c8c0400e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092550"
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