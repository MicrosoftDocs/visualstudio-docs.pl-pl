---
title: Projekt podtypów projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706449"
---
# <a name="project-subtypes-design"></a>Projektowanie podtypów projektów

Podtypy projektu umożliwiają pakiety VSPackages rozszerzają projekty na podstawie aparatu kompilacji firmy Microsoft (MSBuild). Użycie agregacji umożliwia ponowne użycie większości podstawowego zarządzanego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] systemu projektu zaimplementowanego w jeszcze nadal dostosowywać zachowanie dla określonego scenariusza.

 Następujące tematy szczegółowo podstawowe projektowanie i wdrażanie podtypów projektu:

- Projekt podtypu projektu.

- Agregacja wielopoziomowa.

- Interfejsy pomocnicze.

## <a name="project-subtype-design"></a>Projekt podtypu projektu

Inicjowanie podtypu projektu odbywa się poprzez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> agregowanie głównych i obiektów. Ta agregacja umożliwia podtyp projektu zastąpić lub zwiększyć większość możliwości projektu podstawowego. Podtypy projektu otrzymują pierwszą szansę <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>na obsługę <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>przy użyciu , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>polecenia za pomocą i , i zarządzania elementami projektu za pomocą . Podtypy projektu mogą również rozszerzać:

- Obiekty konfiguracji projektu.

- Obiekty zależne od konfiguracji.

- Przeglądanie obiektów niezależne od konfiguracji.

- Obiekty automatyzacji projektu.

- Kolekcje właściwości automatyzacji projektu.

Aby uzyskać więcej informacji na temat rozszerzalności według podtypów projektu, zobacz [Właściwości i metody rozszerzone według podtypów projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Pliki zasad

Środowisko [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera przykład rozszerzenia systemu projektu podstawowego o podtyp projektu w jego realizacji plików zasad. Plik zasad umożliwia kształtowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska przez zarządzanie funkcjami, które obejmują Eksplorator rozwiązań, Okno dialogowe **Dodawanie projektu,** **Dodawanie nowego elementu** i okno **dialogowe Właściwości.** Podtyp zasad zastępuje i ulepsza te <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` funkcje za pomocą programu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementacji.

### <a name="aggregation-mechanism"></a>Mechanizm agregacji

Mechanizm agregacji podtypu projektu środowiska obsługuje wiele poziomów agregacji, umożliwiając w ten sposób zaimplementowanie zaawansowanego podtypu przez dalsze aromatyzowanie projektu smakowego. Ponadto obiekty pomocnicze podtypu projektu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>takie jak , są zaprojektowane tak, aby umożliwić wiele poziomów warstw. Zgodnie z ograniczeniami reguł agregacji COM i COM podtypy projektu i projekty podstawowe muszą być programowane wspólnie, aby umożliwić podtyp wewnętrzny lub projekt podstawowy, aby prawidłowo uczestniczyć w delegowaniu wywołań metod i zarządzaniu liczbami odwołań. Oznacza to, że projekt, który ma zostać zagregowany, musi zostać zaprogramowany do obsługi agregacji.

Na poniższej ilustracji przedstawiono schematyczną reprezentację wielopoziomowej agregacji podtypu projektu.

![Grafika projektu wielopoziomowego projektu visual studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Wielopoziomowa agregacja podtypu projektu składa się z trzech poziomów, projektu podstawowego, który jest agregowany przez podtyp projektu, a następnie agregowany przez zaawansowany podtyp projektu. Rysunek koncentruje się na niektórych interfejsów pomocniczych, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są dostarczane jako część architektury podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanizmy wdrażania

Wśród wielu funkcji systemu projektu podstawowego wzbogaconych o podtyp projektu są mechanizmy wdrażania. Podtyp projektu wpływa na mechanizmy wdrażania, implementując interfejsy konfiguracji (takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), które są pobierane przez wywołanie QueryInterface on <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. W scenariuszu, w którym zarówno podtyp projektu, jak i podtyp projektu zaawansowanego dodają różne implementacje konfiguracji, projekt podstawowy wywołuje `QueryInterface` podtyp projektu zaawansowanego . `IUnknown` Jeśli podtyp projektu wewnętrznego zawiera implementację konfiguracji, o którą prosi projekt podstawowy, podtyp projektu zaawansowanego deleguje do implementacji dostarczonej przez podtyp projektu wewnętrznego. Jako mechanizm utrwalania stanu z jednego poziomu agregacji do drugiego, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wszystkie poziomy podtypów projektu implementują do utrwalania niezbudowych danych XML powiązanych z nimi w plikach projektu. Aby uzyskać więcej informacji, zobacz [Utrwalanie danych w pliku projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>jest realizowany jako mechanizm pobierania przedłużaczy automatyzacji z podtypów projektu.

Na poniższej ilustracji koncentruje się na implementacji rozszerzenia automatyzacji, konfiguracja projektu przeglądać obiekt w szczególności, używane przez podtypy projektu do rozszerzenia systemu projektu podstawowego.

![Grafika automatycznego przedłużacza vs](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektu można dodatkowo rozszerzyć system projektu podstawowego, rozszerzając model obiektu automatyzacji. Są one zdefiniowane jako część obiektu automatyzacji DTE i są `ProjectItem` używane `Configuration` do rozszerzania project obiektu, obiektu i obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregacja wielopoziomowa

Implementacja podtypu projektu, która otacza podtyp projektu niższego poziomu, musi być programowana wspólnie, aby umożliwić prawidłowe działanie podtypu projektu wewnętrznego. Lista obowiązków programistycznych obejmuje:

- Implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> podtypu projektu, który jest zawijanie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> podtypu wewnętrznego musi <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> delegować do implementacji podtypu projektu wewnętrznego dla obu i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metod.

- Implementacja <xref:EnvDTE80.IInternalExtenderProvider> podtypu projektu otoki musi zostać delegowana do podtypu projektu wewnętrznego. W szczególności implementacja <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> potrzeb, aby uzyskać ciąg nazw z podtypu projektu wewnętrznego, a następnie połączyć ciągi, które chce dodać jako extenderów.

- Implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> podtypu projektu otoki musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> utworzyć wystąpienie obiektu jego podtypu projektu wewnętrznego i przytrzymać go jako pełnomocnika prywatnego, ponieważ tylko obiekt konfiguracji projektu projektu podstawowego wie bezpośrednio, że istnieje obiekt konfiguracji podtypu projektu otoki. Podtyp projektu zewnętrznego może początkowo wybrać interfejsy konfiguracji, które chce obsługiwać bezpośrednio, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>delegować resztę do implementacji podtypu projektu wewnętrznego .

## <a name="supporting-interfaces"></a>Interfejsy pomocnicze

Podstawowy projekt deleguje wywołania do obsługi interfejsów dodanych przez podtyp projektu, aby rozszerzyć różne aspekty jego implementacji. Obejmuje to rozszerzenie obiektów konfiguracji projektu i różnych obiektów przeglądarki właściwości. Interfejsy te są pobierane `punkOuter` przez wywołanie `IUnknown` `QueryInterface` (wskaźnik do ) najbardziej zewnętrznego agregatora podtypu projektu.

|Interface|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umożliwia podtyp projektu:<br /><br /> - Zapewnienie realizacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />- Kontrolować uruchomienie debugera, umożliwiając podtyp projektu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>aby zapewnić własną implementację .<br />- Wyłącz ocenę ekspresji w `DBGLAUNCH_DesignTimeExprEval` czasie projektowania, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>odpowiednio zajmując się sprawą w jej realizacji .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umożliwia podtyp projektu:<br /><br /> - Rozszerzenie <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> projektu, aby dodać lub usunąć niezależne od konfiguracji właściwości projektu.<br />- Rozszerzenie obiektu automatyzacji projektu (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>) projektu.<br /><br /> Powyższe wartości właściwości <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> są pobierane z wyliczenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umożliwia podtyp projektu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> mapowania z powrotem do obiektu, biorąc pod uwagę obiekt przeglądania konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umożliwia podtyp projektu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mapowania `VSITEMID` z powrotem do obiektu lub, biorąc pod uwagę konfigurację projektu przeglądać obiekt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umożliwia podtyp projektu do utrwalenia dowolnych danych strukturalnych XML do pliku projektu (.vbproj lub csproj). Te dane nie są widoczne dla MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umożliwia podtyp projektu:<br /><br /> - Dodaj nowe właściwości MSBuild do utrwalenia.<br />- Usuń niepotrzebne właściwości z MSBuild.<br />- Kwerenda o bieżącą wartość właściwości MSBuild.<br />- Zmień bieżącą wartość właściwości MSBuild.|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
