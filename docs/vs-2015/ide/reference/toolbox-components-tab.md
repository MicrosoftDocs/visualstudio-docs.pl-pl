---
title: Przybornik, karta składniki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661569"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla składniki, które można dodać do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektantów. Oprócz [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] składników, które są dołączone do programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , takich jak <xref:System.Messaging.MessageQueue> składniki i <xref:System.Diagnostics.EventLog> , można dodać do tej karty składniki własne lub inne firmy. Aby uzyskać więcej informacji, zobacz [How to: manipulowanie kartami przybornika](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Aby wyświetlić tę kartę, w menu **Widok** wybierz pozycję **Przybornik**. W **przyborniku**wybierz kartę **składniki** .

 **BackgroundWorker** Tworzy `System.ComponentModel.BackgroundWorker` wystąpienie składnika, które może uruchamiać operację w oddzielnym, dedykowanym wątku.

 **DirectoryEntry** Tworzy <xref:System.DirectoryServices.DirectoryEntry> wystąpienie składnika, które hermetyzuje węzeł lub obiekt w hierarchii Active Directory i może służyć do współpracy z Active Directory dostawcami usług.

 **DirectorySearcher** Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, za pomocą którego można wykonywać zapytania dotyczące Active Directory.

 **ErrorProvider** Tworzy `System.Windows.Forms.ErrorProvider` wystąpienie składnika, które wskazuje użytkownikowi końcowemu, że formant w formularzu ma związany z nim błąd.

 **Dziennik zdarzeń** Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika, którego można użyć do współpracy z systemem i dziennikami zdarzeń niestandardowych, w tym zapisywania zdarzeń w dzienniku i odczytywania danych dziennika. Aby uzyskać więcej informacji, zobacz [wprowadzenie do składnika EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Tworzy <xref:System.IO.FileSystemWatcher> wystąpienie składnika, którego można użyć do monitorowania zmian w dowolnym katalogu lub pliku, do którego masz dostęp. Aby uzyskać więcej informacji, zobacz [How to: Configure FileSystemWatcher Component Instances](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider —** Tworzy `System.Windows.Forms.HelpProvider` wystąpienie składnika, które zapewnia podręczną lub pomoc online dla kontrolek.

 **Lista ImageList** Tworzy `System.Windows.Forms.ImageList` wystąpienie składnika, które dostarcza metody do zarządzania kolekcją `System.Drawing.Image` obiektów.

 **MessageQueue** Tworzy <xref:System.Messaging.MessageQueue> wystąpienie składnika, którego można użyć do współdziałania z kolejkami komunikatów, w tym odczytywanie komunikatów z i zapisywanie komunikatów w kolejkach, przetwarzanie transakcji i wykonywanie zadań administracyjnych kolejki. Aby uzyskać więcej informacji, zobacz [using Messaging Components](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, którego można użyć do współdziałania z licznikami wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywanie obliczeń na danych licznika. Aby uzyskać więcej informacji, zobacz [monitorowanie progów wydajności](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Proces** Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika, którego można użyć do zatrzymywania, uruchamiania i manipulowania danymi związanymi z procesami w systemie. Aby uzyskać więcej informacji, zobacz [monitorowanie procesów systemu Windows i zarządzanie nimi](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **Klasy SerialPort** Tworzy `System.IO.Ports.SerialPort` wystąpienie składnika, które zapewnia synchroniczną i sterowaną zdarzeniami we/wy dostęp do Stanów PIN i przerwania oraz dostęp do właściwości sterownika szeregowego.

 **Kontroler ServiceController** Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika, którego można użyć do manipulowania istniejącymi usługami, w tym uruchamiania i zatrzymywania usług i wysyłania do nich poleceń. Aby uzyskać więcej informacji, zobacz [monitorowanie usług systemu Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Czasomierz** Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika, którego można użyć w celu dodania funkcji opartych na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz temat [składnik czasomierza](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Istnieje również system <xref:System.Timers.Timer> , który można dodać do **przybornika** <xref:System.Timers.Timer> , który jest zoptymalizowany pod kątem aplikacji serwera, a Windows Forms <xref:System.Windows.Forms.Timer> jest najlepiej dostosowany do korzystania z Windows Forms.

## <a name="see-also"></a>Zobacz też
 [Programowanie ze](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [składnikami przewodniki programowania składników](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) [Toolbox](../../ide/reference/toolbox.md) — [okno dialogowe Wybieranie elementów przybornika (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
