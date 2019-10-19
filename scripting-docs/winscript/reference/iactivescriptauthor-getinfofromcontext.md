---
title: 'IActiveScriptAuthor:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 457b2ad1bda3226caf3604e3ccd6b976f01bca83
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576212"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Zwraca informacje o typie i położenia zakotwiczenia dla danego znaku w bloku kodu. Zawiera informacje na temat elementów członkowskich IntelliSense, list globalnych i porad dotyczących parametrów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 podczas Adres ciągu bloku kodu używany do generowania wyników informacji.  
  
 `cchCode`  
 podczas Długość bloku kodu.  
  
 `ichCurrentPosition`  
 podczas Pozycja znaku względem początku bloku.  
  
 `dwListTypesRequested`  
 podczas Żądane typy list. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Brak listy.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Lista elementów członkowskich.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Lista tekstów stałych.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Lista parametrów metody wywołania.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Globalna lista.|  
  
 Typ SCRIPT_CMPL_GLOBALLIST jest traktowany jako domyślny element uzupełniający, który można łączyć za pomocą operatora OR z innymi elementami ukończenia. Aparat tworzenia skryptów najpierw próbuje wypełnić informacje o typie dla innych elementów listy uzupełniania. Jeśli to się nie powiedzie, aparat wypełnia dla SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 określoną Typ podanej listy.  
  
 `pichListAnchorPosition`  
 określoną Początkowy indeks kontekstu zawierającego bieżącą pozycję. Indeks początkowy jest względem początku bloku.  
  
 Jest to wypełniane tylko wtedy, gdy `dwListTypesRequested` zawiera SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST lub SCRIPT_CMPL_GLOBALLIST. W przypadku innych żądanych typów list wynik jest niezdefiniowany.  
  
 `pichFuncAnchorPosition`  
 określoną Początkowy indeks wywołania funkcji, który zawiera bieżącą pozycję. Indeks początkowy jest względem początku bloku.  
  
 Jest to wypełniane tylko wtedy, gdy kontekst zawierający bieżącą pozycję jest wywołaniem funkcji i gdy `dwListTypesRequested` zawiera SCRIPT_CMPL_PARAMLIST. W przeciwnym razie wynik jest niezdefiniowany.  
  
 `pmemid`  
 określoną Właściwość MEMBERID funkcji, zgodnie z definicją typu w parametrze `IProvideMultipleClassInfo``ppunk` out.  
  
 Jest to wypełniane tylko wtedy, gdy `dwListTypesRequested` zawiera SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 określoną Indeks parametru, który zawiera bieżącą pozycję. Jeśli bieżące położenie jest w nazwie funkcji, zwracana jest wartość-1.  
  
 Wartość `piCurrentParameter` jest wypełniana tylko wtedy, gdy `dwListTypesRequested` zawiera SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Informacje o typie, które są dostępne w formie obiektu `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IProvideMultipleClassInfo   interfejsu](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)