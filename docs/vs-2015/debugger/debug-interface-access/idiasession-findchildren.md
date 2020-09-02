---
title: 'IDiaSession:: findChildren — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150426"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera wszystkie elementy podrzędne określonego identyfikatora nadrzędnego, które pasują do nazwy i typu symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 podczas Obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący element nadrzędny. Jeśli ten symbol nadrzędny jest funkcją, modułem lub blokiem, wówczas jego leksykalne elementy podrzędne są zwracane w `ppResult` . Jeśli symbol nadrzędny jest typem, jego elementy podrzędne klasy są zwracane. Jeśli ten parametr ma wartość `NULL` , `symtag` musi być ustawiona na `SymTagExe` lub `SymTagNull` , która zwraca zakres globalny (plik. exe).  
  
 `symtag`  
 podczas Określa tag symbolu elementów podrzędnych, które mają zostać pobrane. Wartości są pobierane z wyliczenia [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) . Ustaw, aby `SymTagNull` pobrać wszystkie elementy podrzędne.  
  
 `name`  
 podczas Określa nazwę elementów podrzędnych do pobrania. Ustaw na `NULL` wszystkie elementy podrzędne do pobrania.  
  
 `compareFlags`  
 podczas Określa opcje porównania stosowane do dopasowywania nazw. Wartości z wyliczenia [namesearchoptions —](../../debugger/debug-interface-access/namesearchoptions.md) można użyć samodzielnie lub w połączeniu.  
  
 `ppResult`  
 określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę pobranych symboli podrzędnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak znaleźć zmienne lokalne funkcji `pFunc` , które pasują do nazwy `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podsumowanie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Namesearchoptions —, Wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
