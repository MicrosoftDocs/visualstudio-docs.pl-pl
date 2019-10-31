---
title: Debugowanie i proces hostingu | Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188470"
---
# <a name="debugging-and-the-hosting-process"></a>Debugowanie i proces hostingu
Proces hostingu programu Visual Studio poprawia wydajność debugera i udostępnia nowe funkcje debugera, takie jak debugowanie częściowej relacji zaufania i obliczanie wyrażeń czasu projektowania. Proces hostingu można wyłączyć, jeśli jest to konieczne. W poniższych sekcjach opisano pewne różnice między debugowaniem i bez procesu hostingu.

> [!NOTE]
> Począwszy od programu Visual Studio 2017, opcja debugowania przy użyciu procesu hostingu nie jest już wymagana i została usunięta. Aby uzyskać więcej informacji, zobacz [debugowanie: program Visual Studio 2017 ma na celu przyspieszenie najmniejszego ulubionego zadania](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Debugowanie częściowej relacji zaufania i zabezpieczenia dwukrotnego kliknięcia
 Debugowanie częściowej relacji zaufania wymaga procesu hostingu. Jeśli wyłączysz proces hostingu, Debugowanie częściowego zaufania nie będzie działało nawet wtedy, gdy zabezpieczenia na poziomie zaufania są włączone na stronie zabezpieczenia **właściwości projektu**. Aby uzyskać więcej informacji, zobacz [How to: Debug a Intrusting Application](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażeń czasu projektowania
 Wyrażenie czasu projektowania zawsze używa procesu hostingu. Wyłączenie procesu hostingu we **właściwościach projektu** wyłącza obliczanie wyrażeń w czasie projektowania dla projektów biblioteki klas. W przypadku innych typów projektów Obliczanie wyrażenia czasu projektowania nie jest wyłączone. Zamiast tego program Visual Studio uruchamia rzeczywisty plik wykonywalny i używa go do oceny czasu projektowania bez procesu hostingu. Różnica ta może dawać różne wyniki.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Różnice między elementami AppDomain. CurrentDomain —. FriendlyName
 `AppDomain.CurrentDomain.FriendlyName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `AppDomain.CurrentDomain.FriendlyName` z włączonym procesem hostingu funkcja zwróci`.vhost.exe`*APP_NAME* . Jeśli wywołajesz IT proces hostingu jest wyłączony, zwraca *app_name*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). Różnice FullName
 `Assembly.GetCallingAssembly().FullName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `Assembly.GetCallingAssembly().FullName` z włączonym procesem hostingu zwraca `mscorlib`. Jeśli wywołasz `Assembly.GetCallingAssembly().FullName` z wyłączonym procesem hostingu, zwraca nazwę aplikacji.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: debugowanie częściowo zaufanych aplikacji](debugger-security.md)