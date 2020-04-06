---
title: 'Jak: Świadczenie usług | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710773"
---
# <a name="how-to-provide-a-service"></a>Jak: Świadczenie usług
A VSPackage może świadczyć usługi, które inne pakiety VSPackages można użyć. Aby zapewnić usługę, VSPackage musi zarejestrować usługę w programie Visual Studio i dodać usługę.

 Klasa <xref:Microsoft.VisualStudio.Shell.Package> implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> zarówno <xref:System.ComponentModel.Design.IServiceContainer>i . <xref:System.ComponentModel.Design.IServiceContainer>zawiera metody wywołania zwrotnego, które świadczą usługi na żądanie.

 Aby uzyskać więcej informacji o usługach, zobacz [Podstawowe usługi](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Gdy VSPackage ma zostać zwolniony, Visual Studio czeka, aż wszystkie żądania dla usług, które zapewnia VSPackage zostały dostarczone. Nie zezwala na nowe żądania dla tych usług. Nie należy jawnie <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> wywołać metodę, aby odwołać usługę podczas zwalniania.

## <a name="implement-a-service"></a>Implementowanie usługi

1. Tworzenie projektu VSIX (**Plik** > **nowy** > **projekt** > **Visual C#** > **Rozszerzalność** > **VSIX Project**).

2. Dodaj VSPackage do projektu. Wybierz węzeł projektu w **Eksploratorze rozwiązań** i kliknij pozycję **Dodaj** > **nowy element** > **Visual C# Element** > **Rozszerzalność** > **pakietu programu Visual Studio**.

3. Aby zaimplementować usługę, należy utworzyć trzy typy:

   - Interfejs, który opisuje usługę. Wiele z tych interfejsów są puste, oznacza to, że nie mają żadnych metod.

   - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody, które mają być zaimplementowane.

   - Klasa, która implementuje zarówno usługi i interfejsu usługi.

     W poniższym przykładzie przedstawiono podstawową implementację trzech typów. Konstruktor klasy usługi musi ustawić dostawcę usług.

   ```csharp
   public class MyService : SMyService, IMyService
   {
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;
       private string myString;
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)
       {
           Trace.WriteLine(
                  "Constructing a new instance of MyService");
           serviceProvider = sp;
       }
       public void Hello()
       {
           myString = "hello";
       }
       public string Goodbye()
       {
          return "goodbye";
       }
   }
   public interface SMyService
   {
   }
   public interface IMyService
   {
       void Hello();
       string Goodbye();
   }

   ```

### <a name="register-a-service"></a>Zarejestruj usługę

1. Aby zarejestrować usługę, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> dodaj do VSPackage, który udostępnia usługę. Oto przykład:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Ten atrybut rejestruje `SMyService` się w programie Visual Studio.

    > [!NOTE]
    > Aby zarejestrować usługę, która zastępuje inną usługę <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>o tej samej nazwie, użyj pliku . Należy zauważyć, że dozwolone jest tylko jedno zastąpienie usługi.

### <a name="add-a-service"></a>Dodawanie usługi

1. W vspackage inicjatora, dodaj usługę i dodać metodę wywołania zwrotnego, aby utworzyć usługi. Oto zmiana, aby wprowadzić <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> do metody:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Zaimplementuj metodę wywołania zwrotnego, która powinna utworzyć i zwrócić usługę lub null, jeśli nie można jej utworzyć.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio można odrzucić żądanie świadczenia usługi. Robi to, jeśli inny VSPackage już zapewnia usługę.

3. Teraz możesz uzyskać usługę i korzystać z jej metod. Poniższy przykład pokazuje przy użyciu usługi w inicjatorze, ale można uzyskać usługę w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     Wartość `helloString` powinna być "Hello".

## <a name="see-also"></a>Zobacz też
- [Jak: Uzyskaj usługę](../extensibility/how-to-get-a-service.md)
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
- [Podstawowe usługi](../extensibility/internals/service-essentials.md)
