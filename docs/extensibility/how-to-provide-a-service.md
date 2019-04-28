---
title: 'Instrukcje: Oferuje usługi | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be56d37ddcd1047e776df2652c7e874e260a806
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417099"
---
# <a name="how-to-provide-a-service"></a>Instrukcje: Oferuje usługi
Pakietu VSPackage oferuje usługi, które można użyć innych pakietów VSPackage. Do świadczenia usług, pakietu VSPackage należy zarejestrować usługę za pomocą programu Visual Studio, a następnie Dodaj usługę.

 <xref:Microsoft.VisualStudio.Shell.Package> Klasa implementuje interfejsy <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> zawiera metody wywołania zwrotnego, które zapewniają usługi na żądanie.

 Aby uzyskać więcej informacji na temat usług, zobacz [usługa essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Gdy pakietu VSPackage ma zostać zwolniony, Visual Studio czeka, aż wszystkie żądania dotyczące usług, które zapewnia pakietu VSPackage zostały dostarczone. Nie zezwalaj na nowe żądania dla tych usług. Nie należy jawnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody, aby można było odwołać usługi podczas zwalniania.

## <a name="implement-a-service"></a>Implementowanie usługi

1. Utwórz projekt VSIX (**pliku** > **New** > **projektu** > **Visual C#**  >  **Rozszerzalności** > **projekt VSIX**).

2. Dodanie pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj** > **nowy element** > **elementy Visual C#**  >  **Rozszerzalności** > **pakietu Visual Studio**.

3. Aby wdrożyć usługi, musisz utworzyć trzy typy:

   - Interfejs, który zawiera opis usługi. Wiele z tych interfejsów są puste, oznacza to, ponieważ mają one żadnych metod.

   - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

   - Klasa, która implementuje interfejs usługi i usługi.

     Poniższy przykład pokazuje podstawową implementację trzy typy. Konstruktor klasy usługi należy ustawić dostawcę usług.

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

1. Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu VSPackage, która dostarcza usługę. Oto przykład:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Ten atrybut rejestruje `SMyService` z programem Visual Studio.

    > [!NOTE]
    > Aby zarejestrować to usługa, która zastępuje inną usługę o takiej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Uwaga dozwolony jest tylko jeden zastąpienie usługi.

### <a name="add-a-service"></a>Dodaj usługę

1. W inicjatorze pakietu VSPackage Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego, trzeba utworzyć usługi. Oto zmiany do wprowadzenia <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implementuje metody wywołania zwrotnego, które należy utworzyć i zwracać usługi lub wartość null, jeśli nie można utworzyć.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Program Visual Studio można odrzucić żądanie do świadczenia usług. Robi to jeśli innego pakietu VSPackage już zawiera usługę.

3. Teraz możesz pobrać usługę i użycie jej metod. W poniższym przykładzie przy użyciu usługi w inicjatorze, ale możesz uzyskać odpowiednią usługę dowolne miejsce do korzystania z usługi.

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

     Wartość `helloString` powinien być "Hello".

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)
- [Użyj i świadczenia usług](../extensibility/using-and-providing-services.md)
- [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)
