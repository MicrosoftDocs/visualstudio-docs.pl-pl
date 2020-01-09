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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597311"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta składniki

Wyświetla składniki, które można dodać do Visual Basic C# i projektantów dla Windows Forms. Oprócz składników programu .NET, które są dołączone do programu Visual Studio, takich jak składniki <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog>, możesz dodać własne składniki programu lub innych firm do tej karty.

Aby wyświetlić tę kartę, Otwórz projektanta Windows Forms. Wybierz pozycję **wyświetl** > **Przybornik**. W **przyborniku**wybierz kartę **składniki** .

## <a name="components"></a>Składniki

**BackgroundWorker**

Tworzy wystąpienie składnika <xref:System.ComponentModel.BackgroundWorker>, które może uruchamiać operację w oddzielnym, dedykowanym wątku. Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Tworzy wystąpienie składnika <xref:System.DirectoryServices.DirectoryEntry>, które hermetyzuje węzeł lub obiekt w hierarchii Active Directory i może służyć do współpracy z dostawcami usług Active Directory.

**DirectorySearcher**

Tworzy wystąpienie składnika <xref:System.DirectoryServices.DirectorySearcher>, za pomocą którego można wykonywać zapytania dotyczące Active Directory.

**ErrorProvider**

Tworzy wystąpienie składnika <xref:System.Windows.Forms.ErrorProvider>, które wskazuje użytkownikowi końcowemu, że formant w formularzu ma skojarzony z nim błąd. Aby uzyskać więcej informacji, zobacz [składnik ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Tworzy wystąpienie składnika <xref:System.Diagnostics.EventLog>, którego można użyć do współpracy z systemem i dziennikami zdarzeń niestandardowych, w tym zapisywania zdarzeń w dzienniku i odczytywania danych dziennika.

**FileSystemWatcher**

Tworzy wystąpienie składnika <xref:System.IO.FileSystemWatcher>, którego można użyć do monitorowania zmian w dowolnym katalogu lub pliku, do którego masz dostęp.

**HelpProvider**

Tworzy wystąpienie składnika <xref:System.Windows.Forms.HelpProvider>, które zapewnia podręczną lub pomoc online dla kontrolek. Aby uzyskać więcej informacji, zobacz [składnik HelpProvider —](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Tworzy wystąpienie składnika <xref:System.Windows.Forms.ImageList>, które udostępnia metody zarządzania kolekcją obiektów <xref:System.Drawing.Image>. Aby uzyskać więcej informacji, zobacz [składnik ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Tworzy wystąpienie składnika <xref:System.Messaging.MessageQueue>, którego można użyć do współdziałania z kolejkami komunikatów, w tym odczytywanie komunikatów z i zapisywanie komunikatów w kolejkach, przetwarzanie transakcji i wykonywanie zadań administracyjnych kolejki.

**PerformanceCounter**

Tworzy wystąpienie składnika <xref:System.Diagnostics.PerformanceCounter>, którego można użyć do współdziałania z licznikami wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywanie obliczeń na danych licznika.

**Podstawowych**

Tworzy wystąpienie składnika <xref:System.Diagnostics.Process>, za pomocą którego można zatrzymywać i uruchamiać dane skojarzone z procesami w systemie oraz manipulować nimi.

**SerialPort**

Tworzy wystąpienie składnika <xref:System.IO.Ports.SerialPort>, które zapewnia synchroniczną, opartą na zdarzeniach we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego.

**ServiceController**

Tworzy wystąpienie składnika <xref:System.ServiceProcess.ServiceController>, którego można użyć do manipulowania istniejącymi usługami, w tym uruchamiania i zatrzymywania usług oraz wysyłania do nich poleceń.

**Timer**

Tworzy wystąpienie składnika <xref:System.Windows.Forms.Timer>, którego można użyć w celu dodania funkcji opartych na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz temat [składnik czasomierza](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Istnieje również <xref:System.Timers.Timer> systemowa, którą można dodać do **przybornika** , <xref:System.Timers.Timer> jest zoptymalizowana pod kątem aplikacji serwerowych, a <xref:System.Windows.Forms.Timer> Windows Forms najlepiej nadaje się do użycia na Windows Forms.

## <a name="see-also"></a>Zobacz także

- [Kontrolki do użycia na Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Wybierz elementy paska narzędzi, składniki WPF](choose-toolbox-items-wpf-components.md)
- [Przybornik](../../ide/reference/toolbox.md)
