---
title: Omówienie profilowania aktywnego skryptu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5313bad4b1145216d6e04607242ed1ca131694
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835722"
---
# <a name="active-script-profiling-overview"></a>Przegląd profilowania aktywnego skryptu
[Interfejsy profilera aktywnego skryptu](../winscript/reference/active-script-profiler-interfaces.md) umożliwiają profilowanie aparatu skryptów. Profilowanie aktywnego skryptu obejmuje następujące części:  
  
- Aparat języka  
  
- Host  
  
- Profiler  
  
## <a name="language-engine"></a>Aparat języka  
 Aparat języka wykonuje skrypt. Dostarcza metody, które umożliwiają profilowanie kodu skryptu w miarę jego wykonywania. Gdy profilowanie jest włączone, Aparat języka Pobiera identyfikator klasy (CLSID) obiektu COM profilera jako argument. Tworzy wystąpienie obiektu COM profilera, a następnie wywołuje do profilera w przypadku wystąpienia różnych zdarzeń.  
  
 Aparat języka implementuje [interfejs IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]Środowisko uruchomieniowe języka sprawdza zmienną środowiskową JS_PROFILER przy tworzeniu, aby określić, czy profilowanie powinno być włączone. Jeśli ta zmienna jest ustawiona na identyfikator CLSID profilera, środowisko uruchomieniowe języka tworzy wystąpienie obiektu COM profilera przy użyciu wartości zmiennej, aby określić, który Profiler ma zostać utworzony.  
  
## <a name="host"></a>Host  
 Host tworzy aparat językowy i udostępnia Aparat języka ze skryptami do wykonania. Host inteligentny udostępnia również kontekst dokumentu, który może być używany przez debuger lub profiler w celu zapewnienia lepszych informacji podczas debugowania lub profilowania.  
  
## <a name="profiler"></a>Profiler  
 Profiler odbiera wywołania z aparatu języka w przypadku wystąpienia różnych zdarzeń. Profiler musi być zarejestrowany jako obiekt COM i musi implementować [interfejs IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../winscript/reference/active-script-profiler-interfaces.md)