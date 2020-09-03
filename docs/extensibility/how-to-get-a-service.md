---
title: 'Instrukcje: Uzyskiwanie usługi | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a401103112096a1089b59ba3733d19480f93e891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905836"
---
# <a name="how-to-get-a-service"></a>Instrukcje: Uzyskiwanie usługi

Często trzeba uzyskać dostęp do różnych funkcji usług Visual Studio. Ogólnie rzecz biorąc, usługa Visual Studio udostępnia jeden lub więcej interfejsów, których można użyć. Większość usług można uzyskać z pakietu VSPackage.

Każdy pakietu VSPackage, który pochodzi z <xref:Microsoft.VisualStudio.Shell.Package> i który został prawidłowo zlokalizowany, może poprosił o jakąkolwiek usługę globalną. Ponieważ `Package` Klasa implementuje <xref:System.IServiceProvider> , każdy pakietu VSPackage pochodzący od `Package` jest również dostawcą usług.

Gdy program Visual Studio ładuje <xref:Microsoft.VisualStudio.Shell.Package> , przekazuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> obiekt do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody podczas inicjalizacji. Ta *nazwa jest* nazywana pakietu VSPackage. `Package`Klasa otacza tego dostawcę usług i zapewnia <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodę uzyskiwania usług.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Pobieranie usługi z zainicjowane pakietu VSPackage

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt VSIX o nazwie `GetServiceExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Teraz Dodaj niestandardowy szablon elementu polecenia o nazwie **GetServiceCommand**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *GetServiceCommand.cs*. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, [Utwórz rozszerzenie za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. W *GetServiceCommand.cs*Usuń treść `MenuItemCommand` metody i Dodaj następujący kod:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Ten kod pobiera usługę SVsActivityLog i rzutuje ją na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może być używany do zapisywania w dzienniku aktywności. Aby zapoznać się z przykładem, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W menu **Narzędzia** wystąpienia eksperymentalnego Znajdź przycisk **Wywołaj GetServiceCommand** . Po kliknięciu tego przycisku zostanie wyświetlone okno komunikatu z informacją o **znalezieniu usługi dziennika aktywności.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Pobieranie usługi z okna narzędzi lub kontenera kontrolek

Czasami może być konieczne uzyskanie usługi z okna narzędzi lub kontenera kontroli, który nie został zlokalizowany, lub w innym systemie, który jest zlokalizowany przez dostawcę usług, który nie wie o żądaną usługę. Na przykład możesz chcieć zapisać w dzienniku aktywności z poziomu kontrolki.

Metoda statyczna <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> bazuje na buforowanym dostawcy usług, który jest inicjowany po raz pierwszy od pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .

Ponieważ Konstruktor pakietu VSPackage jest wywoływany przed zlokalizowaniem pakietu VSPackage, usługi globalne są zwykle niedostępne z poziomu konstruktora pakietu VSPackage. Zobacz [jak: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) w celu obejścia tego problemu.

Oto przykład sposobu uzyskania usługi w oknie narzędzi lub innym elemencie pakietu VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Pobieranie usługi z obiektu DTE

Możesz również pobrać usługi z <xref:EnvDTE.DTEClass> obiektu. Należy jednak uzyskać obiekt DTE jako usługę z pakietu VSPackage lub przez wywołanie metody statycznej <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

Implementuje obiekt DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , którego można użyć do wykonywania zapytań dotyczących usługi przy użyciu <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

Oto jak uzyskać usługę z obiektu DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Instrukcje: dostarczanie usługi](../extensibility/how-to-provide-a-service.md)
- [Używanie i udostępnianie usług](../extensibility/using-and-providing-services.md)
- [Podstawowa usługa](../extensibility/internals/service-essentials.md)
