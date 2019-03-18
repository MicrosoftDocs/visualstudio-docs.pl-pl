---
title: Wyliczenie SOURCE_TEXT_ATTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05faeddf43c91ce0f45d54d2f6b6ed46cf8d2a4f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157990"
---
# <a name="sourcetextattr-enumeration"></a>Wyliczenie SOURCE_TEXT_ATTR
Opisuje atrybuty pojedynczego znaku w tekście źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Znak jest częścią słowa kluczowego języka, na przykład, słowo kluczowe VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Znak jest częścią blok komentarza.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Znak nie jest częścią tekst źródłowy języka skompilowany. Na przykład HTML otaczający blok skryptu.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Znak jest częścią operator języka. Na przykład:, operatora arytmetycznego **+**.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Znak jest częścią stałej liczbowej języka.  Na przykład stała 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Znak jest częścią stałą typu string języka. Na przykład ciąg "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Znak wskazuje początek bloku funkcji|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, i `IActiveScriptDebug::GetScriptTextAttributes` metody zwracają jeden atrybut tekstu na znak, chyba że:  
  
-   Jest ustawiona flaga GETATTRTYPE_DEPSCAN, w którym to przypadku metoda może zwrócić SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP flagi  
  
-   Jest ustawiona flaga GETATTRFLAG_THIS, w którym to przypadku metoda może zwrócić flagę SOURCETEXT_ATTR_THIS  
  
-   Flaga GETATTRFLAG_HUMANTEXT jest ustawiona, w którym to przypadku metoda może zwrócić flagi SOURCETEXT_ATTR_HUMANTEXT bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)