---
title: 'Porady: debugowanie wyjątków ASP.NET | Dokumentacja firmy Microsoft'
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d505e67018c24f659e88401b565011a4c7bea96
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789216"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Porady: debugowanie wyjątków ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie wyjątków jest ważną częścią opracowywania niezawodnej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji. Ogólne informacje o tym, jak można debugować wyjątki wynosi [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Aby debugować nieobsłużone [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wyjątki, musisz upewnić się, że debuger zatrzymuje działanie dla nich. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Środowisko uruchomieniowe ma program obsługi wyjątków najwyższego poziomu. W związku z tym debuger nigdy nie przerywa wykonywania kodu na nieobsłużonych wyjątków domyślnie. Aby przerwać w debugerze, gdy wyjątek jest zgłaszany, należy wybrać **Przerwij, gdy wyjątek jest: zgłoszono** ustawienie dla określonego wyjątku w **wyjątki** okno dialogowe.  
  
 Jeśli włączono opcję tylko mój kod **Przerwij, gdy wyjątek jest: zgłoszono** nie powoduje, że debuger natychmiast przerywa, jeśli wyjątek jest zgłaszany w metodzie środowiska .NET Framework lub innym kodzie systemowym. Zamiast tego kontynuuje wykonywanie dopóki debuger uderza w kodu-system, a następnie przerywa. W rezultacie, nie masz przechodzić przez kodu systemu po wystąpieniu wyjątku.  
  
 Tylko mój kod daje inne rozwiązanie, które mogą być bardziej przydatne: **Przerwij, gdy wyjątek jest: User-unhandled**. Jeśli wybierzesz to ustawienie, dla wyjątku, debuger spowoduje przerwanie wykonywania w kodzie użytkownika, ale tylko wtedy, gdy wyjątek nie jest wychwycony i obsłużony przez kod użytkownika. To ustawienie neguje efekt najwyższego poziomu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aparatu obsługi wyjątków, ponieważ ten program obsługi jest kod niezwiązany z użytkownikiem.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Aby włączyć debugowanie wyjątków ASP.NET za pomocą tylko mój kod  
  
1.  Na **debugowania** menu, kliknij przycisk **wyjątki**.  
  
     **Wyjątki** pojawi się okno dialogowe.  
  
2.  Na **wyjątki środowiska uruchomieniowego języka wspólnego** wiersz, wybierz opcję **zgłoszenia** lub **User-unhandled**.  
  
     Aby użyć **User-unhandled** ustawienie **tylko mój kod** musi być włączona...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Aby stosować najlepsze rozwiązania dla obsługi wyjątków programu ASP.NET  
  
-   Miejsce `try … catch` bloki wokół kodu, który może generować wyjątki, które można przewidzieć i wiedzieć jak je obsługiwać. Na przykład, jeśli aplikacja wykonuje wywołania do usługi sieci Web XML lub bezpośrednio do programu SQL Server, ten kod powinien być w **try... catch** blokuje, ponieważ istnieją liczne wyjątki, które mogą wystąpić.



