---
title: 'Jak: Korzystanie z dziennika aktywności | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710581"
---
# <a name="how-to-use-the-activity-log"></a>Jak: Korzystanie z dziennika aktywności
VSPackages można zapisywać wiadomości do dziennika aktywności. Ta funkcja jest szczególnie przydatna do debugowania vspackages w środowiskach sieci sprzedaży.

> [!TIP]
> Dziennik aktywności jest zawsze włączony. Visual Studio przechowuje bufor kroczący z ostatnich 100 wpisów, a także pierwszych 10 wpisów, które mają ogólne informacje o konfiguracji.

## <a name="to-write-an-entry-to-the-activity-log"></a>Aby napisać wpis w dzienniku działań

1. Wstaw ten <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> kod w metodzie lub w innej metodzie z wyjątkiem konstruktora VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Ten kod <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> pobiera usługę i rzuca <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> go do interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>zapisuje wpis informacyjny w dzienniku działań przy użyciu bieżącego kontekstu kulturowego.

2. Po załadowaniu vspackage (zwykle, gdy polecenie jest wywoływane lub okno jest otwierane), tekst jest zapisywany w dzienniku działań.

## <a name="to-examine-the-activity-log"></a>Aby sprawdzić dziennik aktywności

1. Uruchom program Visual Studio za pomocą przełącznika wiersza polecenia [/Log,](../ide/reference/log-devenv-exe.md) aby zapisać plik ActivityLog.xml na dysku podczas sesji.

2. Po zamknięciu programu Visual Studio znajdź dziennik aktywności w podfolderze danych programu Visual Studio:

   <em> *%AppData%</em>\Microsoft\VisualStudio\\\<wersja>\ActivityLog.xml*.

3. Otwórz dziennik aktywności za pomocą dowolnego edytora tekstu. Oto typowy wpis:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Solidne programowanie

Ponieważ dziennik aktywności jest usługą, dziennik aktywności jest niedostępny w konstruktorze VSPackage.

Dziennik aktywności należy uzyskać tuż przed zapisaniem do niego. Nie buforuj ani nie zapisuj dziennika aktywności do wykorzystania w przyszłości.

## <a name="see-also"></a>Zobacz też

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Rozwiązywanie problemów z pakietami VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
