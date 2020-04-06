---
title: 'Jak: Uzyskaj usługę | Dokumenty firmy Microsoft'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710955"
---
# <a name="how-to-get-a-service"></a>Jak: Uzyskaj usługę

Często trzeba uzyskać usługi Visual Studio, aby uzyskać dostęp do różnych funkcji. Ogólnie rzecz biorąc usługa Visual Studio udostępnia jeden lub więcej interfejsów, których można użyć. Większość usług można uzyskać z VSPackage.

Każdy VSPackage, który <xref:Microsoft.VisualStudio.Shell.Package> pochodzi z i który został poprawnie umiejscowiony można poprosić o każdej usługi globalnej. Ponieważ `Package` klasa implementuje, <xref:System.IServiceProvider>wszelkie VSPackage, `Package` który pochodzi od jest również dostawcą usług.

Gdy program Visual <xref:Microsoft.VisualStudio.Shell.Package>Studio ładuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> przekazuje obiekt do metody podczas inicjowania. Jest to tak zwane *usymulanie* VSPackage. Klasa `Package` zawija tego dostawcę <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> usług i udostępnia metodę uzyskiwania usług.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Uzyskiwanie usługi z zainicjowanego programu VSPackage

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierał zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX o nazwie `GetServiceExtension`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Teraz dodaj niestandardowy szablon elementu polecenia o nazwie **GetServiceCommand**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *GetServiceCommand.cs*. Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, [Utwórz rozszerzenie za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. W *GetServiceCommand.cs*usunąć treść `MenuItemCommand` metody i dodać następujący kod:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Ten kod pobiera usługę SVsActivityLog i <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rzuca go do interfejsu, który może służyć do zapisu w dzienniku aktywności. Na przykład zobacz [Jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

5. W menu **Narzędzia** wystąpienia eksperymentalnego znajdź przycisk **Wywołaj GetServiceCommand.** Po kliknięciu tego przycisku powinien zostać wyświetlony okno komunikatu z napisem **Znaleziono usługę dziennika aktywności.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Uzyskiwanie usługi z okna narzędzia lub kontenera sterowania

Czasami może być konieczne uzyskanie usługi z okna narzędzia lub kontenera formantu, który nie został umiejscowiony, lub został umiejscowiony u dostawcy usług, który nie wie o żądanej usłudze. Na przykład można zapisać w dzienniku aktywności z poziomu formantu.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Metoda statyczna opiera się na buforowanym dostawcy usług, który jest inicjowany po raz pierwszy wszystkie VSPackage pochodzi z <xref:Microsoft.VisualStudio.Shell.Package> jest zlokalizowany.

Ponieważ konstruktor VSPackage jest wywoływana przed vspackage jest umiejscowiona, usługi globalne są zazwyczaj niedostępne z wewnątrz konstruktora VSPackage. Zobacz [Jak: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md) w celu obejścia problemu.

Oto przykład sposobu, aby uzyskać usługę w oknie narzędzia lub innych non-VSPackage element.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Uzyskiwanie usługi z obiektu DTE

Można również uzyskać <xref:EnvDTE.DTEClass> usługi z obiektu. Jednak należy uzyskać DTE obiektu jako usługi z VSPackage lub <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> wywołując metodę statyczną.

Obiekt DTE implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, którego można użyć do <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>kwerendy dla usługi za pomocą programu .

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

- [Jak: Świadczenie usług](../extensibility/how-to-provide-a-service.md)
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
- [Podstawowe usługi](../extensibility/internals/service-essentials.md)
