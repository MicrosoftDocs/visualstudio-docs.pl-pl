---
title: IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98425d12c53c61cb3f7557d1243cc757c326a89a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157558"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analizuje procedury danego kodu i dodaje procedurę do przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Adres tekst procedury do oceny. Interpretacja tego ciągu zależy od języka skryptów.  
  
 `pstrFormalParams`  
 [in] Adres nazwy parametrów formalnych w procedurze. Nazwy parametrów muszą być oddzielone ogranicznikami odpowiednie dla silnika wykonywania skryptów. Nazwy nie powinna zostać ujęta w nawiasy.  
  
 `pstrProcedureName`  
 [in] Adres nazwę procedury do przeanalizowania.  
  
 `pstrItemName`  
 [in] Adres nazwy elementu który podaje kontekst, w którym ma zostać obliczone procedury. Jeśli ten parametr jest `NULL`, kod jest oceniany w kontekście globalnym silnika wykonywania skryptów.  
  
 `punkContext`  
 [in] Adres obiektu kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być świadczona przez debuger do reprezentowania aktywnego kontekstu wykonywania. Jeśli ten parametr jest `NULL`, aparat używa parametru `pstrItemName` do zidentyfikowania kontekstu.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika końcowego wewnętrzny. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec procedury. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) silnik wykonywania skryptów korzysta z tych informacji zależy od silnika wykonywania skryptów. Ustaw ten parametr na `NULL` Jeśli host nie korzystał z ogranicznika do oznaczenia końca procedury.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanych przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Liczony od zera wartość, która określa, która linia będzie rozpoczynać analizę.  
  
 `dwFlags`  
 [in] Flagi skojarzone z tą procedurą. Może być kombinacją tych wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Oznacza to, że kod w `pstrCode` jest wyrażeniem, która reprezentuje wartość zwracaną przez procedurę. Domyślnie kod może zawierać wyrażenia, listę instrukcji lub czymkolwiek dozwolonym else w procedurze, za pomocą języka skryptów.|  
|SCRIPTPROC_IMPLICIT_THIS|Oznacza to, że `this` wskaźnik myszy znajduje się w zakresie procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Oznacza to, że nadrzędne `this` wskaźnika znajdują się w zakresie procedury.|  
  
 `ppdisp`  
 [out] Adres wskaźnika na obiekt zawierający właściwości i metody globalne skryptu. Jeśli silnik wykonywania skryptów nie obsługuje taki obiekt `NULL` jest zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania czasu wykonywania procedur do przestrzeni nazw.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił nieokreślony błąd składniowy w procedurze.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dispatch; `ppdisp` parametr ma wartość `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Brak kodu skryptu jest oceniany podczas tego wywołania; przeciwnie procedura jest kompilowana w stan skryptu, w którym może być wywołany przez skrypt później.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)