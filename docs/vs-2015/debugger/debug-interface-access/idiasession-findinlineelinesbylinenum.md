---
title: IDiaSession::findInlineeLinesByLinenum | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3c147c0360ae87c2f41d299d5860cede59a93f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724827"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio w określone źródło pliku i numer wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)



