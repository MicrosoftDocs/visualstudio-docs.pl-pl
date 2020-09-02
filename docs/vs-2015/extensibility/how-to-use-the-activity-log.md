---
title: 'Instrukcje: korzystanie z dziennika aktywności | Microsoft Docs'
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
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824258"
---
# <a name="how-to-use-the-activity-log"></a>Instrukcje: Korzystanie z dziennika aktywności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage może zapisywać komunikaty w dzienniku aktywności. Ta funkcja jest szczególnie przydatna w przypadku debugowania pakietów VSPackage w środowiskach detalicznych.  
  
> [!TIP]
> Dziennik aktywności jest zawsze włączony. Program Visual Studio utrzymuje stopniowe buforu ostatnich 100 wpisów, a także pierwsze dziesięć wpisów, które zawierają ogólne informacje o konfiguracji.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Aby napisać wpis do dziennika aktywności  
  
1. Wstaw ten kod w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie lub w innej metodzie z wyjątkiem konstruktora pakietu VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ten kod pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługę i rzutuje ją na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Zapisuje wpis informacyjny w dzienniku aktywności przy użyciu bieżącego kontekstu kulturowego.  
  
2. Po załadowaniu pakietu VSPackage (zazwyczaj w przypadku wywołania polecenia lub otwarciu okna) tekst jest zapisywana w dzienniku aktywności.  
  
### <a name="to-examine-the-activity-log"></a>Aby przejrzeć dziennik aktywności  
  
1. Znajdź dziennik aktywności w podfolderze dla danych programu Visual Studio: *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML..  
  
2. Otwórz dziennik aktywności przy użyciu dowolnego edytora tekstu. Oto typowy wpis:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ponieważ dziennik aktywności jest usługą, dziennik aktywności jest niedostępny w konstruktorze pakietu VSPackage.  
  
 Dziennik aktywności należy uzyskać tuż przed zapisaniem w nim. Nie Buforuj ani nie zapisuj dziennika aktywności do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Rozwiązywanie problemów z pakietów VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
