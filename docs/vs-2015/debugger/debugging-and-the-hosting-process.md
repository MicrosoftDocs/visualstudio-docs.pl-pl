---
title: Debugowanie i proces hostingu | Dokumentacja firmy Microsoft
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
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775288"
---
# <a name="debugging-and-the-hosting-process"></a>Debugowanie i proces hostingu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procesu hostingu Visual Studio zwiększa wydajność debugera i włącza nowe funkcje debugera, takich jak debugowanie częściowego zaufania i Obliczanie wyrażenia czasu projektowania. Jeśli chcesz, możesz wyłączyć procesu hostingu. Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md). W poniższych sekcjach opisano niektóre różnice między debugowania i bez procesu hostingu.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Częściowego zaufania, debugowania i kliknij przycisk — raz zabezpieczeń  
 Debugowanie częściowego zaufania wymaga procesu hostingu. Jeśli wyłączysz procesu hostingu, debugowanie częściowego zaufania nie będzie działać nawet, jeśli włączona jest funkcja zabezpieczeń częściowego zaufania **zabezpieczeń** strony **właściwości projektu**. Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md) i [jak: Debugowanie aplikacji częściowej relacji zaufania](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Zawsze wyrażenia czasu projektowania używa procesu hostingu. Wyłączanie hostingu przetworzyć w **właściwości projektu** wyłącza Obliczanie wyrażenia czasu projektowania dla projektów biblioteki klas. Obliczanie wyrażenia czasu projektowania dla innych typów projektów nie jest wyłączone. Zamiast tego program Visual Studio uruchamia rzeczywiste pliki wykonywalne i używa go na potrzeby oceny czasu projektowania bez procesu hostingu. Różnica ta może wygenerować różne wyniki.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Różnice AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` Zwraca różne wyniki, w zależności od tego, czy jest włączona procesu hostingu. Jeśli wywołasz `AppDomain.CurrentDomain.FriendlyName` przy użyciu procesu hostingu włączone, zwraca *nazwa_aplikacji*`.vhost.exe`. Jeśli wywołasz ją procesu hostingu wyłączone, funkcja zwraca *nazwa_aplikacji*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName Differences  
 `Assembly.GetCallingAssembly().FullName` Zwraca różne wyniki, w zależności od tego, czy jest włączona procesu hostingu. Jeśli wywołasz `Assembly.GetCallingAssembly().FullName` przy użyciu procesu hostingu włączone, zwraca `mscorlib`. Jeśli wywołasz `Assembly.GetCallingAssembly().FullName` przy użyciu procesu hostingu wyłączone, funkcja zwraca nazwę aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Instrukcje: Debugowanie aplikacji częściowej relacji zaufania](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Instrukcje: Wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)
