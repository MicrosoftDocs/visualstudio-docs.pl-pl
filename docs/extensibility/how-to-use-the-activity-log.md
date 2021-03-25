---
title: 'Instrukcje: korzystanie z dziennika aktywności | Microsoft Docs'
description: Pakietów VSPackage może zapisywać komunikaty w dzienniku aktywności. Dowiedz się, jak używać dziennika aktywności do debugowania pakietów VSPackage w środowiskach detalicznych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02a8dd1497680239db9363a2e0682082f0c68d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057341"
---
# <a name="how-to-use-the-activity-log"></a>Instrukcje: korzystanie z dziennika aktywności
Pakietów VSPackage może zapisywać komunikaty w dzienniku aktywności. Ta funkcja jest szczególnie przydatna w przypadku debugowania pakietów VSPackage w środowiskach detalicznych.

> [!TIP]
> Dziennik aktywności jest zawsze włączony. Program Visual Studio utrzymuje stopniowe buforu ostatnich 100 wpisów, a także 10 pierwszych wpisów, które zawierają ogólne informacje o konfiguracji.

## <a name="to-write-an-entry-to-the-activity-log"></a>Aby napisać wpis do dziennika aktywności

1. Wstaw ten kod w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie lub w innej metodzie z wyjątkiem konstruktora pakietu VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Ten kod pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługę i rzutuje ją na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Zapisuje wpis informacyjny w dzienniku aktywności przy użyciu bieżącego kontekstu kulturowego.

2. Po załadowaniu pakietu VSPackage (zazwyczaj w przypadku wywołania polecenia lub otwarciu okna) tekst jest zapisywana w dzienniku aktywności.

## <a name="to-examine-the-activity-log"></a>Aby przejrzeć dziennik aktywności

1. Uruchom program Visual Studio z wierszem polecenia [/log](../ide/reference/log-devenv-exe.md) , aby zapisać ActivityLog.xml na dysku podczas sesji.

2. Po zamknięciu programu Visual Studio Znajdź dziennik aktywności w podfolderze dla danych programu Visual Studio:

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Otwórz dziennik aktywności przy użyciu dowolnego edytora tekstu. Oto typowy wpis:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Niezawodne programowanie

Ponieważ dziennik aktywności jest usługą, dziennik aktywności jest niedostępny w konstruktorze pakietu VSPackage.

Dziennik aktywności należy uzyskać tuż przed zapisaniem w nim. Nie Buforuj ani nie zapisuj dziennika aktywności do użytku w przyszłości.

## <a name="see-also"></a>Zobacz też

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Rozwiązywanie problemów z pakietami VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
