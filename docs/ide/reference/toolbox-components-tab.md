---
title: Przybornik, karta Składniki
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5eb8c320a3190121d95395f7b359aa9ed978408
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597311"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki

Wyświetla składniki, które można dodać do projektantów języka Visual Basic i C# dla formularzy systemu Windows. Oprócz składników platformy .NET, które są dołączone do <xref:System.Messaging.MessageQueue> programu <xref:System.Diagnostics.EventLog> Visual Studio, takich jak składniki i składniki, można dodać własne lub innych firm składników do tej karty.

Aby wyświetlić tę kartę, otwórz projektanta formularzy systemu Windows. Wybierz **pozycję Wyświetl** > **przybornik**. W **przyborniku**wybierz kartę **Składniki.**

## <a name="components"></a>Składniki

**Backgroundworker**

Tworzy <xref:System.ComponentModel.BackgroundWorker> wystąpienie składnika, które można uruchomić operację na oddzielnym, dedykowanym wątku. Aby uzyskać więcej informacji, zobacz [BackgroundWorker składnik](/dotnet/framework/winforms/controls/backgroundworker-component).

**Directoryentry**

Tworzy <xref:System.DirectoryServices.DirectoryEntry> wystąpienie składnika, które hermetyzuje węzeł lub obiekt w hierarchii usługi Active Directory i może być używane do interakcji z dostawcami usług Usługi Active Directory.

**Directorysearcher**

Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, którego można używać do wykonywania kwerend względem usługi Active Directory.

**Errorprovider**

Tworzy <xref:System.Windows.Forms.ErrorProvider> wystąpienie składnika, które wskazuje użytkownikowi końcowemu, że formant w formularzu ma błąd skojarzony z nim. Aby uzyskać więcej informacji, zobacz [ErrorProvider component](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**Eventlog**

Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika, którego można używać do interakcji z systemowymi i niestandardowymi dziennikami zdarzeń, w tym zapisywania zdarzeń w dzienniku i odczytywania danych dziennika.

**Filesystemwatcher**

Tworzy <xref:System.IO.FileSystemWatcher> wystąpienie składnika, za pomocą którego można monitorować zmiany w dowolnym katalogu lub pliku, do którego masz dostęp.

**Helpprovider**

Tworzy <xref:System.Windows.Forms.HelpProvider> wystąpienie składnika, które zapewnia wyskakujące okienka lub pomoc online dla formantów. Aby uzyskać więcej informacji, zobacz [Składnik HelpProvider](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Imagelist**

Tworzy <xref:System.Windows.Forms.ImageList> wystąpienie składnika, który udostępnia <xref:System.Drawing.Image> metody zarządzania kolekcją obiektów. Aby uzyskać więcej informacji, zobacz [ImageList składnik](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**Messagequeue**

Tworzy <xref:System.Messaging.MessageQueue> wystąpienie składnika, którego można używać do interakcji z kolejkami komunikatów, w tym do odczytywania wiadomości i zapisywania wiadomości do kolejek, przetwarzania transakcji i wykonywania zadań administracyjnych kolejek.

**Performancecounter**

Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, którego można używać do interakcji z licznikami wydajności systemu Windows, w tym tworzenia nowych kategorii i wystąpień, odczytywania wartości z liczników i wykonywania obliczeń na danych liczników.

**Proces**

Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika, za pomocą którego można zatrzymać, uruchomić i manipulować danymi skojarzonymi z procesami w systemie.

**Serialport**

Tworzy <xref:System.IO.Ports.SerialPort> wystąpienie składnika, które zapewnia synchroniczne i oparte na zdarzeniach we/wy, dostęp do stanów przypięcia i przerwania oraz dostęp do właściwości sterownika szeregowego.

**Servicecontroller**

Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika, którego można używać do manipulowania istniejącymi usługami, w tym uruchamiania i zatrzymywania usług oraz wysyłania do nich poleceń.

**Czasomierz**

Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika, za pomocą którego można dodać funkcje oparte na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz [Składnik timera](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Istnieje również system oparty <xref:System.Timers.Timer> na tym, który można dodać do **przybornika** To <xref:System.Timers.Timer> <xref:System.Windows.Forms.Timer> jest zoptymalizowane pod kątem aplikacji serwerowych, a formularze systemu Windows najlepiej nadają się do użycia w formularzach systemu Windows.

## <a name="see-also"></a>Zobacz też

- [Formanty używane w formularzach systemu Windows](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Wybieranie elementów przybornika, składników WPF](choose-toolbox-items-wpf-components.md)
- [Przybornik](../../ide/reference/toolbox.md)
