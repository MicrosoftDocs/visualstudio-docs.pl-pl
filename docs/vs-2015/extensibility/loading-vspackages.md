---
title: Ładowanie pakietów VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802266"
---
# <a name="loading-vspackages"></a>Ładowanie pakietów VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage są ładowane do programu Visual Studio tylko wtedy, gdy ich funkcjonalność jest wymagana. Na przykład pakietu VSPackage jest ładowany, gdy program Visual Studio używa fabryki projektu lub usługi implementującej implementację pakietu VSPackage. Ta funkcja jest nazywana opóźnionym ładowaniem, które jest używane w miarę możliwości w celu zwiększenia wydajności.  
  
> [!NOTE]
> Program Visual Studio może określić pewne informacje pakietu VSPackage, takie jak polecenia oferowane przez pakietu VSPackage, bez ładowania pakietu VSPackage.  
  
 Pakietów VSPackage można ustawić na automatyczne ładowanie w kontekście określonego interfejsu użytkownika, na przykład po otwarciu rozwiązania. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Atrybut ustawia ten kontekst.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Automatyczne ładowanie elementu pakietu VSPackage w określonym kontekście  
  
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
  
## <a name="forcing-a-vspackage-to-load"></a>Wymuszanie załadowania pakietu VSPackage  
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
  
     Wymuś ładowanie nie należy używać do komunikacji pakietu VSPackage. Zamiast tego użyj [usługi i usług](../extensibility/using-and-providing-services.md) .  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Używanie atrybutu niestandardowego do rejestrowania pakietu VSPackage  
 W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Możesz użyć atrybutów rejestracji, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi być pochodną <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> i musi zastąpić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody i.  
  
## <a name="creating-a-registry-key"></a>Tworzenie klucza rejestru  
 W poniższym kodzie atrybut niestandardowy tworzy **niestandardowy** podklucz w kluczu dla pakietu VSPackage, który jest rejestrowany.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości w istniejącym kluczu rejestru  
 Możesz dodać wartości niestandardowe do istniejącego klucza. Poniższy kod pokazuje, jak dodać nową wartość do klucza rejestracji pakietu VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
