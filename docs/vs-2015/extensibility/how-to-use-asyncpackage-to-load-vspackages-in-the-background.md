---
title: 'Porady: używanie klasy AsyncPackage do ładowania pakietów VSPackages w tle | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: d5bc0c22ff0a29984e59c30db6dc2b391bf007e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778790"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Porady: używanie klasy AsyncPackage do ładowania pakietów VSPackages w tle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ładowanie i Inicjowanie pakietu programu VS może spowodować We/Wy dysku. W przypadku takich operacji We/Wy na wątek interfejsu użytkownika, może to prowadzić do problemów z czasem odpowiedzi. Aby rozwiązać ten problem, Visual Studio 2015 wprowadzono <xref:Microsoft.VisualStudio.Shell.AsyncPackage> klasy, który umożliwia ładowanie pakiet w wątku tła.  
  
## <a name="creating-an-asyncpackage"></a>Tworzenie AsyncPackage  
 Możesz zacząć od utworzenia projektu VSIX (**plik / nowy / Project / Visual C# / rozszerzalności / projekt VSIX**) i dodawanie pakietu VSPackage do projektu (kliknij prawym przyciskiem myszy projekt i **elementu Dodawanie/New / C# elementu/rozszerzalność/Visual Pakiet Studio**). Można utworzyć usługi i dodawanie tych usług do pakietu.  
  
1. Pochodzi pakiet z <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2. Jeśli udostępniasz usług, których wykonywanie kwerend może spowodować, że można załadować pakietu:  
  
    Aby wskazać w programie Visual Studio, czy pakiet jest bezpieczny dla tła ładowania oraz zdecydować się na to zachowanie usługi <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> należy ustawić **AllowsBackgroundLoading** właściwości na wartość true w Konstruktorze atrybutu.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Aby wskazać w programie Visual Studio, bezpiecznego do utworzenia wystąpienia usługi w wątku w tle, należy ustawić <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> właściwości na wartość true w <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> konstruktora.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. Jeśli są ładowane za pośrednictwem interfejsu użytkownika kontekstów, a następnie należy określić **PackageAutoLoadFlags.BackgroundLoad** dla <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> lub wartość (0x2) do flag zapisywane jako wartość wpisu automatycznie załadować do pakietu.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. W przypadku inicjowania asynchroniczne zadania do wykonania należy zastąpić <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Usuń **Initialize()** metody dostarczone przez szablon VSIX. ( **Initialize()** method in Class metoda **AsyncPackage** jest zapieczętowany). Można użyć dowolnego z <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metod dodawania asynchronicznych usług do pakietu.  
  
    Uwaga: Aby wywołać **podstawowej. InitializeAsync()**, można zmienić kod źródłowy, aby:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. Możesz należy uważać, aby nie wprowadzać RPC (Usuń wywoływanie procedur) w kodzie inicjowania asynchroniczne (w **InitializeAsync**). One może wystąpić, gdy wywołujesz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> bezpośrednio lub pośrednio.  Podczas ładowania synchronizacji są wymagane, wątek interfejsu użytkownika zostanie zablokowane, używając <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Domyślny model blokowania wyłącza RPC. Oznacza to, że Jeśli spróbujesz użyć wywołania RPC ze swojej zadań asynchronicznych, będzie zakleszczenie wtedy wątku interfejsu użytkownika jest oczekiwanie pakietu do załadowania. Ogólne alternatywą jest do organizowania kodu do wątku interfejsu użytkownika, jeśli to konieczne, przy użyciu polecenia podobnego **sprzęganiu fabryki zadań**firmy <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> lub inny mechanizm, który nie korzysta z usługi RPC.  Nie używaj **ThreadHelper.Generic.Invoke** lub ogólnie blokuje wątek wywołujący, oczekiwanie na wątek interfejsu użytkownika.  
  
    Uwaga: Należy unikać używania **GetService** lub **QueryService** w swojej **InitializeAsync** metody. Jeśli masz ich użyć, należy najpierw przełącz do wątku interfejsu użytkownika. Alternatywą jest użycie <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> z Twojej **AsyncPackage** (przez rzutowanie jego <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
   C#: Tworzenie AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konwertowanie istniejącego pakietu VSPackage na AsyncPackage  
 Większość pracy jest taka sama, jak podczas tworzenia nowego **AsyncPackage**. Należy wykonać kroki od 1 do 5 powyżej. Należy również wykonać wyjątkową ostrożność od następujących czynników:  
  
1.  Pamiętaj, aby usunąć **zainicjować** zastąpienie miał w pakiecie.  
  
2.  Należy unikać zakleszczenia: może być ukryta zdalnych wywołań procedury w kodzie, który teraz powinny być wykonywane dla wątku w tle. Należy upewnić się, że jeśli wykonujesz zdalnego wywołania procedury (np. **GetService**), musisz albo (1) Przełącz do wątku głównego, lub (2) Użyj asynchroniczną wersję interfejsu API, jeśli taki istnieje (np. **element GetServiceAsync**).  
  
3.  Nie Przełączaj pomiędzy wątkami zbyt często. Spróbuj zlokalizować pracy, która może nastąpić w wątku w tle. Powoduje to skrócenie czasu ładowania.  
  
## <a name="querying-services-from-asyncpackage"></a>Podczas badania usługi AsyncPackage  
 **AsyncPackage** może lub nie może załadować asynchronicznie w zależności od obiektu wywołującego. Na przykład  
  
- Jeśli element wywołujący o nazwie **GetService** lub **QueryService** (zarówno synchronicznych interfejsów API) lub  
  
- Jeśli element wywołujący o nazwie **IVsShell::LoadPackage** (lub **IVsShell5::LoadPackageWithContext**) lub  
  
- Obciążenie jest wyzwalany przez kontekstu interfejsu użytkownika, ale nie określono, że mogą być można ładować asynchronicznie w mechanizm kontekstu interfejsu użytkownika  
  
  następnie pakietu zostanie załadowany synchronicznie.  
  
  Należy zauważyć, że pakietu nadal ma szansy sprzedaży (w fazie asynchronicznego inicjowania) do pracy Wyłącz wątku interfejsu użytkownika do wątku interfejsu użytkownika zostanie zablokowane na ukończenie tej pracy. Jeśli obiekt wywołujący używa **IAsyncServiceProvider** asynchronicznie zapytania dla Twojej usługi, następnie obciążenia i inicjowania zostanie wykonane asynchronicznie zakładając, że nie są natychmiast zablokować w obiekcie wynikowym zadania.  
  
  C#: Jak asynchronicznie zapytań usługi:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

