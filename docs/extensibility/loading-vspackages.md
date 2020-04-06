---
title: Ładowanie pakietów VSPackage | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702966"
---
# <a name="load-vspackages"></a>Załaduj pakiety VSPackages
Pakiety VSPackages są ładowane do programu Visual Studio tylko wtedy, gdy ich funkcjonalność jest wymagana. Na przykład VSPackage jest ładowany, gdy visual studio używa fabryki projektu lub usługi, które vspackage implementuje. Ta funkcja jest nazywana opóźnionym ładowaniem, który jest używany, gdy jest to możliwe, aby zwiększyć wydajność.

> [!NOTE]
> Visual Studio można określić niektóre informacje VSPackage, takie jak polecenia, które oferuje VSPackage, bez ładowania VSPackage.

 VSPackages można ustawić do automatycznego ładowania w kontekście interfejsu użytkownika (UI), na przykład, gdy rozwiązanie jest otwarte. Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ustawia ten kontekst.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatyczne ładowanie pakietu VSPackage w określonym kontekście

- Dodaj `ProvideAutoLoad` atrybut do atrybutów VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Zobacz wyliczone pola <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> listy kontekstów interfejsu użytkownika i ich wartości guid.

- Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> w metodzie.

- Tworzenie VSPackage i rozpocząć debugowanie.

- Załaduj rozwiązanie lub utwórz je.

     VSPackage ładuje i zatrzymuje się w punkcie przerwania.

## <a name="force-a-vspackage-to-load"></a>Wymuszanie ładowania pakietu VSPackage
 W pewnych okolicznościach VSPackage może być konieczności wymuszenia innego VSPackage do załadowania. Na przykład lekki VSPackage może załadować większy VSPackage w kontekście, który nie jest dostępny jako CMDUIContext.

 Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metody, aby wymusić VSPackage załadować.

- Wstaw ten <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> kod do metody VSPackage, która wymusza ładowanie innego vspackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Po zainicjowaniu VSPackage, wymusi `PackageToBeLoaded` załadować.

     Wymuszanie ładowania nie powinny być używane do komunikacji VSPackage. Zamiast tego [użyj i dziel usługi.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
