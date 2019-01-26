---
title: IDiaSession::findInlineeLinesByLinenum | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 432c0859041740c74e6c3264c318d46352d262b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972696"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio w określone źródło pliku i numer wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compiland`  
 [in] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który reprezentuje compiland —, w których należy szukać numerów wierszy. Ten parametr nie może być `NULL`.  
  
 `file`  
 [in] [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekt, który reprezentuje plik źródłowy, w którym do wyszukiwania. Ten parametr nie może być `NULL`.  
  
 `linenum`  
 [in] Określa numer liczonego od jednego wiersza.  
  
> [!NOTE]
>  Nie można użyć zero, aby określić wszystkie wiersze (Użyj [idiasession::findlines —](../../debugger/debug-interface-access/idiasession-findlines.md) metody do znalezienia wszystkich wierszy).  
  
 `column`  
 [in] Określa liczbę kolumn. Użyj wartości zero, aby określić wszystkie kolumny. Kolumna jest bajt przesunięcie wiersza.  
  
 `ppResult`  
 [out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiektu, który zawiera listę numerów wierszy, które zostały pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)