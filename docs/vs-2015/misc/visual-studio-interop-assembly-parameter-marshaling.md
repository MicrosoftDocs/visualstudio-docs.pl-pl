---
title: Parametr zestawu międzyoperacyjnego programu Visual Studio Marshaling | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686925"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Parametr zestawu międzyoperacyjnego programu Visual Studio Marshalingu
Pakietów VSPackage, które są zapisywane w kodzie zarządzanym może być konieczne wywoływanie lub można wywoływać za pomocą kodu niezarządzanego COM. Argumenty metody są zazwyczaj transformowany lub zorganizować automatycznie, organizator międzyoperacyjny. Jednak czasami argumenty nie mogą zostać przekształcone w prosty sposób. W takich przypadkach parametrów prototypu zestawu międzyoperacyjnego metody są używane do możliwie najdokładniej dopasować parametrów funkcji COM. Aby uzyskać więcej informacji, zobacz [Marshaling międzyoperacyjności](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Ogólne sugestie  
  
##### <a name="read-the-reference-documentation"></a>Przeczytaj dokumenty referencyjne  
 Efektywny sposób wykrywania problemów ze współdziałaniem jest przeczytaj dokumenty referencyjne dla każdej metody.  
  
 Dokumentacja dla każdej metody zawiera trzy istotne sekcje:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Prototypu funkcji COM.  
  
- Prototyp metoda zestawu międzyoperacyjnego.  
  
- Lista parametrów COM i krótki opis każdego z nich.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Zwróć uwagę na różnice między dwa prototypy  
 Zagadnienia dotyczące współdziałania większość dziedziczyć niezgodności między definicji typu określonego za pomocą interfejsu COM, jak i definicja tego samego typu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawy międzyoperacyjne. Na przykład, należy wziąć pod uwagę różnice w możliwość przekazywania `null` wartości parametrów [out]. Należy szukać różnice między dwa prototypy i należy wziąć pod uwagę ich rozgałęzień dla przekazywanych danych.  
  
##### <a name="read-the-parameter-definitions"></a>Odczytaj definicje parametrów  
 Odczytaj definicje parametrów. COM jest mniej rygorystyczne niż środowisko uruchomieniowe języka wspólnego (CLR) dotyczące różnych typów danych w jeden parametr. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interfejsów COM w pełni korzystać z tej elastyczności. Parametr można przekazać lub wymagają niestandardowych wartości lub typu danych, takich jak wartości stałej w parametrze wskaźnika, powinny być opisane w związku z tym w dokumentacji.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown przekazywanym jako typ void **  
 Wyszukaj [out] Parametry, które są zdefiniowane jako typ `void **` w COM interfejs, ale są definiowane jako `[``iid_is``]` w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego metody prototypu.  
  
 Czasami generuje interfejsu COM `IUnknown` obiektu i interfejsu COM następnie przekazuje ją jako typ `void **`. Te interfejsy są szczególnie ważne, ponieważ jeśli zmienna jest zdefiniowana jako [out] w pliku IDL, a następnie `IUnknown` obiekt jest zliczonych odwołań z `AddRef` metody. Jeśli obiekt nie jest obsługiwany poprawnie występuje przeciek pamięci.  
  
> [!NOTE]
> `IUnknown` Obiekt utworzony przy użyciu interfejsu COM i zwracane w zmiennej [out] powoduje przeciek pamięci, jeśli nie jest jawnie zwalniane.  
  
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
> Wiadomo, że następujące metody przekazywania `IUnknown` obiektu wskaźników jako typ <xref:System.IntPtr>. Je obsłużyć zgodnie z opisem w tej sekcji.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Opcjonalne [parametry out]  
 Wyszukaj parametry, które są zdefiniowane jako [out] — Typ danych (`int`, `object`i tak dalej) w COM interfejs, ale są definiowane jako tablice tego samego typu danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego metody prototypu.  
  
 Niektóre COM interfejsów, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, Traktuj [opcjonalne parametry out]. Jeśli obiekt nie jest wymagane, zwracają te interfejsy COM `null` wskaźnik jako wartość tego parametru, zamiast tworzyć [out] obiekt. To jest celowe. Dla tych interfejsów `null` wskaźniki będą traktowani jako część prawidłowe działanie pakietu VSPackage, a nie błąd jest zwracany.  
  
 Ponieważ środowisko CLR nie zezwala na wartość parametru [out] jako `null`, część zaprojektowane zachowanie tych interfejsów nie jest dostępne bezpośrednio w kodzie zarządzanym. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Metod zestawu międzyoperacyjnego dla interfejsów, których to dotyczy obejść ten problem, definiując odpowiednich parametrów jak tablice, ponieważ środowisko CLR zezwala na przekazywanie `null` tablic.  
  
 Należy umieścić zarządzanej implementacji tych metod `null` tablicę do parametru gdy nie ma nic do zwrócenia. W przeciwnym razie utwórz jeden elementowej tablicy poprawnego typu i umieścić wartości zwracanej w tablicy.  
  
 Zarządzane metody, które otrzymywanie informacji z współpracuje z opcjonalne [out] Parametry pobierają parametr jako tablicę. Po prostu sprawdzić wartość pierwszego elementu tablicy. Jeśli nie jest `null`, Traktuj pierwszego elementu, tak jakby pierwotny parametr.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Stałe przekazywanie w parametrach wskaźnika  
 Wyszukaj parametry, które są definiowane jako [in] wskaźniki w interfejsie COM, ale które są definiowane jako <xref:System.IntPtr> wpisać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego metody prototypu.  
  
 Podobny problem występuje, gdy interfejs COM przekazuje wartość specjalne, np. 0, -1 lub -2, a nie wskaźnik do obiektu. W odróżnieniu od [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], środowisko CLR nie zezwala na stałe, można rzutować jako obiekty. Zamiast tego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego definiuje jako parametr <xref:System.IntPtr> typu.  
  
 Zarządzanej implementacji metody te powinny korzystać z zalet fakt, <xref:System.IntPtr> klasa ma zarówno `int` i `void *` konstruktorów do tworzenia <xref:System.IntPtr> z obiektem lub stała liczba całkowita, w stosownych przypadkach.  
  
 Zarządzane metody, które odbierają <xref:System.IntPtr> parametry tego typu należy używać <xref:System.IntPtr> wpisz operatory konwersji do obsługi wyników. Najpierw przekonwertuj <xref:System.IntPtr> do `int` i testujemy stałe całkowite istotne. Jeśli żadne wartości nie są zgodne, przekonwertuj go na obiekt typu wymagane i kontynuować.  
  
 Przykłady tego, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE zwracają wartości przekazane jako [parametry out]  
 Wyszukaj metody, które mają `retval` mają wartości zwracanej w interfejsu COM, ale `int` zwracać wartości i dodatkowy [parametr tablicy w out] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego metody prototypu. Powinno być jasne, że te metody wymagają specjalnej obsługi, ponieważ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawu międzyoperacyjnego metoda prototypów ma jeden parametr więcej niż metody interfejsu COM.  
  
 Wiele interfejsów COM, które zajmują się działanie OLE wysyłane informacje o stanie OLE program wywołujący przechowywane w `retval` zwracają wartość interfejs. Zamiast używania zwracanej wartości, odpowiedni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metod zestawu międzyoperacyjnego wysyłane informacje przechowywane w [out] program wywołujący tablicy parametrów.  
  
 Zarządzane implementacji tych metod należy utworzyć jednoelementowa tablica tego samego typu co parametr [out] i umieścić go w parametrze. Wartość elementu tablicy, powinna być taka sama jak odpowiednie COM `retval`.  
  
 Zarządzanych metod, które wywołują interfejsy tego typu należy ściągnąć pierwszego elementu poza [out] tablica. Ten element może być traktowana tak, jakby była `retval` zwracanie wartości z odpowiedniego interfejsu COM.  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling międzyoperacyjny](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshaling międzyoperacyjny](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Problemów związanych ze współdziałaniem](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Managed VSPackages](../misc/managed-vspackages.md)