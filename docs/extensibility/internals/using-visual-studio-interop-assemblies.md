---
title: Przy użyciu zestawów międzyoperacyjnych programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f083e97427b44256ac565e2fc6822586825aef4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061947"
---
# <a name="using-visual-studio-interop-assemblies"></a>Korzystanie z zestawów międzyoperacyjnych programu Visual Studio
Visual Studio, zestawy międzyoperacyjne Zezwalaj na dostęp do interfejsów COM, które przewiduje rozszerzalności programu Visual Studio zarządzanych aplikacji. Istnieją pewne różnice między proste interfejsy COM i ich wersje międzyoperacyjnego. Na przykład wartości HRESULT zazwyczaj są reprezentowane jako wartości int i muszą być obsługiwani w taki sam sposób jak wyjątki i parametry (szczególnie parametrów out) są traktowane inaczej.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa wartości HRESULT zwracane do kodu zarządzanego z modelu COM
 Po wywołaniu interfejsu COM z kodu zarządzanego, sprawdź wartość HRESULT, aby zgłosić wyjątek, jeśli jest to wymagane. <xref:Microsoft.VisualStudio.ErrorHandler> Klasa zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> przekazany metody, która zgłasza wyjątek modelu COM., w zależności od wartości HRESULT.

 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przekazywana wartość HRESULT, która ma wartość niższą niż zero. W przypadkach, takich wartości HRESULT są dopuszczalne wartości i nie należy zgłosić wyjątek, wartości dodatkowe wartości HRESULT powinien zostać przekazany do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po wartości są badane. Jeśli HRESULT testowana pasuje do dowolnej wartości HRESULT jawnie przekazany do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, jest zgłaszany żaden wyjątek.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Klasa zawiera stałe dla typowych wartości HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> i <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wartości HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> udostępnia również <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metod, które odnoszą się do makra Powodzenie, a nie powiodło się w modelu COM.

 Na przykład, należy wziąć pod uwagę poniższe wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest mniejsza niż zero reprezentuje błąd akceptowalną wartość zwracana, ale inne HRESULT.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Jeśli istnieje więcej niż jeden dopuszczalne wartości zwracane, dodatkowe wartości HRESULT tylko można dołączyć do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wartości HRESULT dla modelu COM z kodu zarządzanego
 Jeśli nie wystąpi wyjątek, zarządzany kod zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkcji COM, która nazwała go. Usługa międzyoperacyjna modelu COM obsługuje powszechne wyjątki, które są silnie typizowane w kodzie zarządzanym. Na przykład, metody, która odbiera niedopuszczalne `null` zgłasza argument <xref:System.ArgumentNullException>.

 Jeśli nie jesteś niektórych który wyjątków zgłaszają, ale wiesz HRESULT chcesz wrócić do modelu COM, można użyć <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodę, aby zgłosić wyjątek odpowiednie. Dzieje się tak nawet w przypadku błędów niestandardowych, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zamapować HRESULT przekazany do silnie typizowanego wyjątku. Jeśli jest ona nieosiągalna, zgłosi wyjątek ogólny COM zamiast tego. Ostateczny wynik jest HRESULT, były przekazywane do <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego jest zwracany do funkcji COM, która nazwała go.

> [!NOTE]
>  Wyjątki wpłynąć na wydajność i są przeznaczone do wskazania niewłaściwym warunków. Warunki, które często występują powinny być obsługiwane w tekście, a nie zgłoszony wyjątek.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametry przekazywane jako typ void **
 Wyszukaj [out] Parametry, które są zdefiniowane jako typ `void **` w COM interfejs, ale są definiowane jako `[``iid_is``]` w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego metody prototypu.

 Czasami generuje interfejsu COM `IUnknown` obiektu i interfejsu COM następnie przekazuje ją jako typ `void **`. Te interfejsy są szczególnie ważne, ponieważ jeśli zmienna jest zdefiniowana jako [out] w pliku IDL, a następnie `IUnknown` obiekt jest zliczonych odwołań z `AddRef` metody. Jeśli obiekt nie jest obsługiwany poprawnie występuje przeciek pamięci.

> [!NOTE]
>  `IUnknown` Obiekt utworzony przy użyciu interfejsu COM i zwracane w zmiennej [out] powoduje przeciek pamięci, jeśli nie jest jawnie zwalniane.

 Zarządzanych metod, które obsługują takie obiekty powinny traktować <xref:System.IntPtr> jako wskaźnik do `IUnknown` obiektu, a następnie wywołaj <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metody do uzyskiwania obiektu. Obiekt wywołujący powinien następnie rzutowanie zwracanej wartości do dowolnego typu, jest odpowiednie. Gdy obiekt nie jest już potrzebny, wywołaj <xref:System.Runtime.InteropServices.Marshal.Release%2A> do jego zwolnienia.

 Poniżej znajduje się przykład wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metody i obsługa `IUnknown` obiektu prawidłowo:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
>  Wiadomo, że następujące metody przekazywania `IUnknown` obiektu wskaźników jako typ <xref:System.IntPtr>. Je obsłużyć zgodnie z opisem w tej sekcji.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Opcjonalne [parametry out]
 Wyszukaj parametry, które są zdefiniowane jako [out] — Typ danych (`int`, `object`i tak dalej) w COM interfejs, ale są definiowane jako tablice tego samego typu danych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego metody prototypu.

 Niektóre COM interfejsów, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, Traktuj [opcjonalne parametry out]. Jeśli obiekt nie jest wymagane, zwracają te interfejsy COM `null` wskaźnik jako wartość tego parametru, zamiast tworzyć [out] obiekt. To jest celowe. Dla tych interfejsów `null` wskaźniki będą traktowani jako część prawidłowe działanie pakietu VSPackage, a nie błąd jest zwracany.

 Ponieważ środowisko CLR nie zezwala na wartość parametru [out] jako `null`, część zaprojektowane zachowanie tych interfejsów nie jest dostępne bezpośrednio w kodzie zarządzanym. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Metod zestawu międzyoperacyjnego dla interfejsów, których to dotyczy obejść ten problem, definiując odpowiednich parametrów jak tablice, ponieważ środowisko CLR zezwala na przekazywanie `null` tablic.

 Należy umieścić zarządzanej implementacji tych metod `null` tablicę do parametru gdy nie ma nic do zwrócenia. W przeciwnym razie utwórz jeden elementowej tablicy poprawnego typu i umieścić wartości zwracanej w tablicy.

 Zarządzane metody, które otrzymywanie informacji z współpracuje z opcjonalne [out] Parametry pobierają parametr jako tablicę. Po prostu sprawdzić wartość pierwszego elementu tablicy. Jeśli nie jest `null`, Traktuj pierwszego elementu, tak jakby pierwotny parametr.

## <a name="passing-constants-in-pointer-parameters"></a>Stałe przekazywanie w parametrach wskaźnika
 Wyszukaj parametry, które są definiowane jako [in] wskaźniki w interfejsie COM, ale które są definiowane jako <xref:System.IntPtr> wpisać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego metody prototypu.

 Podobny problem występuje, gdy interfejs COM przekazuje wartość specjalne, np. 0, -1 lub -2, a nie wskaźnik do obiektu. W odróżnieniu od [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], środowisko CLR nie zezwala na stałe, można rzutować jako obiekty. Zamiast tego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego definiuje jako parametr <xref:System.IntPtr> typu.

 Zarządzanej implementacji metody te powinny korzystać z zalet fakt, <xref:System.IntPtr> klasa ma zarówno `int` i `void *` konstruktorów do tworzenia <xref:System.IntPtr> z obiektem lub stała liczba całkowita, w stosownych przypadkach.

 Zarządzane metody, które odbierają <xref:System.IntPtr> parametry tego typu należy używać <xref:System.IntPtr> wpisz operatory konwersji do obsługi wyników. Najpierw przekonwertuj <xref:System.IntPtr> do `int` i testujemy stałe całkowite istotne. Jeśli żadne wartości nie są zgodne, przekonwertuj go na obiekt typu wymagane i kontynuować.

 Przykłady tego, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE zwracają wartości przekazane jako [parametry out]
 Wyszukaj metody, które mają `retval` mają wartości zwracanej w interfejsu COM, ale `int` zwracać wartości i dodatkowy [parametr tablicy w out] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego metody prototypu. Powinno być jasne, że te metody wymagają specjalnej obsługi, ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego metoda prototypów ma jeden parametr więcej niż metody interfejsu COM.

 Wiele interfejsów COM, które zajmują się działanie OLE wysyłane informacje o stanie OLE program wywołujący przechowywane w `retval` zwracają wartość interfejs. Zamiast używania zwracanej wartości, odpowiedni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metod zestawu międzyoperacyjnego wysyłane informacje przechowywane w [out] program wywołujący tablicy parametrów.

 Zarządzane implementacji tych metod należy utworzyć jednoelementowa tablica tego samego typu co parametr [out] i umieścić go w parametrze. Wartość elementu tablicy, powinna być taka sama jak odpowiednie COM `retval`.

 Zarządzanych metod, które wywołują interfejsy tego typu należy ściągnąć pierwszego elementu poza [out] tablica. Ten element może być traktowana tak, jakby była `retval` zwracanie wartości z odpowiedniego interfejsu COM.

## <a name="see-also"></a>Zobacz też
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)