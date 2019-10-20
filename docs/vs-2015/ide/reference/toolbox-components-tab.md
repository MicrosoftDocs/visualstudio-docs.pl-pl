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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661569"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla składniki, które można dodać do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektantów. Oprócz składników [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], które są dołączone do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], takich jak składniki <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog>, można dodać własne składniki programu lub innych firm do tej karty. Aby uzyskać więcej informacji, zobacz [How to: manipulowanie kartami przybornika](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Aby wyświetlić tę kartę, w menu **Widok** wybierz pozycję **Przybornik**. W **przyborniku**wybierz kartę **składniki** .

 **BackgroundWorker** Tworzy wystąpienie składnika `System.ComponentModel.BackgroundWorker`, które może uruchamiać operację w oddzielnym, dedykowanym wątku.

 **DirectoryEntry** Tworzy wystąpienie składnika <xref:System.DirectoryServices.DirectoryEntry>, które hermetyzuje węzeł lub obiekt w hierarchii Active Directory i może służyć do współpracy z dostawcami usług Active Directory.

 **DirectorySearcher** Tworzy wystąpienie składnika <xref:System.DirectoryServices.DirectorySearcher>, za pomocą którego można wykonywać zapytania dotyczące Active Directory.

 **ErrorProvider** Tworzy wystąpienie składnika `System.Windows.Forms.ErrorProvider`, które wskazuje użytkownikowi końcowemu, że formant w formularzu ma skojarzony z nim błąd.

 **Dziennik zdarzeń** Tworzy wystąpienie składnika <xref:System.Diagnostics.EventLog>, którego można użyć do współpracy z systemem i dziennikami zdarzeń niestandardowych, w tym zapisywania zdarzeń w dzienniku i odczytywania danych dziennika. Aby uzyskać więcej informacji, zobacz [wprowadzenie do składnika EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Tworzy wystąpienie składnika <xref:System.IO.FileSystemWatcher>, którego można użyć do monitorowania zmian w dowolnym katalogu lub pliku, do którego masz dostęp. Aby uzyskać więcej informacji, zobacz [How to: Configure FileSystemWatcher Component Instances](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider —** Tworzy wystąpienie składnika `System.Windows.Forms.HelpProvider`, które zapewnia podręczną lub pomoc online dla kontrolek.

 **Lista ImageList** Tworzy wystąpienie składnika `System.Windows.Forms.ImageList`, które udostępnia metody zarządzania kolekcją obiektów `System.Drawing.Image`.

 **MessageQueue** Tworzy wystąpienie składnika <xref:System.Messaging.MessageQueue>, którego można użyć do współdziałania z kolejkami komunikatów, w tym odczytywanie komunikatów z i zapisywanie komunikatów w kolejkach, przetwarzanie transakcji i wykonywanie zadań administracyjnych kolejki. Aby uzyskać więcej informacji, zobacz [using Messaging Components](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Tworzy wystąpienie składnika <xref:System.Diagnostics.PerformanceCounter>, którego można użyć do współdziałania z licznikami wydajności systemu Windows, w tym tworzenie nowych kategorii i wystąpień, odczytywanie wartości z liczników i wykonywanie obliczeń na danych licznika. Aby uzyskać więcej informacji, zobacz [monitorowanie progów wydajności](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Proces** Tworzy wystąpienie składnika <xref:System.Diagnostics.Process>, za pomocą którego można zatrzymywać i uruchamiać dane skojarzone z procesami w systemie oraz manipulować nimi. Aby uzyskać więcej informacji, zobacz [monitorowanie procesów systemu Windows i zarządzanie nimi](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **Klasy SerialPort** Tworzy wystąpienie składnika `System.IO.Ports.SerialPort`, które zapewnia synchroniczną, opartą na zdarzeniach we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego.

 **Kontroler ServiceController** Tworzy wystąpienie składnika <xref:System.ServiceProcess.ServiceController>, którego można użyć do manipulowania istniejącymi usługami, w tym uruchamiania i zatrzymywania usług oraz wysyłania do nich poleceń. Aby uzyskać więcej informacji, zobacz [monitorowanie usług systemu Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Czasomierz** Tworzy wystąpienie składnika <xref:System.Windows.Forms.Timer>, którego można użyć w celu dodania funkcji opartych na czasie do aplikacji opartych na systemie Windows. Aby uzyskać więcej informacji, zobacz temat [składnik czasomierza](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Istnieje również <xref:System.Timers.Timer> systemowa, którą można dodać do **przybornika** , <xref:System.Timers.Timer> jest zoptymalizowana pod kątem aplikacji serwerowych, a <xref:System.Windows.Forms.Timer> Windows Forms najlepiej nadaje się do użycia na Windows Forms.

## <a name="see-also"></a>Zobacz też
 [Programowanie ze](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [składnikami przewodniki programowania składników](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) [](../../ide/reference/toolbox.md) — [okno dialogowe Wybieranie elementów przybornika (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
