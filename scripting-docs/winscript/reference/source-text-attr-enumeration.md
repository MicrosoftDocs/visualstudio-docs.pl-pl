---
title: SOURCE_TEXT_ATTR, Wyliczenie | Microsoft Docs
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
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573004"
---
# <a name="source_text_attr-enumeration"></a>Wyliczenie SOURCE_TEXT_ATTR
Opisuje atrybuty pojedynczego znaku w tekście źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Znak jest częścią słowa kluczowego języka, na przykład słowo kluczowe VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Znak jest częścią bloku komentarza.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Znak nie jest częścią skompilowanego tekstu źródłowego języka. Na przykład kod HTML otaczający blok skryptu.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Znak jest częścią operatora języka. Na przykład:, operator arytmetyczny **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Znak jest częścią stałej numerycznej języka.  Na przykład stała 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Znak jest częścią stałej ciągu języka. Na przykład ciąg "Hello world".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Znak wskazuje początek bloku funkcji|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj metody `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` i `IActiveScriptDebug::GetScriptTextAttributes` zwracają jeden atrybut tekstowy na znak, chyba że:  
  
- Flaga GETATTRTYPE_DEPSCAN jest ustawiona, w tym przypadku metoda może zwrócić flagi SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
- Flaga GETATTRFLAG_THIS jest ustawiona, w tym przypadku metoda może zwrócić flagę SOURCETEXT_ATTR_THIS,  
  
- Flaga GETATTRFLAG_HUMANTEXT jest ustawiona, w tym przypadku metoda może zwrócić flagę SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)