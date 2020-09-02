---
title: Debugowanie i proces hostingu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157896"
---
# <a name="debugging-and-the-hosting-process"></a>Debugowanie i proces hostingu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces hostingu programu Visual Studio poprawia wydajność debugera i udostępnia nowe funkcje debugera, takie jak debugowanie częściowej relacji zaufania i obliczanie wyrażeń czasu projektowania. Proces hostingu można wyłączyć, jeśli jest to konieczne. Aby uzyskać więcej informacji, zobacz [jak: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md). W poniższych sekcjach opisano pewne różnice między debugowaniem i bez procesu hostingu.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Debugowanie częściowej relacji zaufania i zabezpieczenia dwukrotnego kliknięcia  
 Debugowanie częściowej relacji zaufania wymaga procesu hostingu. Jeśli wyłączysz proces hostingu, Debugowanie częściowego zaufania nie będzie działało nawet wtedy, gdy zabezpieczenia na poziomie zaufania są włączone **Security** na stronie zabezpieczenia **właściwości projektu**. Aby uzyskać więcej informacji, zobacz [jak: wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md) i [instrukcje: debugowanie częściowej aplikacji zaufania](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażeń czasu projektowania  
 Wyrażenie czasu projektowania zawsze używa procesu hostingu. Wyłączenie procesu hostingu we **właściwościach projektu** wyłącza obliczanie wyrażeń w czasie projektowania dla projektów biblioteki klas. W przypadku innych typów projektów Obliczanie wyrażenia czasu projektowania nie jest wyłączone. Zamiast tego program Visual Studio uruchamia rzeczywisty plik wykonywalny i używa go do oceny czasu projektowania bez procesu hostingu. Różnica ta może dawać różne wyniki.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Różnice między elementami AppDomain. CurrentDomain —. FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `AppDomain.CurrentDomain.FriendlyName` z włączonym procesem hostingu zwraca *APP_NAME* `.vhost.exe` . Jeśli wywołajesz go jako wyłączony proces hostingu, zwraca *APP_NAME* `.exe` .  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). Różnice FullName  
 `Assembly.GetCallingAssembly().FullName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `Assembly.GetCallingAssembly().FullName` z włączonym procesem hostingu funkcja zwraca wartość `mscorlib` . Jeśli wywołasz `Assembly.GetCallingAssembly().FullName` proces hostingu wyłączony, zwraca nazwę aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Instrukcje: debugowanie częściowej aplikacji zaufania](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Instrukcje: Wyłączanie procesu hostingu](../ide/how-to-disable-the-hosting-process.md)
