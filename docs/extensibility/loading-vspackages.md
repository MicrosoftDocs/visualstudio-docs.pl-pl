---
title: Ładowanie pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce0f09c1749621838729e1e4f64feb3ca8b07628
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117567"
---
# <a name="load-vspackages"></a>Ładowanie pakietów VSPackage
Pakietów VSPackage są ładowane do programu Visual Studio, tylko wtedy, gdy ich funkcjonalność jest wymagana. Na przykład pakietu VSPackage jest ładowany, gdy program Visual Studio używa w fabryce projektu lub usługi, która implementuje pakietu VSPackage. Ta funkcja jest nazywana opóźnionego ładowania, która jest używana zawsze, gdy jest to możliwe zwiększyć wydajność.

> [!NOTE]
>  Program Visual Studio można określić pewne informacje pakietu VSPackage, takich jak polecenia, które oferuje pakietu VSPackage, bez załadowania pakietu VSPackage.

 Pakietów VSPackage można ustawić na automatyczne ładowanie w kontekście interfejsu użytkownika, na przykład, gdy rozwiązanie jest otwarte. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Atrybut ustawia w tym kontekście.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Załaduj VSPackage w określonym kontekście

- Dodaj `ProvideAutoLoad` atrybutu atrybutów pakietu VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Zobacz wyliczany pola <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> lista kontekstów interfejsu użytkownika i ich wartości identyfikatora GUID.

- Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

- Tworzenie pakietu VSPackage, a następnie rozpocząć debugowanie.

- Załaduj rozwiązanie lub utworzyć nowe.

     Pakietu VSPackage ładuje i zatrzymuje się w punkcie przerwania.

## <a name="force-a-vspackage-to-load"></a>Wymuś można załadować pakietu VSPackage
 W pewnych okolicznościach pakietu VSPackage może zajść potrzeba wymuszenia innego pakietu VSPackage do załadowania. Na przykład lekki pakietu VSPackage może ładować większych pakietu VSPackage w kontekście, który nie jest dostępna jako CMDUIContext.

 Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodę wymuszania można załadować pakietu VSPackage.

- Wstaw ten kod do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metoda pakietu VSPackage, który wymusza innego pakietu VSPackage załadować:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Po zainicjowaniu pakietu VSPackage wymusi `PackageToBeLoaded` do załadowania.

     Ładowanie życie nie należy używać do komunikacji pakietu VSPackage. Użyj [użycia i świadczenia usług](../extensibility/using-and-providing-services.md) zamiast tego.

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
