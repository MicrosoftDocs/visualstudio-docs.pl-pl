---
title: Przybornik, karta składniki | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98955b3f9428126775ca6a58f19a12de416833c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689493"
---
# <a name="toolbox-components-tab"></a>Przybornik, karta Składniki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla składniki, które można dodać do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektantów. Oprócz [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] składniki, które są dołączone [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], takich jak <xref:System.Messaging.MessageQueue> i <xref:System.Diagnostics.EventLog> składników, możesz dodać swoje składniki posiada lub w innej firmy do tej karty. Aby uzyskać więcej informacji, zobacz [jak: Karty przybornika manipulowania](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Aby wyświetlić tę kartę, z **widoku** menu, wybierz opcję **przybornika**. W **przybornika**, wybierz opcję **składniki** kartę.  
  
 **BackgroundWorker**  
 Tworzy `System.ComponentModel.BackgroundWorker` wystąpienie składnika, który można uruchomić operację na oddzielne, wyspecjalizowany wątek.  
  
 **DirectoryEntry**  
 Tworzy <xref:System.DirectoryServices.DirectoryEntry> instancji składnika, która hermetyzuje węzła lub obiektu w hierarchii usługi Active Directory i może służyć do interakcji z dostawcami usług Active Directory.  
  
 **DirectorySearcher**  
 Tworzy <xref:System.DirectoryServices.DirectorySearcher> wystąpienie składnika, który służy do wykonywania zapytań względem usługi Active Directory.  
  
 **ErrorProvider**  
 Tworzy `System.Windows.Forms.ErrorProvider` wystąpienia składnika, co oznacza użytkownika końcowego, że formant w formularzu ma skojarzone z nim błąd.  
  
 **EventLog**  
 Tworzy <xref:System.Diagnostics.EventLog> wystąpienie składnika służy do interakcji z systemu i niestandardowych dzienników zdarzeń, w tym zapisywanie zdarzeń do dziennika i odczytywanie danych dziennika. Aby uzyskać więcej informacji, zobacz [wprowadzenie do składnik EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Tworzy <xref:System.IO.FileSystemWatcher> wystąpienia składnika, używanego na potrzeby monitorowania zmieni się na dowolny katalog lub plik, do których masz dostęp. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie wystąpienia klasy FileSystemWatcher składnika](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Tworzy `System.Windows.Forms.HelpProvider` instancji składnika, która zawiera menu podręczne lub pomoc dla formantów.  
  
 **ImageList**  
 Tworzy `System.Windows.Forms.ImageList` wystąpienie składnika, który udostępnia metody umożliwiające zarządzanie kolekcją `System.Drawing.Image` obiektów.  
  
 **MessageQueue**  
 Tworzy <xref:System.Messaging.MessageQueue> instancji składnika, która służy do interakcji z kolejek komunikatów, m.in. odczytywania komunikatów z oraz zapisywanie komunikatów do kolejki przetwarzania transakcji i wykonywania zadań administracyjnych w kolejce. Aby uzyskać więcej informacji, zobacz [przy użyciu składników obsługi wiadomości](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Tworzy <xref:System.Diagnostics.PerformanceCounter> wystąpienie składnika, który służy do interakcji z liczników wydajności Windows, w tym tworzenie nowych kategorii i wystąpienia, odczytywanie wartości z liczników i wykonywaniu obliczeń na danych licznika. Aby uzyskać więcej informacji, zobacz [progi monitorowania wydajności](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Proces**  
 Tworzy <xref:System.Diagnostics.Process> wystąpienie składnika można zatrzymać, uruchomić i manipulowanie danymi skojarzone z procesami w systemie. Aby uzyskać więcej informacji, zobacz [monitorowanie i zarządzanie procesami Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Tworzy `System.IO.Ports.SerialPort` instancji składnika, która zapewnia synchroniczne i oparte na zdarzeniach operacji We/Wy, dostęp stanom pin i podziału i dostęp do właściwości sterownika szeregowe.  
  
 **ServiceController**  
 Tworzy <xref:System.ServiceProcess.ServiceController> wystąpienie składnika służy do modyfikowania istniejących usług, w tym uruchamianie i zatrzymywanie usług oraz wysyłania poleceń do nich. Aby uzyskać więcej informacji, zobacz [monitorowania usług Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Timer**  
 Tworzy <xref:System.Windows.Forms.Timer> wystąpienie składnika można użyć, aby dodać funkcje oparte na czasie do aplikacji z systemem Windows. Aby uzyskać więcej informacji, zobacz [składnika Timer formularzy](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).  
  
> [!NOTE]
> Istnieje również opartych na systemie <xref:System.Timers.Timer> , można dodać do **przybornika** to <xref:System.Timers.Timer> jest zoptymalizowany dla aplikacji serwerowych i formularze Windows <xref:System.Windows.Forms.Timer> najlepiej nadaje się do użycia w formularzach Windows Forms.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie przy użyciu składników](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Programowanie składników — wskazówki](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Przybornik](../../ide/reference/toolbox.md)   
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
