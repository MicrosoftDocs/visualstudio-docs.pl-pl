---
title: 'Instrukcje: dostarczanie usługi | Microsoft Docs'
description: Pakietu VSPackage może zapewnić usługi, których mogą używać inne pakietów VSPackage. Dowiedz się, w jaki sposób pakietu VSPackage rejestruje usługę w programie Visual Studio i dodaje ją do usługi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f16e05ecbd211652dbf5fb511211627a09137df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952268"
---
# <a name="how-to-provide-a-service"></a>Instrukcje: dostarczanie usługi
Pakietu VSPackage może zapewnić usługi, których mogą używać inne pakietów VSPackage. Aby zapewnić usługę, pakietu VSPackage musi zarejestrować usługę w programie Visual Studio i dodać usługę.

 <xref:Microsoft.VisualStudio.Shell.Package>Klasa implementuje obie <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> zawiera metody wywołania zwrotnego, które udostępniają usługi na żądanie.

 Aby uzyskać więcej informacji na temat usług, zobacz temat [Service Essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Gdy pakietu VSPackage zostanie zwolniony, program Visual Studio czeka, aż zostaną dostarczone wszystkie żądania usług, które udostępnia pakietu VSPackage. Nie zezwala na nowe żądania dla tych usług. Nie należy jawnie wywoływać <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody do odwoływania usługi podczas jej zwalniania.

## <a name="implement-a-service"></a>Implementowanie usługi

1. Utwórz projekt VSIX (**plik**  >  **New**  >  **Project**  >  **Visual C#**  >  **Rozszerzalny**  >  **Projekt VSIX**).

2. Dodaj pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań** a następnie kliknij pozycję **Dodaj**  >  **nowy element**  >  **Visual C# elementy**  >  **Rozszerzalny**  >  **pakiet Visual Studio**.

3. Aby zaimplementować usługę, należy utworzyć trzy typy:

   - Interfejs, który opisuje usługę. Wiele z tych interfejsów jest pustych, czyli nie ma metod.

   - Interfejs opisujący interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

   - Klasa implementująca zarówno usługę, jak i interfejs usługi.

     Poniższy przykład pokazuje podstawową implementację trzech typów. Konstruktor klasy usługi musi ustawić dostawcę usług.

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

### <a name="register-a-service"></a>Rejestrowanie usługi

1. Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do usługi pakietu VSPackage, która udostępnia usługę. Oto przykład:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Ten atrybut rejestruje `SMyService` w programie Visual Studio.

    > [!NOTE]
    > Aby zarejestrować usługę, która zastępuje inną usługę o tej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Należy zauważyć, że dozwolone jest tylko jedno zastąpienie usługi.

### <a name="add-a-service"></a>Dodawanie usługi

1. W inicjatorze pakietu VSPackage Dodaj usługę i Dodaj metodę wywołania zwrotnego, aby utworzyć usługi. Oto zmiana do wprowadzenia do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Zaimplementuj metodę wywołania zwrotnego, która powinna utworzyć i zwrócić usługę, lub wartość null, jeśli nie można jej utworzyć.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Program Visual Studio może odrzucić żądanie dostarczenia usługi. Jest to możliwe, jeśli inny pakietu VSPackage już udostępnia usługę.

3. Teraz możesz uzyskać usługę i użyć jej metod. W poniższym przykładzie pokazano użycie usługi w inicjatorze, ale możesz uzyskać usługę w dowolnym miejscu, w którym chcesz korzystać z usługi.

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

     Wartość `helloString` powinna być równa "Hello".

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)
- [Używanie i udostępnianie usług](../extensibility/using-and-providing-services.md)
- [Podstawowa usługa](../extensibility/internals/service-essentials.md)
