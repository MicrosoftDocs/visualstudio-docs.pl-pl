---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
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
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575810"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Dodaje bibliotekę typów do przestrzeni nazw dla skryptu. Jest to podobne do dyrektywy `#include` w języku C/C++. Umożliwia ona dodanie zestawu wstępnie zdefiniowanych elementów, takich jak definicje klas, `typedefs` i nazwane stałe, które mają zostać dodane do środowiska wykonawczego dostępnego dla skryptu.  
  
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
 podczas Identyfikator CLSID biblioteki typów do dodania.  
  
 `dwMaj`  
 podczas Główny numer wersji.  
  
 `dwMin`  
 podczas Pomocniczy numer wersji.  
  
 `dwFlags`  
 podczas Flagi opcji. Mogą być następujące:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Biblioteka typów zawiera opis kontrolki ActiveX używanej przez hosta.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować określonej biblioteki typów.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)