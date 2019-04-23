---
title: Ładowanie pakietów VSPackage | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6c9de9c90840c01b37b99d813fbf23b7c2be3eea
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066575"
---
# <a name="loading-vspackages"></a>Ładowanie pakietów VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage są ładowane do programu Visual Studio, tylko wtedy, gdy ich funkcjonalność jest wymagana. Na przykład pakietu VSPackage jest ładowany, gdy program Visual Studio używa w fabryce projektu lub usługi, która implementuje pakietu VSPackage. Ta funkcja jest nazywana opóźnionego ładowania, która jest używana zawsze, gdy jest to możliwe zwiększyć wydajność.  
  
> [!NOTE]
>  Program Visual Studio można określić pewne informacje pakietu VSPackage, takich jak polecenia, które oferuje pakietu VSPackage, bez załadowania pakietu VSPackage.  
  
 Pakietów VSPackage można ustawić na automatyczne ładowanie w kontekście interfejsu użytkownika, na przykład, gdy rozwiązanie jest otwarte. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Atrybut ustawia w tym kontekście.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Autoloading VSPackage w określonym kontekście  
  
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
  
## <a name="forcing-a-vspackage-to-load"></a>Wymuszanie można załadować pakietu VSPackage  
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
  
     Ładowanie życie nie należy używać do komunikacji pakietu VSPackage. Użyj [Using i dostarczanie usług](../extensibility/using-and-providing-services.md) zamiast tego.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Za pomocą atrybutu niestandardowego można zarejestrować pakietu VSPackage  
 W niektórych przypadkach może być konieczne utworzenie nowego atrybutu rejestracji dla rozszerzenia. Można użyć atrybutów rejestracji, aby dodać nowe klucze rejestru lub dodać nowe wartości do istniejących kluczy. Nowy atrybut musi pochodzić od klasy <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, i musi ono przesłonić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> i <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody.  
  
## <a name="creating-a-registry-key"></a>Tworzenie klucza rejestru  
 Poniższy kod powoduje utworzenie niestandardowego atrybutu **niestandardowe** podkluczy klucza dla pakietu VSPackage, który jest rejestrowany.  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości w ramach istniejącego klucza rejestru  
 Wartości niestandardowe można dodać do istniejącego klucza. Poniższy kod przedstawia sposób dodawania nowej wartości z kluczem rejestracji pakietu VSPackage.  
  
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
