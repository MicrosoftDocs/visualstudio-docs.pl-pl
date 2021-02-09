---
title: Debugowanie i proces hostingu | Microsoft Docs
description: W przypadku wersji programu Visual Studio wcześniejszych niż 2017 Użyj procesu hostingu, aby zwiększyć wydajność debugera i uzyskać dostęp do niektórych funkcji debugera.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 750b210ce04850e0cb6370094cdcc835f577b587
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872875"
---
# <a name="debugging-and-the-hosting-process"></a>Debugowanie i proces hostingu
Proces hostingu programu Visual Studio poprawia wydajność debugera i udostępnia nowe funkcje debugera, takie jak debugowanie częściowej relacji zaufania i obliczanie wyrażeń czasu projektowania. Proces hostingu można wyłączyć, jeśli jest to konieczne. W poniższych sekcjach opisano pewne różnice między debugowaniem i bez procesu hostingu.

> [!NOTE]
> Począwszy od programu Visual Studio 2017, opcja debugowania przy użyciu procesu hostingu nie jest już wymagana i została usunięta. Aby uzyskać więcej informacji, zobacz [debugowanie: program Visual Studio 2017 ma na celu przyspieszenie najmniejszego ulubionego zadania](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Partial-Trust debugowanie i zabezpieczenia Click-Once
 Debugowanie częściowej relacji zaufania wymaga procesu hostingu. Jeśli wyłączysz proces hostingu, Debugowanie częściowego zaufania nie będzie działało nawet wtedy, gdy zabezpieczenia na poziomie zaufania są włączone  na stronie zabezpieczenia **właściwości projektu**. Aby uzyskać więcej informacji, zobacz [How to: Debug a Intrusting Application](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia Design-Time
 Wyrażenie czasu projektowania zawsze używa procesu hostingu. Wyłączenie procesu hostingu we **właściwościach projektu** wyłącza obliczanie wyrażeń w czasie projektowania dla projektów biblioteki klas. W przypadku innych typów projektów Obliczanie wyrażenia czasu projektowania nie jest wyłączone. Zamiast tego program Visual Studio uruchamia rzeczywisty plik wykonywalny i używa go do oceny czasu projektowania bez procesu hostingu. Różnica ta może dawać różne wyniki.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Różnice między elementami AppDomain. CurrentDomain —. FriendlyName
 `AppDomain.CurrentDomain.FriendlyName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `AppDomain.CurrentDomain.FriendlyName` z włączonym procesem hostingu zwraca *APP_NAME* `.vhost.exe` . Jeśli wywołajesz go jako wyłączony proces hostingu, zwraca *APP_NAME* `.exe` .

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). Różnice FullName
 `Assembly.GetCallingAssembly().FullName` zwraca różne wyniki w zależności od tego, czy proces hostingu jest włączony. W przypadku wywołania `Assembly.GetCallingAssembly().FullName` z włączonym procesem hostingu funkcja zwraca wartość `mscorlib` . Jeśli wywołasz `Assembly.GetCallingAssembly().FullName` proces hostingu wyłączony, zwraca nazwę aplikacji.

## <a name="see-also"></a>Zobacz też

- [Porady: debugowanie częściowo zaufanych aplikacji](debugger-security.md)