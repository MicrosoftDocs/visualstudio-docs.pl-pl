---
title: Uruchamianie programu Visual Studio przy użyciu DTE
description: Dowiedz się, jak uruchamiać Visual Studio dte w celu obsługi instalacji side-by-side wydań głównych. Ten artykuł zawiera przykładowy kod.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/26/2019
ms.topic: how-to
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253c7f106f1d139f694fea3d469385f200c84029
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903115"
---
# <a name="launch-visual-studio-using-dte"></a>Uruchamianie programu Visual Studio przy użyciu DTE

Począwszy od Visual Studio 2017 r., mechanizm uruchamiania Visual Studio dte różni się od uruchamiania poprzednich wersji Visual Studio. Ta zmiana jest konieczna, ponieważ program Visual Studio 2017 i nowsze wersje obsługują instalacje obok siebie wydań głównych (na przykład obok siebie można zainstalować wersję zapoznawczą i wersję wydania).

W pozostałej części tego artykułu przedstawiono kod, który umożliwia uruchomienie programu Visual Studio 2019 r. przy użyciu dte.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

Aby zobaczyć, jak kod uruchamia się w akcji, utwórz projekt, korzystając z poniższych kroków.

1. Utwórz nowy projekt **aplikacji konsolowej** dla .NET Framework.

2. Zainstaluj [Microsoft.VisualStudio.Setup.Configadres URL. Przeplataj](https://www.nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop/) pakiet NuGet i dodaj odwołanie do zestawu.

3. Dodaj odwołanie do envDTE.

4. Wklej [przykładowy kod](#example-code) do pliku *Program.cs.*

5. Naciśnij **klawisz F5,** aby uruchomić program. Przed zamknięciem Visual Studio 2019 r. powinna zostać otwarta.

## <a name="example-code"></a>Przykładowy kod

```csharp
using Microsoft.VisualStudio.Setup.Configuration;
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices;
using System.Runtime.InteropServices.ComTypes;
using System.Threading;

namespace ConsoleLauncherApp
{
    class Program
    {
        static void Main(string[] args)
        {
            EnvDTE.DTE dte = LaunchVsDte(isPreRelease: false);

            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMaximize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMinimize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateNormal;
            dte.Quit();
        }

        private static EnvDTE.DTE LaunchVsDte(bool isPreRelease)
        {
            ISetupInstance setupInstance = GetSetupInstance(isPreRelease);
            string installationPath = setupInstance.GetInstallationPath();
            string executablePath = Path.Combine(installationPath, @"Common7\IDE\devenv.exe");
            Process vsProcess = Process.Start(executablePath);
            string runningObjectDisplayName = $"VisualStudio.DTE.16.0:{vsProcess.Id}";

            IEnumerable<string> runningObjectDisplayNames = null;
            object runningObject;
            for (int i = 0; i < 60; i++)
            {
                try
                {
                    runningObject = GetRunningObject(runningObjectDisplayName, out runningObjectDisplayNames);
                }
                catch
                {
                    runningObject = null;
                }

                if (runningObject != null)
                {
                    return (EnvDTE.DTE)runningObject;
                }

                Thread.Sleep(millisecondsTimeout: 1000);
            }

            throw new TimeoutException($"Failed to retrieve DTE object. Current running objects: {string.Join(";", runningObjectDisplayNames)}");
        }

        private static object GetRunningObject(string displayName, out IEnumerable<string> runningObjectDisplayNames)
        {
            IBindCtx bindContext = null;
            NativeMethods.CreateBindCtx(0, out bindContext);

            IRunningObjectTable runningObjectTable = null;
            bindContext.GetRunningObjectTable(out runningObjectTable);

            IEnumMoniker monikerEnumerator = null;
            runningObjectTable.EnumRunning(out monikerEnumerator);

            object runningObject = null;
            List<string> runningObjectDisplayNameList = new List<string>();
            IMoniker[] monikers = new IMoniker[1];
            IntPtr numberFetched = IntPtr.Zero;
            while (monikerEnumerator.Next(1, monikers, numberFetched) == 0)
            {
                IMoniker moniker = monikers[0];

                string objectDisplayName = null;
                try
                {
                    moniker.GetDisplayName(bindContext, null, out objectDisplayName);
                }
                catch (UnauthorizedAccessException)
                {
                    // Some ROT objects require elevated permissions.
                }

                if (!string.IsNullOrWhiteSpace(objectDisplayName))
                {
                    runningObjectDisplayNameList.Add(objectDisplayName);
                    if (objectDisplayName.EndsWith(displayName, StringComparison.Ordinal))
                    {
                        runningObjectTable.GetObject(moniker, out runningObject);
                        if (runningObject == null)
                        {
                            throw new InvalidOperationException($"Failed to get running object with display name {displayName}");
                        }
                    }
                }
            }

            runningObjectDisplayNames = runningObjectDisplayNameList;
            return runningObject;
        }

        private static ISetupInstance GetSetupInstance(bool isPreRelease)
        {
            return GetSetupInstances().First(i => IsPreRelease(i) == isPreRelease);
        }

        private static IEnumerable<ISetupInstance> GetSetupInstances()
        {
            ISetupConfiguration setupConfiguration = new SetupConfiguration();
            IEnumSetupInstances enumerator = setupConfiguration.EnumInstances();

            int count;
            do
            {
                ISetupInstance[] setupInstances = new ISetupInstance[1];
                enumerator.Next(1, setupInstances, out count);
                if (count == 1 &&
                    setupInstances != null &&
                    setupInstances.Length == 1 &&
                    setupInstances[0] != null)
                {
                    yield return setupInstances[0];
                }
            }
            while (count == 1);
        }

        private static bool IsPreRelease(ISetupInstance setupInstance)
        {
            ISetupInstanceCatalog setupInstanceCatalog = (ISetupInstanceCatalog)setupInstance;
            return setupInstanceCatalog.IsPrerelease();
        }

        private static class NativeMethods
        {
            [DllImport("ole32.dll")]
            public static extern int CreateBindCtx(uint reserved, out IBindCtx ppbc);

            [DllImport("ole32.dll")]
            public static extern void GetRunningObjectTable(int reserved, out IRunningObjectTable prot);
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie programu Visual Studio](locating-visual-studio.md)
- [Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora](walkthrough-accessing-the-dte-object-from-an-editor-extension.md)
