---
title: 'Instrukcje: debugowanie wyjątków ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205426"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Porady: debugowanie wyjątków ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie wyjątków jest ważną częścią opracowywania niezawodnej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji. Ogólne informacje o sposobie debugowania wyjątków polegają na [zarządzaniu wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Aby debugować nieobsłużone [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wyjątki, należy się upewnić, że debuger go zatrzyma. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Środowisko uruchomieniowe ma program obsługi wyjątków najwyższego poziomu. W związku z tym debuger nigdy nie jest podzielony na Nieobsłużone wyjątki domyślnie. Aby przerwać debuger w przypadku zgłoszenia wyjątku, należy wybrać opcję **Przerwij, gdy wyjątek to: zgłoszone** ustawienie dla tego konkretnego wyjątku w oknie dialogowym **wyjątki** .  
  
 Jeśli włączono Tylko mój kod, Przerwij, **gdy wyjątek to: zgłoszone** nie powoduje natychmiastowego przerwania debugera, jeśli wyjątek jest zgłaszany w metodzie .NET Framework lub w innym kodzie systemowym. Zamiast tego wykonywanie jest kontynuowane do momentu, aż debuger trafi w kodzie niesystemowym, spowoduje przerwanie działania. W związku z tym nie trzeba wykonywać kroków kodu systemowego, gdy wystąpi wyjątek.  
  
 Tylko mój kod daje kolejną opcję, która może być jeszcze bardziej przydatna: **Przerwij, gdy wyjątek jest: nieobsługiwany przez użytkownika**. W przypadku wybrania tego ustawienia dla wyjątku debuger przerwie wykonywanie w kodzie użytkownika, ale tylko wtedy, gdy wyjątek nie zostanie przechwycony i obsłużony przez kod użytkownika. To ustawienie powoduje negację efektu programu obsługi wyjątków najwyższego poziomu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , ponieważ program obsługi znajduje się w kodzie niebędącym użytkownikiem.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Aby włączyć debugowanie wyjątków ASP.NET z Tylko mój kod  
  
1. W menu **debugowanie** kliknij pozycję **wyjątki**.  
  
     Zostanie wyświetlone okno dialogowe **wyjątki** .  
  
2. W wierszu **wyjątki środowiska uruchomieniowego języka wspólnego** wybierz opcję **zgłoszone** lub **nieobsługiwane przez użytkownika**.  
  
     Aby można było użyć ustawienia **nieobsługiwanego przez użytkownika** , należy włączyć **tylko mój kod** ..  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Aby użyć najlepszych rozwiązań dla obsługi wyjątków ASP.NET  
  
- Umieść `try … catch` bloki wokół kodu, który może generować wyjątki, które można przewidywanie i wiedzieć, jak obsłużyć. Na przykład jeśli aplikacja przeprowadza wywołania do usługi sieci Web XML lub bezpośrednio do SQL Server, ten kod powinien znajdować się w **try... bloki catch** , ponieważ mogą wystąpić liczne wyjątki.
