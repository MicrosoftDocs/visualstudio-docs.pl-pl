---
title: Organizowanie parametrów zestawu międzyoperacyjnego programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686925"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Kierowanie parametrów zestawu międzyoperacyjnego programu Visual Studio
Pakietów VSPackage, które są zapisywane w kodzie zarządzanym, może być wywoływana lub być wywołana przez niezarządzany kod COM. Zazwyczaj argumenty metody są przekształcane lub organizowane automatycznie przez organizatora międzyoperacyjności. Jednak czasami argumenty nie mogą być przekształcone w prosty sposób. W takich przypadkach parametry prototypu metody zestawu międzyoperacyjnego są używane do dokładnego dopasowania parametrów funkcji COM. Aby uzyskać więcej informacji, zobacz [organizowanie międzyoperacyjnych](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Ogólne sugestie  
  
##### <a name="read-the-reference-documentation"></a>Przeczytaj dokumentację referencyjną  
 Skutecznym sposobem wykrywania problemów ze współdziałaniem jest zapoznanie się z dokumentacją referencyjną dla każdej z tych metod.  
  
 Dokumentacja referencyjna dla każdej metody zawiera trzy odpowiednie sekcje:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Prototyp funkcji com.  
  
- Prototyp metody zestawu międzyoperacyjnego.  
  
- Lista parametrów COM i Krótki opis każdego z nich.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Poszukaj różnic między dwoma prototypami  
 Większość problemów ze współdziałaniem wynika z niezgodności między definicją określonego typu w interfejsie COM a definicją tego samego typu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawach międzyoperacyjnych. Rozważmy na przykład różnicę w zakresie możliwości przekazania `null` wartości w parametrze [out]. Należy wyszukać różnice między tymi dwoma prototypami i wziąć pod uwagę ich konsekwencje dla danych, które są przesyłane.  
  
##### <a name="read-the-parameter-definitions"></a>Odczytywanie definicji parametrów  
 Przeczytaj definicje parametrów. COM jest mniej rygorystyczny niż środowisko uruchomieniowe języka wspólnego (CLR) dotyczące mieszania różnych typów danych w pojedynczym parametrze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Interfejsy com w pełni wykorzystują tę elastyczność. Wszystkie parametry, które mogą przekazać lub wymagać niestandardową wartość lub typ danych, takie jak wartość stała w parametrze wskaźnika, powinny być opisane w dokumentacji.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Obiekty IUnknown przechodzą jako typ void * *  
 Poszukaj parametrów [out], które są zdefiniowane jako typ `void **` w interfejsie com, ale które są zdefiniowane jako `[``iid_is``]` w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypie metody zestawu międzyoperacyjnego.  
  
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
  
### <a name="optional-out-parameters"></a>Opcjonalne parametry [out]  
 Poszukaj parametrów, które są zdefiniowane jako typ danych [out] ( `int` , `object` , i tak dalej) w interfejsie com, ale które są zdefiniowane jako tablice tego samego typu danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypie metody zestawu międzyoperacyjnego.  
  
 Niektóre interfejsy COM, takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , traktują parametry [out] jako opcjonalne. Jeśli obiekt nie jest wymagany, te interfejsy COM zwracają `null` wskaźnik jako wartość tego parametru, zamiast tworzyć obiekt [out]. Jest to celowe. W przypadku tych interfejsów, `null` przyjmuje się, że wskaźniki są częścią prawidłowego zachowania pakietu VSPackage i żaden błąd nie jest zwracany.  
  
 Ponieważ środowisko CLR nie zezwala na użycie wartości parametru [out] `null` , część zaprojektowanego zachowania tych interfejsów nie jest bezpośrednio dostępna w kodzie zarządzanym. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Metody zestawu międzyoperacyjności dotyczące interfejsów, których dotyczy problem, obejść problem przez zdefiniowanie odpowiednich parametrów jako tablic, ponieważ środowisko CLR umożliwia przekazywanie `null` tablic.  
  
 Zarządzane implementacje tych metod powinny umieścić `null` tablicę w parametrze, gdy nie ma niczego do zwrócenia. W przeciwnym razie Utwórz tablicę z jednym elementem o poprawnym typie i umieść wartość zwracaną w tablicy.  
  
 Metody zarządzane, które odbierają informacje z interfejsów z opcjonalnymi parametrami [out], otrzymują parametr jako tablicę. Po prostu Przeanalizuj wartość pierwszego elementu tablicy. Jeśli tak nie jest `null` , Traktuj pierwszy element tak, jakby był pierwotnym parametrem.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Przekazywanie stałych w parametrach wskaźnika  
 Poszukaj parametrów, które są zdefiniowane jako wskaźniki [in] w interfejsie COM, ale które są zdefiniowane jako <xref:System.IntPtr> Typ w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypie metody zestawu międzyoperacyjnego.  
  
 Podobny problem występuje, gdy interfejs COM przekazuje wartość specjalną, taką jak 0,-1 lub – 2, zamiast wskaźnika obiektu. W przeciwieństwie do [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , środowisko CLR nie zezwala na rzutowanie stałych jako obiektów. Zamiast tego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestaw międzyoperacyjny definiuje parametr jako <xref:System.IntPtr> Typ.  
  
 Zarządzane implementacje tych metod powinny korzystać z faktu, że <xref:System.IntPtr> Klasa ma zarówno `int` konstruktora, `void *` jak i konstruktorów <xref:System.IntPtr> , aby utworzyć obiekt na podstawie albo do stałej, jak i w razie potrzeby.  
  
 Metody zarządzane, które odbierają <xref:System.IntPtr> Parametry tego typu, powinny używać <xref:System.IntPtr> operatorów konwersji typów do obsługi wyników. Najpierw przekonwertuj wartość <xref:System.IntPtr> na `int` i przetestuj ją względem odpowiednich stałych całkowitych. Jeśli wartości nie są zgodne, przekonwertuj je na obiekt typu wymaganego i Kontynuuj.  
  
 Aby zapoznać się z przykładami, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Wartości zwracane przez OLE zostały przesłane jako parametry [out]  
 Wyszukaj metody, które mają `retval` wartość zwracaną w interfejsie com, ale które mają `int` wartość zwracaną i dodatkowy parametr tablicy [out] w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypie metody zestawu międzyoperacyjnego. Powinno być jasne, że te metody wymagają specjalnej obsługi, ponieważ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypy metod zestawu międzyoperacyjnego mają jeden parametr niż metody interfejsu com.  
  
 Wiele interfejsów COM, które zajmują się działaniem OLE, wysyła informacje o stanie OLE z powrotem do wywołującego programu przechowywanego w `retval` wartości zwracanej przez interfejs. Zamiast korzystać z wartości zwracanej, odpowiednie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metody zestawu międzyoperacyjnego wysyłają informacje z powrotem do wywołującego programu przechowywanego w parametrze tablicy [out].  
  
 Zarządzane implementacje tych metod powinny tworzyć jednoelementową tablicę tego samego typu co parametr [out] i umieścić ją w parametrze. Wartość elementu Array powinna być taka sama jak w przypadku odpowiedniego modelu COM `retval` .  
  
 Metody zarządzane, które wywołują interfejsy tego typu, powinny pobierać pierwszy element z tablicy [out]. Ten element może być traktowany tak, jakby był `retval` wartością zwracaną z odpowiedniego interfejsu com.  
  
## <a name="see-also"></a>Zobacz też  
 [Organizowanie międzyoperacyjnych](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Organizowanie międzyoperacyjnych](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Współpraca w rozwiązywaniu problemów](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Zarządzane pakietów VSPackage](../misc/managed-vspackages.md)