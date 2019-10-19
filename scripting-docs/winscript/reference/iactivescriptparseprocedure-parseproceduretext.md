---
title: IActiveScriptParseProcedure::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 53ed29c3e283af0f923590851cf9bf0655f7ac08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561538"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analizuje daną procedurę kodu i dodaje procedurę do przestrzeni nazw.  
  
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
 podczas Adres tekstu procedury do obliczenia. Interpretacja tego ciągu zależy od języka skryptowego.  
  
 `pstrFormalParams`  
 podczas Adres formalnych nazw parametrów dla procedury. Nazwy parametrów muszą być oddzielone odpowiednimi ogranicznikami aparatu obsługi skryptów. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pstrProcedureName`  
 podczas Adres nazwy procedury do przeanalizowania.  
  
 `pstrItemName`  
 podczas Adres nazwy elementu, który zawiera kontekst, w którym ma zostać obliczona procedura. Jeśli ten parametr jest `NULL`, kod jest oceniany w kontekście globalnym aparatu skryptów.  
  
 `punkContext`  
 podczas Adres obiektu kontekstu. Ten obiekt jest zarezerwowany do użytku w środowisku debugowania, gdzie taki kontekst może być dostarczony przez debuger do reprezentowania aktywnego kontekstu czasu wykonywania. Jeśli ten parametr jest `NULL`, aparat używa `pstrItemName` do identyfikowania kontekstu.  
  
 `pstrDelimiter`  
 podczas Adres ogranicznika końca procedury. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), w celu wykrycia końca procedury. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr, aby `NULL`, Jeśli host nie używał ogranicznika do oznaczenia końca procedury.  
  
 `dwSourceContextCookie`  
 podczas Wartość zdefiniowana przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 podczas Wartość zerowa, która określa, w którym wierszu rozpocznie się analizowanie.  
  
 `dwFlags`  
 podczas Flagi skojarzone z procedurą. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Wskazuje, że kod w `pstrCode` jest wyrażeniem, które reprezentuje wartość zwracaną przez procedurę. Domyślnie kod może zawierać wyrażenie, listę instrukcji lub inne elementy dozwolone w procedurze przez język skryptu.|  
|SCRIPTPROC_IMPLICIT_THIS|Wskazuje, że w zakresie procedury znajduje się wskaźnik `this`.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Wskazuje, że elementy nadrzędne wskaźnika `this` są zawarte w zakresie procedury.|  
  
 `ppdisp`  
 określoną Adres wskaźnika dla obiektu zawierającego globalne metody i właściwości skryptu. Jeśli aparat skryptów nie obsługuje takiego obiektu, `NULL` jest zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania procedur do przestrzeni nazw w czasie wykonywania.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów jest w stanie niezainicjowanym lub zamkniętym).|  
|`OLESCRIPT_E_SYNTAX`|W procedurze Wystąpił nieokreślony błąd składniowy.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu wysyłania; parametr `ppdisp` jest ustawiony na `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Kod skryptu nie jest oceniany podczas tego wywołania; Zamiast tego procedura jest kompilowana w stanie skryptu, w którym może być wywoływana przez skrypt później.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)