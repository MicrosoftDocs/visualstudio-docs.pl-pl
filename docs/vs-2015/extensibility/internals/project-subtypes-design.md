---
title: Podtypy projektów projekt | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78b768ae63fcf03912d4f81820e80706f8a46a98
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776467"
---
# <a name="project-subtypes-design"></a>Projektowanie podtypów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtypy projektów umożliwiają pakietów VSPackage rozszerzanie projektów opartych na aparatu Microsoft Build Engine (MSBuild). Użycie agregacji umożliwia ponowne używanie zbiorcze systemu projektu core zarządzane, które są zaimplementowane w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ale nadal dostosować zachowanie w przypadku danego scenariusza.  
  
 Poniższe tematy przedstawiają szczegółowo, podstawowe projektowania i implementowania podtypy projektów:  
  
-   Podtypu projektu.  
  
-   Wielopoziomowe agregacji.  
  
-   Obsługa interfejsów.  
  
## <a name="project-subtype-design"></a>Podtypu projektu  
 Inicjowanie podtypu projektu odbywa się agregowanie głównym <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> obiektów. Takie połączenie umożliwia podtypem projektu do nadpisania lub zwiększ większość funkcji projektu podstawowego. Podtypy projektów uzyskać pierwszy szansę, aby obsłużyć właściwości za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, poleceń, za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>i Projekt element zarządzania za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Dodatkowo można rozszerzyć podtypy projektów:  
  
- Obiekty konfiguracji projektu.  
  
- Obiekty zależne od konfiguracji.  
  
- Niezależne od konfiguracji przeglądania obiektów.  
  
- Obiekty automatyzacji projektu.  
  
- Kolekcje właściwości automatyzacji dla projektu.  
  
  Aby uzyskać więcej informacji na temat rozszerzania przez podtypy projektów, zobacz [właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Pliki zasad  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Środowisko zawiera przykład rozszerzanie systemu projektu podstawowego z podtypem projektu w swojej implementacji pliki zasad. Plik zasad umożliwia przekształcanie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska dzięki zarządzaniu funkcje, w Eksploratorze rozwiązań **Dodaj projekt** okno dialogowe **Dodaj nowy element** okno dialogowe i  **Właściwości** okno dialogowe. Podtyp zasad zastępuje i rozszerza te funkcje przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementacji.  
  
##### <a name="aggregation-mechanism"></a>Mechanizm agregacji  
 Mechanizm agregacji podtypu projektu środowiska obsługuje agregacji, dzięki czemu zaawansowane podtyp implementowany przez dalsze flavoring projektu przeznaczonego na wielu poziomach. Ponadto obiekty pomocnicze projektu podtypu, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, pozwalają na wielu poziomach warstwowe. Zgodnie z ograniczeniami COM i COM reguły agregacji, podtypy projektów i projektów podstawowego konieczne programowane wspólne podtyp wewnętrzny lub projektu podstawowego, prawidłowo uczestniczyć w delegowanie wywołań metod i zarządzanie nimi odwołań . Oznacza to projektu do agregowania musi być zaprogramowane, aby obsługiwać agregacji.  
  
 Poniższa ilustracja przedstawia schematyczny reprezentacją agregacji podtypu projektu wielopoziomowe.  
  
 ![Grafika przedstawiająca wielopoziomowej projectflavor Visual Studio](../../extensibility/internals/media/vs-multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Podtyp wielopoziomowej projektu  
  
 Agregacja podtypu projektu wielopoziomowe składa się z trzech poziomów, podstawowego projektu, który jest agregowana przez podtypu projektu, a następnie dodatkowo agregowane przez podtypu projektu zaawansowane. Rysunek koncentruje się na niektórych pomocnicze interfejsy, które są dostarczane jako część [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] architektura podtypu projektu.  
  
##### <a name="deployment-mechanisms"></a>Mechanizmy wdrażania  
 Wśród wielu systemu podstawowego projektu funkcje ulepszane z wykorzystaniem podtypu projektu są mechanizmy wdrożenia. Mechanizmy wdrażania ma wpływ podtypu projektu poprzez implementację interfejsów konfiguracji (takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), są pobierane za pomocą wywołania QueryInterface na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. W scenariuszu, gdzie podtypu projektu i podtypem projektu zaawansowane dodać inną konfigurację implementacji, wywołuje projektu podstawowego `QueryInterface` na podtypu projektu zaawansowane `IUnknown`. Jeśli podtypu projektu wewnętrzny zawiera implementację konfiguracji, który żąda projektu podstawowego, podtypu projektu zaawansowane deleguje do implementacji, dostarczone przez podtypu projektu wewnętrznego. Jako mechanizm utrwalanie stanu z poziomu jednego agregacji do innego wdrożenia wszystkie poziomy podtypy projektów <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> można utrwalić bez kompilacji powiązane dane XML w plikach projektu. Aby uzyskać więcej informacji, zobacz [przechowywanie danych w pliku projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> jest implementowany jako mechanizm można pobrać urządzeń Extender automatyzacji z podtypy projektów.  
  
 Na poniższej ilustracji koncentruje się na implementacji extender automatyzacji, obiekt przeglądania konfiguracji projektu w szczególności używanej przez podtypy projektów do rozszerzania systemu podstawowego projektu.  
  
 ![VS Project Flavor Auto Extender graphic](../../extensibility/internals/media/vs-projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Urządzenie Extender automatyzacji podtypu projektu.  
  
 Podtypy projektów Dodatkowo można rozszerzyć systemu podstawowego projektu, rozszerzając modelu obiektu automatyzacji. Te są zdefiniowane jako część obiektu automatyzacji DTE i służą do rozszerzania obiektu projektu `ProjectItem` obiektu i `Configuration` obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie modelu obiektu projektu Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Wielopoziomowe agregacji  
 Implementacji podtypu projektu, który otacza niższe podtypu projektu musi programowane wspólne umożliwia podtypu projektu wewnętrznego działać prawidłowo. Lista programowania obowiązki obejmuje:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementacji podtyp projektu, do którego jest zawijany wewnętrzny podtyp musi delegować do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementacji podtypu projektu wewnętrznego dla obu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> Implementacji podtypu projektu otoki musi delegować, jego podtypu projektu wewnętrznego. W szczególności wykonania <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> musi uzyskać ciąg nazwy z podtypu projektu wewnętrzny i następnie ciągów chce, aby dodać jako urządzenia Extender.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Utworzyć implementacji podtypu projektu otoki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> obiekt wewnętrzny jego podtypu projektu i przytrzymaj go jako Delegat prywatny, ponieważ tylko obiekt konfiguracji projektu podstawowego projektu bezpośrednio wie, że otoki istnieje obiekt konfiguracji podtypu projektu. Podtypu projektu zewnętrznego można początkowo wybrać interfejsy konfiguracji, które chce obsługiwać bezpośrednio, a następnie poprzez delegowanie przekazać rest podtypu projektu wewnętrznej implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Obsługa interfejsów  
 Podstawowy projekt deleguje wywołania do obsługi dodane przez podtypem projektu interfejsach rozszerzenie różnych aspektów implementacji. W tym rozszerzanie obiektów konfiguracji projektu i różnych właściwości przeglądarki obiektów. Te interfejsy są pobierane przez wywołanie metody `QueryInterface` na `punkOuter` (wskaźnik do `IUnknown`) z agregatora podtypu projektu najbardziej zewnętrznej.  
  
|Interface|Podtypu projektu|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> — Podać implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Kontrolowanie uruchamiania debugera, umożliwiając podtypu projektu zapewnienie własną implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />— Wyłącz Obliczanie wyrażenia czasu projektowania przy odpowiednio `DBGLAUNCH_DesignTimeExprEval` wielkości liter w jego implementacja obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> -Rozszerzyć <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> projektu, aby dodać lub usunąć właściwości niezależnie od konfiguracji projektu.<br />-Rozszerzenie obiektu automatyzacji projektu (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) projektu.<br /><br /> Powyższe wartości właściwości są pobierane z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wyliczenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umożliwia podtypu projektu zamapować powrót do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiekt na podstawie obiektu przeglądania konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umożliwia podtypu projektu zamapować powrót do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> lub `VSITEMID` obiektu, biorąc pod uwagę obiekt przeglądania konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umożliwia podtypu projektu utrwalić dowolne dane ze strukturą XML do pliku projektu (.vbproj lub .csproj). Te dane nie jest widoczna do programu MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> — Dodawanie nowych właściwości programu MSBuild w celu jego utrwalenia.<br />— Usuń zbędne właściwości z programu MSBuild.<br />-Query dla bieżącej wartości właściwości programu MSBuild.<br />-Zmień bieżącą wartość właściwości programu MSBuild.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
