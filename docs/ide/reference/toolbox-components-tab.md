---
title: Przybornik, karta Składniki
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00417b853fbaac9e57d93553974cab786dce5aad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949132"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta składniki

Wyświetla składniki, które można dodać do projektantów w Visual Basic i C# dla formularzy Windows Forms. Oprócz składników .NET Framework, które znajdują się za pomocą programu Visual Studio, takie jak <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog> składników, możesz dodać swoje składniki posiada lub w innej firmy do tej karty.

Aby wyświetlić tę kartę, otwórz projektanta Windows Forms. Wybierz **widoku** > **przybornika**. W **przybornika**, wybierz opcję **składniki** kartę.

## <a name="components"></a>Składniki

**BackgroundWorker**

Tworzy <xref:System.ComponentModel.BackgroundWorker> wystąpienie składnika, który można uruchomić operację na oddzielne, wyspecjalizowany wątek. Aby uzyskać więcej informacji, zobacz [BackgroundWorker, składnik](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Tworzy <xref:System.DirectoryServices.DirectoryEntry> instancji składnika, która hermetyzuje węzła lub obiektu w hierarchii usługi Active Directory i może służyć do interakcji z dostawcami usług Active Directory.

**DirectorySearcher**

Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, który służy do wykonywania zapytań względem usługi Active Directory.

**ErrorProvider**

Tworzy <xref:System.Windows.Forms.ErrorProvider> wystąpienia składnika, co oznacza użytkownika końcowego, że formant w formularzu ma skojarzone z nim błąd. Aby uzyskać więcej informacji, zobacz [ErrorProvider, składnik](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika służy do interakcji z systemu i niestandardowych dzienników zdarzeń, w tym zapisywanie zdarzeń do dziennika i odczytywanie danych dziennika.

**FileSystemWatcher**

Tworzy <xref:System.IO.FileSystemWatcher> wystąpienia składnika, używanego na potrzeby monitorowania zmieni się na dowolny katalog lub plik, do których masz dostęp.

**HelpProvider**

Tworzy <xref:System.Windows.Forms.HelpProvider> instancji składnika, która zawiera menu podręczne lub pomoc dla formantów. Aby uzyskać więcej informacji, zobacz [HelpProvider, składnik](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Tworzy <xref:System.Windows.Forms.ImageList> wystąpienie składnika, który udostępnia metody umożliwiające zarządzanie kolekcją <xref:System.Drawing.Image> obiektów. Aby uzyskać więcej informacji, zobacz [składnika ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Tworzy <xref:System.Messaging.MessageQueue> instancji składnika, która służy do interakcji z kolejek komunikatów, m.in. odczytywania komunikatów z oraz zapisywanie komunikatów do kolejki przetwarzania transakcji i wykonywania zadań administracyjnych w kolejce.

**PerformanceCounter**

Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, który służy do interakcji z liczników wydajności Windows, w tym tworzenie nowych kategorii i wystąpienia, odczytywanie wartości z liczników i wykonywaniu obliczeń na danych licznika.

**Proces**

Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika można zatrzymać, uruchomić i manipulowanie danymi skojarzone z procesami w systemie.

**SerialPort**

Tworzy <xref:System.IO.Ports.SerialPort> instancji składnika, która zapewnia synchroniczne i oparte na zdarzeniach operacji We/Wy, dostęp stanom pin i podziału i dostęp do właściwości sterownika szeregowe.

**ServiceController**

Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika służy do modyfikowania istniejących usług, w tym uruchamianie i zatrzymywanie usług oraz wysyłania poleceń do nich.

**Timer**

Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika można użyć, aby dodać funkcje oparte na czasie do aplikacji z systemem Windows. Aby uzyskać więcej informacji, zobacz [składnika Timer formularzy](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Istnieje również opartych na systemie <xref:System.Timers.Timer> , można dodać do **przybornika** to <xref:System.Timers.Timer> jest zoptymalizowany dla aplikacji serwerowych i formularze Windows <xref:System.Windows.Forms.Timer> najlepiej nadaje się do użycia w formularzach Windows Forms.

## <a name="see-also"></a>Zobacz także

- [Kontrolki do użycia w formularzach Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Wybierz elementy paska narzędzi, składniki WPF](choose-toolbox-items-wpf-components.md)
- [Przybornik](../../ide/reference/toolbox.md)