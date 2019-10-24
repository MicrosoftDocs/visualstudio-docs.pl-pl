---
title: Używanie zestawów międzyoperacyjnych programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722099"
---
# <a name="using-visual-studio-interop-assemblies"></a>Korzystanie z zestawów międzyoperacyjnych programu Visual Studio
Zestawy międzyoperacyjne programu Visual Studio umożliwiają zarządzanym aplikacjom dostęp do interfejsów COM, które udostępniają rozszerzalność programu Visual Studio. Istnieją pewne różnice między prostymi interfejsami COM i ich wersjami międzyoperacyjnymi. Na przykład HRESULTs są zwykle reprezentowane jako wartości int i muszą być obsługiwane w taki sam sposób jak wyjątki, a parametry (zwłaszcza parametry out) są traktowane inaczej.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa HRESULT zwróconych do kodu zarządzanego z modelu COM
 Gdy wywoływany jest interfejs COM z kodu zarządzanego, należy przeanalizować wartość HRESULT i zgłosić wyjątek, jeśli jest to wymagane. Klasa <xref:Microsoft.VisualStudio.ErrorHandler> zawiera metodę <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, która zgłasza wyjątek COM w zależności od wartości przenoszonego do niego wyniku.

 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przenoszona wynik HRESULT o wartości mniejszej od zera. W przypadkach, gdy takie HRESULT są akceptowalnymi wartościami i żaden wyjątek nie powinien być zgłaszany, wartości dodatkowych HRESULT powinny być przesyłane do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po przetestowaniu wartości. Jeśli wartość HRESULT jest testowana dopasowuje wszystkie wartości HRESULT jawnie przekazaną do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, żaden wyjątek nie jest zgłaszany.

> [!NOTE]
> Klasa <xref:Microsoft.VisualStudio.VSConstants> zawiera stałe dla typowych wartości HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> i <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> oraz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> udostępnia również metody <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, które odpowiadają makrom zakończonym powodzeniem i niepomyślnym w modelu COM.

 Rozważmy na przykład następujące wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest akceptowalną wartością zwracaną, ale wszystkie inne HRESULT, które są mniejsze od zera, reprezentują błąd.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Jeśli istnieje więcej niż jedna akceptowalna wartość zwracana, do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> można dołączyć dodatkowe wartości HRESULT.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wartości HRESULT do modelu COM z kodu zarządzanego
 Jeśli żaden wyjątek nie wystąpi, kod zarządzany zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkcji COM, która go wywołała. Międzyoperacyjność modelu COM obsługuje typowe wyjątki, które są jednoznacznie wpisane w kodzie zarządzanym. Na przykład metoda, która otrzymuje nieakceptowalny `null` argument zgłasza <xref:System.ArgumentNullException>.

 Jeśli nie masz pewności, który wyjątek zgłosić, ale znasz wartość HRESULT, która ma zostać zwrócona do modelu COM, możesz użyć metody <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>, aby zgłosić odpowiedni wyjątek. Działa to nawet z niestandardowym błędem, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zamapować przekazaną do niego wynik HRESULT na wyjątek o jednoznacznie określonym typie. Jeśli nie jest to możliwe, zgłasza zamiast niego ogólny wyjątek modelu COM. Ostateczny wynik polega na tym, że wartość HRESULT, którą przekazujesz do <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego jest zwracana do funkcji COM, która ją wywołała.

> [!NOTE]
> Wyjątki naruszają wydajność i mają na celu wskazywanie nietypowych warunków programu. Warunki, które często występują, powinny być obsługiwane wewnętrznie, zamiast zgłoszonego wyjątku.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown przesłane jako void * *
 Poszukaj parametrów [out], które są zdefiniowane jako typ `void **` w interfejsie COM, ale które są zdefiniowane jako `[``iid_is``]` w prototypie metody zestawu międzyoperacyjnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Czasami interfejs COM generuje obiekt `IUnknown`, a interfejs COM przekazuje go jako typ `void **`. Te interfejsy są szczególnie ważne, ponieważ jeśli zmienna jest zdefiniowana jako [out] w IDL, wówczas obiekt `IUnknown` jest liczony jako odwołanie z metodą `AddRef`. Przeciek pamięci występuje, jeśli obiekt nie został poprawnie obsłużony.

> [!NOTE]
> Obiekt `IUnknown` utworzony przez interfejs COM i zwrócony w zmiennej [out] powoduje przeciek pamięci, jeśli nie został jawnie wydaną.

 Zarządzane metody obsługujące takie obiekty powinny traktować <xref:System.IntPtr> jako wskaźnik do obiektu `IUnknown` i wywoływać metodę <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> w celu uzyskania obiektu. Obiekt wywołujący powinien następnie rzutować wartość zwracaną na dowolny typ jest odpowiedni. Gdy obiekt nie jest już wymagany, wywołaj <xref:System.Runtime.InteropServices.Marshal.Release%2A>, aby go zwolnić.

 Poniżej znajduje się przykład wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> i prawidłowo obsługującej obiekt `IUnknown`:

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
> Następujące metody są znane, aby przekazywać `IUnknown` wskaźników obiektów jako <xref:System.IntPtr> typu. Obsłuż je zgodnie z opisem w tej sekcji.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Opcjonalne parametry [out]
 Poszukaj parametrów, które są zdefiniowane jako typ danych [out] (`int`, `object` itd.) w interfejsie COM, ale które są zdefiniowane jako tablice tego samego typu danych w prototypie metody zestawu międzyoperacyjnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Niektóre interfejsy COM, takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, traktują parametry [out] jako opcjonalne. Jeśli obiekt nie jest wymagany, te interfejsy COM zwracają `null` wskaźnik jako wartość tego parametru, zamiast tworzyć obiekt [out]. Jest to zaprojektowane. Dla tych interfejsów `null` wskaźniki są zakładane jako część prawidłowego zachowania pakietu VSPackage i nie jest zwracany żaden błąd.

 Ponieważ środowisko CLR nie zezwala na `null` wartość parametru [out], część zaprojektowanego zachowania tych interfejsów nie jest bezpośrednio dostępna w kodzie zarządzanym. Metody zestawu międzyoperacyjności [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla interfejsów, których dotyczy problem, umożliwiają obejście problemu przez zdefiniowanie odpowiednich parametrów jako tablic, ponieważ środowisko CLR umożliwia przekazywanie tablic `null`owych.

 Zarządzane implementacje tych metod powinny umieścić tablicę `null` do parametru, gdy nie ma niczego do zwrócenia. W przeciwnym razie Utwórz tablicę z jednym elementem o poprawnym typie i umieść wartość zwracaną w tablicy.

 Metody zarządzane, które odbierają informacje z interfejsów z opcjonalnymi parametrami [out], otrzymują parametr jako tablicę. Po prostu Przeanalizuj wartość pierwszego elementu tablicy. Jeśli nie jest `null`, Traktuj pierwszy element tak, jakby był oryginalnym parametrem.

## <a name="passing-constants-in-pointer-parameters"></a>Przekazywanie stałych w parametrach wskaźnika
 Poszukaj parametrów, które są zdefiniowane jako wskaźniki [in] w interfejsie COM, ale które są zdefiniowane jako typ <xref:System.IntPtr> w prototypie metody zestawu międzyoperacyjnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Podobny problem występuje, gdy interfejs COM przekazuje specjalną wartość, taką jak 0,-1 lub-2, zamiast wskaźnika obiektu. W przeciwieństwie do [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], środowisko CLR nie zezwala na rzutowanie stałych jako obiektów. Zamiast tego zestaw międzyoperacyjny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definiuje parametr jako typ <xref:System.IntPtr>.

 Zarządzane implementacje tych metod powinny korzystać z faktu, że Klasa <xref:System.IntPtr> ma zarówno konstruktory `int`, jak i `void *`, aby utworzyć <xref:System.IntPtr> z obiektu lub stałej całkowitej, zgodnie z potrzebami.

 Metody zarządzane, które odbierają parametry <xref:System.IntPtr> tego typu, powinny używać operatorów konwersji typu <xref:System.IntPtr> do obsługi wyników. Najpierw przekonwertuj <xref:System.IntPtr>, aby `int` i przetestować je względem odpowiednich stałych liczb całkowitych. Jeśli wartości nie są zgodne, przekonwertuj je na obiekt typu wymaganego i Kontynuuj.

 Aby zapoznać się z przykładami, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>Wartości zwracane przez OLE zostały przesłane jako parametry [out]
 Wyszukaj metody, które mają `retval` wartość zwracaną w interfejsie COM, ale które mają `int` wartość zwracaną oraz dodatkowy parametr tablicy [out] w prototypie metody zestawu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] międzyoperacyjnego. Powinno być jasne, że te metody wymagają specjalnej obsługi, ponieważ prototypy metod zestawu międzyoperacyjnego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mają jeden parametr niż metody interfejsu COM.

 Wiele interfejsów COM, które zajmują się działaniem OLE, wysyła informacje o stanie OLE z powrotem do wywołującego programu przechowywanego w `retval` wartości zwracanej przez interfejs. Zamiast korzystać z wartości zwracanej, odpowiednie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody zestawu międzyoperacyjnego wysyłają informacje z powrotem do programu wywołującego przechowywanego w parametrze tablicy [out].

 Zarządzane implementacje tych metod powinny tworzyć jednoelementową tablicę tego samego typu co parametr [out] i umieścić ją w parametrze. Wartość elementu Array powinna być taka sama jak odpowiednia `retval` COM.

 Metody zarządzane, które wywołują interfejsy tego typu, powinny pobierać pierwszy element z tablicy [out]. Ten element może być traktowany tak, jakby był `retval` wartością zwracaną z odpowiedniego interfejsu COM.

## <a name="see-also"></a>Zobacz także
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)