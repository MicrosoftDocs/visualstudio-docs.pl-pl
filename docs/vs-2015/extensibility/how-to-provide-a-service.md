---
title: 'Porady: udostępnianie usługi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e0d0425e0e931d28157439d3d8a4174f1d4961a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785914"
---
# <a name="how-to-provide-a-service"></a>Porady: świadczenia usług
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietu VSPackage oferuje usługi, które można użyć innych pakietów VSPackage. Do świadczenia usług, pakietu VSPackage należy zarejestrować usługę za pomocą programu Visual Studio, a następnie Dodaj usługę.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasa implementuje interfejsy <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> zawiera metody wywołania zwrotnego, które zapewniają usługi na żądanie.  
  
 Aby uzyskać więcej informacji na temat usług, zobacz [podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Gdy pakietu VSPackage ma zostać zwolniony, Visual Studio czeka, aż wszystkie żądania dotyczące usług, które zapewnia pakietu VSPackage zostały dostarczone. Nie zezwalaj na nowe żądania dla tych usług. Nie należy jawnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody, aby można było odwołać usługi podczas zwalniania.  
  
#### <a name="implementing-a-service"></a>Wdrażanie usługi  
  
1. Utwórz projekt VSIX (**plik / nowy / Project / Visual C# / Extensiblity / projekt VSIX**).  
  
2. Dodanie pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Add / nowy element / elementy Visual C# / rozszerzalność / pakiet rozszerzeń Visual Studio**.  
  
3. Aby wdrożyć usługi, musisz utworzyć trzy typy:  
  
   - Interfejs, który zawiera opis usługi. Wiele z tych interfejsów są puste, oznacza to, ponieważ mają one żadnych metod.  
  
   - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.  
  
   - Klasa, która implementuje interfejs usługi i usługi.  
  
     Poniższy przykład przedstawia bardzo podstawową implementację z trzech typów. Konstruktor klasy usługi należy ustawić dostawcę usług.  
  
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
  
### <a name="registering-a-service"></a>Rejestrowanie usługi  
  
1.  Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu VSPackage, która dostarcza usługę. Oto przykład:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Ten atrybut rejestruje `SMyService` z programem Visual Studio.  
  
    > [!NOTE]
    >  Aby zarejestrować to usługa, która zastępuje inną usługę o takiej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Uwaga dozwolony jest tylko jeden zastąpienie usługi.  
  
### <a name="adding-a-service"></a>Dodawanie usług telefonii  
  
1.  1.  W inicjatorze pakietu VSPackage Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego, trzeba utworzyć usługi. Oto zmiany do wprowadzenia <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementuje metody wywołania zwrotnego, które należy utworzyć i zwracać usługi lub wartość null, jeśli nie można utworzyć.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Program Visual Studio można odrzucić żądanie do świadczenia usług. Robi to jeśli innego pakietu VSPackage już zawiera usługę.  
  
3.  Teraz możesz pobrać usługę i użycie jej metod. Pokazano to w inicjatorze, ale możesz uzyskać odpowiednią usługę dowolne miejsce do korzystania z usługi.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Wartość `helloString` powinien być "Hello".  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)   
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)

