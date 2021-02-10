---
title: Przybornik, karta Składniki
description: Dowiedz się więcej na temat składników znalezionych na karcie składniki okna przybornika.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adbc2611cf0d0e08ef356e91e25ed0c4854c4386
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965047"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta składniki

Wyświetla składniki, które można dodać do Visual Basic i projektantów C# dla Windows Forms. Oprócz składników .NET, które są dołączone do programu Visual Studio, takich jak <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> składniki i, można dodać własne składniki programu lub innych firm do tej karty.

Aby wyświetlić tę kartę, Otwórz projektanta Windows Forms. Wybierz pozycję **Widok**  >  **Przybornik**. W **przyborniku** wybierz kartę **składniki** .

## <a name="components"></a>Składniki

**BackgroundWorker**

Tworzy <xref:System.ComponentModel.BackgroundWorker> wystąpienie składnika, które może uruchamiać operację w oddzielnym, dedykowanym wątku. Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**Elementu**

Tworzy <xref:System.DirectoryServices.DirectoryEntry> wystąpienie składnika, które hermetyzuje węzeł lub obiekt w hierarchii Active Directory i może służyć do współpracy z Active Directory dostawcami usług.

**DirectorySearcher**

Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, za pomocą którego można wykonywać zapytania dotyczące Active Directory.

**ErrorProvider**

Tworzy <xref:System.Windows.Forms.ErrorProvider> wystąpienie składnika, które wskazuje użytkownikowi końcowemu, że formant w formularzu ma związany z nim błąd. Aby uzyskać więcej informacji, zobacz [składnik ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**Elemencie**

Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika, którego można użyć do współpracy z systemem i dziennikami zdarzeń niestandardowych, w tym zapisywania zdarzeń w dzienniku i odczytywania danych dziennika.

**FileSystemWatcher**

Tworzy <xref:System.IO.FileSystemWatcher> wystąpienie składnika, którego można użyć do monitorowania zmian w dowolnym katalogu lub pliku, do którego masz dostęp.

**HelpProvider —**

Tworzy <xref:System.Windows.Forms.HelpProvider> wystąpienie składnika, które zapewnia podręczną lub pomoc online dla kontrolek. Aby uzyskać więcej informacji, zobacz [składnik HelpProvider —](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Obrazów**

Tworzy <xref:System.Windows.Forms.ImageList> wystąpienie składnika, które dostarcza metody do zarządzania kolekcją <xref:System.Drawing.Image> obiektów. Aby uzyskać więcej informacji, zobacz [składnik ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Tworzy <xref:System.Messaging.MessageQueue> wystąpienie składnika, którego można użyć do współdziałania z kolejkami komunikatów, w tym odczytywanie komunikatów z i zapisywanie komunikatów w kolejkach, przetwarzanie transakcji i wykonywanie zadań administracyjnych kolejki.

**PerformanceCounter**

Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, którego można użyć do współdziałania z licznikami wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywanie obliczeń na danych licznika.

**Proces**

Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika, którego można użyć do zatrzymywania, uruchamiania i manipulowania danymi związanymi z procesami w systemie.

**Klasy SerialPort**

Tworzy <xref:System.IO.Ports.SerialPort> wystąpienie składnika, które zapewnia synchroniczną i sterowaną zdarzeniami we/wy dostęp do Stanów PIN i przerwania oraz dostęp do właściwości sterownika szeregowego.

**ServiceController**

Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika, którego można użyć do manipulowania istniejącymi usługami, w tym uruchamiania i zatrzymywania usług i wysyłania do nich poleceń.

**Czasomierz**

Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika, którego można użyć w celu dodania funkcji opartych na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz temat [składnik czasomierza](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Istnieje również system <xref:System.Timers.Timer> , który można dodać do **przybornika** <xref:System.Timers.Timer> , który jest zoptymalizowany pod kątem aplikacji serwera, a Windows Forms <xref:System.Windows.Forms.Timer> jest najlepiej dostosowany do korzystania z Windows Forms.

## <a name="see-also"></a>Zobacz też

- [Kontrolki do użycia na Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Wybieranie elementów przybornika, składniki WPF](choose-toolbox-items-wpf-components.md)
- [Przybornik](../../ide/reference/toolbox.md)
