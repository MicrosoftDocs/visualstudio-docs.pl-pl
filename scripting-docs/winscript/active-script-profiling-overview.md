---
title: Omówienie profilowania skryptów aktywnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 777d20ecb51b09b282f88dc08464727b9ff2a945
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432976"
---
# <a name="active-script-profiling-overview"></a>Przegląd profilowania aktywnego skryptu
[Aktywne interfejsy Profiler skryptu](../winscript/reference/active-script-profiler-interfaces.md) Włącz profilowanie aparatu obsługi skryptów. Profilowanie aktywnego skryptu składa się z następujących elementów:  
  
- Aparat języka  
  
- Host  
  
- Profiler  
  
## <a name="language-engine"></a>Aparat języka  
 Aparat języka wykonuje skrypt. Zapewnia metody, które umożliwiają profilowanie kodu skryptu, ponieważ jest ono wykonywane. Po włączeniu profilowania aparat języka przyjmuje identyfikator klasy (CLSID) programu profilującego obiektu COM jako argument. Tworzy wystąpienie obiektu COM profiler i następnie wywołuje do profilera po wystąpieniu różnych zdarzeń.  
  
 Implementuje aparat języka [interfejs IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Aparatu plików wykonywalnych języka sprawdza, czy zmienna środowiskowa JS_PROFILER przy tworzeniu, aby ustalić, czy należy włączyć profilowanie. Jeśli ustawiono tę zmienną do identyfikatora CLSID programu profiler, środowisko uruchomieniowe języka tworzy wystąpienie obiektu COM profiler, za pomocą wartość zmiennej, aby określić, które program profilujący do utworzenia.  
  
## <a name="host"></a>Host  
 Host tworzy aparat języka i zapewnia aparat języka skryptów do wykonania. Jest host inteligentny także kontekstu dokumentu, używany przez debugera i profilera w celu zapewnienia lepszej informacji podczas debugowania i profilowania.  
  
## <a name="profiler"></a>Profiler  
 Profiler otrzymuje wywołania z aparatu języka, po wystąpieniu różnych zdarzeń. Program profilujący musi zostać zarejestrowana jako obiekt COM, którą należy wdrożyć [interfejs IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../winscript/reference/active-script-profiler-interfaces.md)