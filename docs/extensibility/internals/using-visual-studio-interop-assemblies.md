---
title: Korzystanie z zestawów interop programu Visual Studio | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704131"
---
# <a name="using-visual-studio-interop-assemblies"></a>Korzystanie z zestawów międzyoperacyjnych programu Visual Studio
Zestawy międzyoperacyjne programu Visual Studio umożliwiają zarządzanym aplikacjom dostęp do interfejsów COM, które zapewniają rozszerzalność programu Visual Studio. Istnieją pewne różnice między prostymi interfejsami COM a ich wersjami międzyoperacyjnymi. Na przykład HRESULTs są zazwyczaj reprezentowane jako wartości int i muszą być obsługiwane w taki sam sposób jak wyjątki i parametry (zwłaszcza out parametry) są traktowane inaczej.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa HRESULTs zwrócona do kodu zarządzanego z COM
 Po wywołaniu interfejsu COM z kodu zarządzanego, sprawdź wartość HRESULT i zgłosić wyjątek, jeśli jest to wymagane. Klasa <xref:Microsoft.VisualStudio.ErrorHandler> zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodę, która zgłasza wyjątek COM, w zależności od wartości HRESULT przekazany do niego.

 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przekazywany HRESULT, który ma wartość mniejszą niż zero. W przypadkach, gdy takie HRESULTs są dopuszczalne wartości i nie należy zgłaszać <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> wyjątku, wartości dodatkowych HRESULTS powinny być przekazywane do po wartości są testowane. Jeśli HRESULT testowane pasuje do wszystkich hresult <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>wartości jawnie przekazywane do , nie wyjątek.

> [!NOTE]
> Klasa <xref:Microsoft.VisualStudio.VSConstants> zawiera stałe dla wspólnych HRESULTS, <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przykład i , i <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> HRESULTS, na przykład i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>zawiera również <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> i metody, które odpowiadają pomyślnie i failed makr w COM.

 Rozważmy na przykład następujące wywołanie <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> funkcji, w którym jest dopuszczalna wartość zwracana, ale wszelkie inne HRESULT mniej niż zero reprezentuje błąd.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Jeśli istnieje więcej niż jedna dopuszczalna wartość zwracana, dodatkowe wartości HRESULT można <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>po prostu dołączyć do listy w wywołaniu .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Powrót HRESULTS do com z kodu zarządzanego
 Jeśli nie wystąpi wyjątek, kod zarządzany zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkcję COM, która go wywoływała. Współdziałacze COM obsługuje typowe wyjątki, które są silnie wpisane w kodzie zarządzanym. Na przykład metoda, która `null` odbiera niedopuszczalne <xref:System.ArgumentNullException>argumentrzuca .

 Jeśli nie masz pewności, który wyjątek zgłosić, ale wiesz, HRESULT chcesz <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> powrócić do com, można użyć metody, aby zgłosić odpowiedni wyjątek. Działa to nawet z niestandardowym błędem, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>na przykład. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>próby mapowania hresult przeszedł do niego do silnie wpisanego wyjątku. Jeśli nie, zgłasza ogólny wyjątek COM zamiast tego. Ostatecznym wynikiem jest to, że HRESULT przekazać <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego jest zwracany do funkcji COM, który go wywoływał.

> [!NOTE]
> Wyjątki zagrażają wydajności i mają na celu wskazanie nieprawidłowych warunków programu. Warunki, które występują często powinny być obsługiwane w linii, zamiast wyjątku zgłoszonych.

## <a name="iunknown-parameters-passed-as-type-void"></a>Nieznane parametry przekazywane jako typ void**
 Poszukaj parametrów [out], `void **` które są zdefiniowane jako `[``iid_is``]` typ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w interfejsie COM, ale które są zdefiniowane jako w prototypie metody montażu międzyoperacyjnego.

 Czasami interfejs COM generuje `IUnknown` obiekt, a interfejs COM przekazuje `void **`go jako typ . Te interfejsy są szczególnie ważne, ponieważ jeśli zmienna jest zdefiniowana `IUnknown` jako [out] w `AddRef` IDL, a następnie obiekt jest zliczany przez odwołanie z metodą. Przeciek pamięci występuje, jeśli obiekt nie jest obsługiwany poprawnie.

> [!NOTE]
> Obiekt `IUnknown` utworzony przez interfejs COM i zwrócony w [out] zmiennej powoduje przeciek pamięci, jeśli nie jest jawnie zwolniony.

 Metody zarządzane, które obsługują <xref:System.IntPtr> takie obiekty `IUnknown` powinny być traktowane <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> jako wskaźnik do obiektu i wywołać metodę, aby uzyskać obiekt. Wywołujący należy następnie rzutować wartość zwracaną do dowolnego typu jest odpowiedni. Gdy obiekt nie jest już <xref:System.Runtime.InteropServices.Marshal.Release%2A> potrzebny, wywołanie go zwolnić.

 Poniżej przedstawiono przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> wywołania `IUnknown` metody i poprawnego obchodzenia się z obiektem:

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
> Następujące metody są znane `IUnknown` przekazać wskaźniki <xref:System.IntPtr>obiektu jako typ . Obsłużyć je zgodnie z opisem w tej sekcji.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Opcjonalne parametry [out]
 Poszukaj parametrów, które są zdefiniowane jako typ danych [out] (`int`, `object`i tak dalej) w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsie COM, ale które są zdefiniowane jako tablice tego samego typu danych w prototypie metody montażu międzyoperacyjnego.

 Niektóre interfejsy COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>takie jak parametry [out] jako opcjonalne. Jeśli obiekt nie jest wymagany, te interfejsy COM zwracają `null` wskaźnik jako wartość tego parametru zamiast tworzenia [out] obiektu. Jest to celowe. W przypadku tych `null` interfejsów wskaźniki są zakładane jako część poprawne zachowanie VSPackage i nie zwracany jest żaden błąd.

 Ponieważ clr nie zezwala na wartość [out] `null`parametr być, część zaprojektowane zachowanie tych interfejsów nie jest bezpośrednio dostępna w kodzie zarządzanym. Metody [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestawu międzyoperacyjnego dla interfejsów, których dotyczy problem, obejść ten problem, definiując odpowiednie parametry jako tablice, ponieważ CLR umożliwia przekazywanie `null` tablic.

 Zarządzane implementacje tych metod `null` należy umieścić tablicy do parametru, gdy nie ma nic do zwrotu. W przeciwnym razie należy utworzyć tablicę jednoelementową właściwego typu i umieścić wartość zwracaną w tablicy.

 Metody zarządzane, które odbierają informacje z interfejsów z opcjonalnymi parametrami [out] odbierają parametr jako tablicę. Wystarczy sprawdzić wartość pierwszego elementu tablicy. Jeśli tak `null`nie jest, potraktuj pierwszy element tak, jakby był oryginalnym parametrem.

## <a name="passing-constants-in-pointer-parameters"></a>Przekazywanie stałych w parametrach wskaźnika
 Poszukaj parametrów, które są zdefiniowane jako [w] wskaźniki <xref:System.IntPtr> w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsie COM, ale które są zdefiniowane jako typ w prototypie metody montażu międzyoperacyjnego.

 Podobny problem występuje, gdy interfejs COM przekazuje specjalną wartość, taką jak 0, -1 lub -2, zamiast wskaźnika obiektu. W [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]przeciwieństwie do programu CLR nie zezwala na rzutowanie stałych jako obiektów. Zamiast tego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zestaw interop definiuje parametr <xref:System.IntPtr> jako typ.

 Zarządzane implementacje tych metod należy skorzystać <xref:System.IntPtr> z faktu, `void *` że klasa <xref:System.IntPtr> ma zarówno `int` i konstruktorów do utworzenia z obiektu lub stałej całkowitej, w stosownych przypadkach.

 Metody zarządzane, <xref:System.IntPtr> które odbierają <xref:System.IntPtr> parametry tego typu, należy użyć operatorów konwersji typu do obsługi wyników. Najpierw przekonwertuj <xref:System.IntPtr> na `int` i przetestuj go względem odpowiednich stałych liczby całkowitej. Jeśli żadne wartości nie są zgodne, przekonwertuj je na obiekt wymaganego typu i kontynuuj.

 Przykłady tego, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>i .

## <a name="ole-return-values-passed-as-out-parameters"></a>Wartości zwrotu OLE przekazywane jako parametry [out]
 Poszukaj metod, które mają wartość zwracaną `retval` `int` w interfejsie COM, ale które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mają wartość zwracaną i dodatkowy parametr tablicy [out] w prototypie metody zestawu międzyoperacyjnego. Należy wyjaśnić, że te metody wymagają [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] specjalnej obsługi, ponieważ prototypy metody montażu międzyoperacyjnego mają jeden parametr więcej niż metody interfejsu COM.

 Wiele interfejsów COM, które zajmują się działaniem OLE, wysyła `retval` informacje o stanie OLE z powrotem do programu wywołującego przechowywanego w wartości zwracanej interfejsu. Zamiast używać wartości zwracanej, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odpowiednie metody zestawu międzyoperacyjnego wysyłają informacje z powrotem do programu wywołującego przechowywanego w parametrze tablicy [out].

 Zarządzane implementacje tych metod należy utworzyć tablicę jednoelementową tego samego typu co parametr [out] i umieścić go w parametrze. Wartość elementu tablicy powinna być taka sama `retval`jak odpowiedni COM .

 Metody zarządzane, które wywołują interfejsy tego typu należy wyciągnąć pierwszy element z [out] tablicy. Ten element może być traktowany `retval` tak, jakby był to zwracany z odpowiedniego interfejsu COM.

## <a name="see-also"></a>Zobacz też
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
