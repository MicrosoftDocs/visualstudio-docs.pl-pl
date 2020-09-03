---
title: Używanie zestawów międzyoperacyjnych programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704131"
---
# <a name="using-visual-studio-interop-assemblies"></a>Korzystanie z zestawów międzyoperacyjnych programu Visual Studio
Zestawy międzyoperacyjne programu Visual Studio umożliwiają zarządzanym aplikacjom dostęp do interfejsów COM, które udostępniają rozszerzalność programu Visual Studio. Istnieją pewne różnice między prostymi interfejsami COM i ich wersjami międzyoperacyjnymi. Na przykład HRESULTs są zwykle reprezentowane jako wartości int i muszą być obsługiwane w taki sam sposób jak wyjątki, a parametry (zwłaszcza parametry out) są traktowane inaczej.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa HRESULT zwróconych do kodu zarządzanego z modelu COM
 Gdy wywoływany jest interfejs COM z kodu zarządzanego, należy przeanalizować wartość HRESULT i zgłosić wyjątek, jeśli jest to wymagane. <xref:Microsoft.VisualStudio.ErrorHandler>Klasa zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodę, która ZGŁASZA wyjątek com, w zależności od wartości przenoszonego do niego wyniku.

 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przenoszona wynik HRESULT o wartości mniejszej od zera. W przypadkach, gdy takie HRESULT są akceptowalnymi wartościami i żaden wyjątek nie powinien być zgłaszany, wartości dodatkowych HRESULT powinny być przesyłane do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po przetestowaniu wartości. Jeśli wartość HRESULT jest testowana dopasowuje wszystkie wartości HRESULT jawnie przekazaną do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , żaden wyjątek nie jest zgłaszany.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>Klasa zawiera stałe dla wspólnych wartości HRESULT, na przykład i <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> udostępnia również <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> metody i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> , które odpowiadają MAKROm zakończonym powodzeniem i niepowodzeniem w modelu com.

 Rozważmy na przykład następujące wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest akceptowalną wartością zwracaną, ale wszystkie inne HRESULT, które są mniejsze od zera, reprezentują błąd.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Jeśli istnieje więcej niż jedna akceptowalna wartość zwracana, dodatkowe wartości HRESULT mogą wystarczy dołączyć do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wartości HRESULT do modelu COM z kodu zarządzanego
 Jeśli żaden wyjątek nie wystąpi, kod zarządzany zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkcji com, która go wywołała. Międzyoperacyjność modelu COM obsługuje typowe wyjątki, które są jednoznacznie wpisane w kodzie zarządzanym. Na przykład metoda, która odbiera nieakceptowalny `null` argument zgłasza <xref:System.ArgumentNullException> .

 Jeśli nie masz pewności, który wyjątek zgłosić, ale znasz wartość HRESULT, która ma zostać zwrócona do modelu COM, możesz użyć <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metody, aby zgłosić odpowiedni wyjątek. Działa to nawet z niestandardowym błędem, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zmapować przekazaną do niego wynik HRESULT na wyjątek silnie określony. Jeśli nie jest to możliwe, zgłasza zamiast niego ogólny wyjątek modelu COM. Ostatecznym wynikiem jest zwrócenie wartości HRESULT <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego do funkcji com, która wywołała ją.

> [!NOTE]
> Wyjątki naruszają wydajność i mają na celu wskazywanie nietypowych warunków programu. Warunki, które często występują, powinny być obsługiwane wewnętrznie, zamiast zgłoszonego wyjątku.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown przesłane jako void * *
 Poszukaj parametrów [out], które są zdefiniowane jako typ `void **` w interfejsie com, ale które są zdefiniowane jako `[``iid_is``]` w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypie metody zestawu międzyoperacyjnego.

 Czasami interfejs COM generuje `IUnknown` obiekt, a interfejs com przekazuje go jako typ `void **` . Te interfejsy są szczególnie ważne, ponieważ jeśli zmienna jest zdefiniowana jako [out] w IDL, to `IUnknown` obiekt jest liczony jako odwołanie za pomocą `AddRef` metody. Przeciek pamięci występuje, jeśli obiekt nie został poprawnie obsłużony.

> [!NOTE]
> `IUnknown`Obiekt utworzony przez interfejs com i zwrócony w zmiennej [out] powoduje przeciek pamięci, jeśli nie został jawnie wydaną.

 Zarządzane metody obsługujące takie obiekty powinny traktować <xref:System.IntPtr> jako wskaźnik do `IUnknown` obiektu i wywoływać <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodę w celu uzyskania obiektu. Obiekt wywołujący powinien następnie rzutować wartość zwracaną na dowolny typ jest odpowiedni. Gdy obiekt nie jest już wymagany, wywołaj <xref:System.Runtime.InteropServices.Marshal.Release%2A> go.

 Poniżej znajduje się przykład wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metody i `IUnknown` prawidłowego obsługi obiektu:

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
> Następujące metody są znane, aby przekazywać `IUnknown` wskaźniki obiektów jako typ <xref:System.IntPtr> . Obsłuż je zgodnie z opisem w tej sekcji.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Opcjonalne parametry [out]
 Poszukaj parametrów, które są zdefiniowane jako typ danych [out] ( `int` , `object` , i tak dalej) w interfejsie com, ale które są zdefiniowane jako tablice tego samego typu danych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypie metody zestawu międzyoperacyjnego.

 Niektóre interfejsy COM, takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , traktują parametry [out] jako opcjonalne. Jeśli obiekt nie jest wymagany, te interfejsy COM zwracają `null` wskaźnik jako wartość tego parametru, zamiast tworzyć obiekt [out]. Jest to celowe. W przypadku tych interfejsów, `null` przyjmuje się, że wskaźniki są częścią prawidłowego zachowania pakietu VSPackage i żaden błąd nie jest zwracany.

 Ponieważ środowisko CLR nie zezwala na użycie wartości parametru [out] `null` , część zaprojektowanego zachowania tych interfejsów nie jest bezpośrednio dostępna w kodzie zarządzanym. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Metody zestawu międzyoperacyjności dotyczące interfejsów, których dotyczy problem, obejść problem przez zdefiniowanie odpowiednich parametrów jako tablic, ponieważ środowisko CLR umożliwia przekazywanie `null` tablic.

 Zarządzane implementacje tych metod powinny umieścić `null` tablicę w parametrze, gdy nie ma niczego do zwrócenia. W przeciwnym razie Utwórz tablicę z jednym elementem o poprawnym typie i umieść wartość zwracaną w tablicy.

 Metody zarządzane, które odbierają informacje z interfejsów z opcjonalnymi parametrami [out], otrzymują parametr jako tablicę. Po prostu Przeanalizuj wartość pierwszego elementu tablicy. Jeśli tak nie jest `null` , Traktuj pierwszy element tak, jakby był pierwotnym parametrem.

## <a name="passing-constants-in-pointer-parameters"></a>Przekazywanie stałych w parametrach wskaźnika
 Poszukaj parametrów, które są zdefiniowane jako wskaźniki [in] w interfejsie COM, ale które są zdefiniowane jako <xref:System.IntPtr> Typ w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypie metody zestawu międzyoperacyjnego.

 Podobny problem występuje, gdy interfejs COM przekazuje specjalną wartość, taką jak 0,-1 lub-2, zamiast wskaźnika obiektu. W przeciwieństwie do [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , środowisko CLR nie zezwala na rzutowanie stałych jako obiektów. Zamiast tego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestaw międzyoperacyjny definiuje parametr jako <xref:System.IntPtr> Typ.

 Zarządzane implementacje tych metod powinny korzystać z faktu, że <xref:System.IntPtr> Klasa ma zarówno `int` konstruktora, `void *` jak i konstruktorów <xref:System.IntPtr> , aby utworzyć obiekt na podstawie albo do stałej, jak i w razie potrzeby.

 Metody zarządzane, które odbierają <xref:System.IntPtr> Parametry tego typu, powinny używać <xref:System.IntPtr> operatorów konwersji typów do obsługi wyników. Najpierw przekonwertuj wartość <xref:System.IntPtr> na `int` i przetestuj ją względem odpowiednich stałych całkowitych. Jeśli wartości nie są zgodne, przekonwertuj je na obiekt typu wymaganego i Kontynuuj.

 Aby zapoznać się z przykładami, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Wartości zwracane przez OLE zostały przesłane jako parametry [out]
 Wyszukaj metody, które mają `retval` wartość zwracaną w interfejsie com, ale które mają `int` wartość zwracaną i dodatkowy parametr tablicy [out] w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypie metody zestawu międzyoperacyjnego. Powinno być jasne, że te metody wymagają specjalnej obsługi, ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypy metod zestawu międzyoperacyjnego mają jeden parametr niż metody interfejsu com.

 Wiele interfejsów COM, które zajmują się działaniem OLE, wysyła informacje o stanie OLE z powrotem do wywołującego programu przechowywanego w `retval` wartości zwracanej przez interfejs. Zamiast korzystać z wartości zwracanej, odpowiednie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody zestawu międzyoperacyjnego wysyłają informacje z powrotem do wywołującego programu przechowywanego w parametrze tablicy [out].

 Zarządzane implementacje tych metod powinny tworzyć jednoelementową tablicę tego samego typu co parametr [out] i umieścić ją w parametrze. Wartość elementu Array powinna być taka sama jak w przypadku odpowiedniego modelu COM `retval` .

 Metody zarządzane, które wywołują interfejsy tego typu, powinny pobierać pierwszy element z tablicy [out]. Ten element może być traktowany tak, jakby był `retval` wartością zwracaną z odpowiedniego interfejsu com.

## <a name="see-also"></a>Zobacz też
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
