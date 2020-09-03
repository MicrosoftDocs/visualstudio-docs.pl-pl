---
title: Ładowanie pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702966"
---
# <a name="load-vspackages"></a>Ładuj pakietów VSPackage
Pakietów VSPackage są ładowane do programu Visual Studio tylko wtedy, gdy ich funkcjonalność jest wymagana. Na przykład pakietu VSPackage jest ładowany, gdy program Visual Studio używa fabryki projektu lub usługi implementującej implementację pakietu VSPackage. Ta funkcja jest nazywana opóźnionym ładowaniem, które jest używane w miarę możliwości w celu zwiększenia wydajności.

> [!NOTE]
> Program Visual Studio może określić pewne informacje pakietu VSPackage, takie jak polecenia oferowane przez pakietu VSPackage, bez ładowania pakietu VSPackage.

 Pakietów VSPackage można ustawić na automatyczne ładowanie w kontekście określonego interfejsu użytkownika, na przykład po otwarciu rozwiązania. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Atrybut ustawia ten kontekst.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatyczne ładowanie pakietu VSPackage w określonym kontekście

- Dodaj `ProvideAutoLoad` atrybut do atrybutów pakietu VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Zapoznaj się z wyliczonymi polami elementu, <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Aby uzyskać listę kontekstów interfejsu użytkownika i ich wartości identyfikatorów GUID.

- Ustaw punkt przerwania w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie.

- Kompiluj pakietu VSPackage i Rozpocznij debugowanie.

- Załaduj rozwiązanie lub utwórz je.

     Pakietu VSPackage ładuje i zatrzyma się w punkcie przerwania.

## <a name="force-a-vspackage-to-load"></a>Wymuś załadowanie pakietu VSPackage
 W pewnych okolicznościach pakietu VSPackage może wymagać wymuszenia załadowania innego pakietu VSPackage. Na przykład lekki pakietu VSPackage może ładować większy pakietu VSPackage w kontekście, który nie jest dostępny jako CMDUIContext.

 Możesz użyć metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> Aby wymusić załadowanie pakietu VSPackage.

- Wstaw ten kod do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody pakietu VSPackage, która wymusza załadowanie innego pakietu VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Po zainicjowaniu pakietu VSPackage zostanie wymuszone `PackageToBeLoaded` załadowanie.

     Wymuś ładowanie nie należy używać do komunikacji pakietu VSPackage. Użyj zamiast tego [usług](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
