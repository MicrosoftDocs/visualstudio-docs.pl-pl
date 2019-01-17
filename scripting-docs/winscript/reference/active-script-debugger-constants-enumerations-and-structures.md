---
title: Stałe debugera aktywnego skryptu, wyliczenia i struktury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913c1b243bcc9c7a6653025fbfcb4f941df2950e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345438"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury debugera aktywnego skryptu
Interfejsy funkcji aktywnego debugowania używają następujących stałych, wyliczeń i struktur.  
  
## <a name="constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury  
  
|Stałe|Opis|  
|---------------|-----------------|  
|[Stałe APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Wskazuje bieżący stan debugowania aplikacji i wątków.|  
|[DEBUG_TEXT, stałe](../../winscript/reference/debug-text-constants.md)|Flagi opcji używane podczas [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[TEXT_DOC_ATTR, stałe](../../winscript/reference/text-doc-attr-constants.md)|Opisuje atrybuty dokumentu.|  
  
|Wyliczenia|Opis|  
|------------------|-----------------|  
|[Stałe APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Wskazuje bieżący stan debugowania aplikacji i wątków.|  
|[APPLICATION_NODE_EVENT_FILTER, wyliczenie](../../winscript/reference/application-node-event-filter-enumeration.md)|Wskazuje węzły, które mają być wykluczone za pomocą filtra.|  
|[BREAKPOINT_STATE, wyliczenie](../../winscript/reference/breakpoint-state-enumeration.md)|Wskazuje stan punktu przerwania.|  
|[BREAKREASON, wyliczenie](../../winscript/reference/breakreason-enumeration.md)|Wskazuje powód przerwania.|  
|[BREAKRESUMEACTION, wyliczenie](../../winscript/reference/breakresumeaction-enumeration.md)|Opisuje sposób kontynuowania pracy po punkcie przerwania.|  
|[DOCUMENTNAMETYPE, wyliczenie](../../winscript/reference/documentnametype-enumeration.md)|Wskazuje, który typ ma zostać pobrany dla dokumentu.|  
|[ERRORRESUMEACTION, wyliczenie](../../winscript/reference/errorresumeaction-enumeration.md)|Opisuje sposób kontynuowania pracy po błędzie czasu wykonywania.|  
|[JS_PROPERTY_ATTRIBUTES, wyliczenie](../../winscript/reference/js-property-attributes-enumeration.md)|Określa atrybuty właściwości.|  
|[JS_PROPERTY_MEMBERS, wyliczenie](../../winscript/reference/js-property-members-enumeration.md)|Flagi określające typ informacji, które będą zwracane w żądaniu o dane elementów członkowskich obiektu.|  
|[JsDebugReadMemoryFlags, wyliczenie](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Flagi określające zachowanie podczas odczytu pamięci.|  
|[SCRIPT_DEBUGGER_OPTIONS, wyliczenie](../../winscript/reference/script-debugger-options-enumeration.md)|Wskazuje zestaw opcji lub funkcji dołączonego debugera.|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND, wyliczenie](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Wskazuje rodzaj zgłaszanego wyjątku.|  
|[Stałe SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)|Opisuje atrybuty pojedynczego znaku w tekście źródłowym.|  
  
|Struktury|Opis|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor, struktura](../../winscript/reference/debugstackframedescriptor-structure.md)|Wylicza ramki stosu i scala dane wyjściowe z kilku modułów wyliczających w tym samym wątku.|  
|[JS_NATIVE_FRAME, struktura](../../winscript/reference/js-native-frame-structure.md)|Reprezentuje ramkę stosu.|  
|[JsDebugPropertyInfo, struktura](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Zawiera informacje o właściwości.|  
|[TEXT_DOCUMENT_ARRAY, struktura](../../winscript/reference/text-document-array-structure.md)|Zawiera zestaw dokumentów.|