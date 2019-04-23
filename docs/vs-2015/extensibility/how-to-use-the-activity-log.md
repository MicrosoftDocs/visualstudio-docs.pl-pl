---
title: 'Instrukcje: Korzystanie z dziennika aktywności | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 812862c3eaf99b7459bb422e174f8fe155ea384a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042590"
---
# <a name="how-to-use-the-activity-log"></a>Instrukcje: Korzystanie z dziennika aktywności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage może zapisywać komunikaty w dzienniku aktywności. Ta funkcja jest szczególnie przydatna podczas debugowania pakietów VSPackage w środowisku handlu detalicznego.  
  
> [!TIP]
>  Dziennik aktywności jest zawsze włączone. Visual Studio przechowuje stopniowe buforu wpisy ostatnio sto, a także pierwszych dziesięciu zapisów, które udostępniają informacje o konfiguracji ogólnej.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Aby zapisać wpis w dzienniku aktywności  
  
1. Wstaw ten kod w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody lub innej metody, z wyjątkiem Konstruktor pakietu VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ten kod pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługi i rzutuje je na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> zapisuje wpis informacyjny w dzienniku aktywności w kontekście bieżącej kultury.  
  
2. Podczas ładowania pakietu VSPackage (zazwyczaj podczas wywoływania polecenia lub okno jest otwarty), tekst został napisany z dziennikiem aktywności.  
  
### <a name="to-examine-the-activity-log"></a>Aby sprawdzić dziennik aktywności  
  
1. Znajdowanie dziennika aktywności w podfolderze dla danych programu Visual Studio: *% AppData %* \Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2. Otwórz dziennik aktywności, za pomocą dowolnego edytora tekstów. Poniżej przedstawiono typowe wpis:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ponieważ dziennik aktywności jest usługą, dziennik aktywności jest niedostępna w Konstruktorze pakietu VSPackage.  
  
 Dziennik aktywności powinna uzyskać tuż przed zapisu do niego. Nie w pamięci podręcznej lub dziennika aktywności do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Rozwiązywanie problemów z pakietami VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
