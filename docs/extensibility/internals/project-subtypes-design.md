---
title: Typy podtypów projektu — | Microsoft Docs
description: Dowiedz się, jak podtypy projektów umożliwiają pakietom VSPackage rozszerzanie projektów na podstawie Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899696"
---
# <a name="project-subtypes-design"></a>Projektowanie podtypów projektów

Podtypy projektów umożliwiają pakietom VSPackage rozszerzanie projektów na podstawie Microsoft Build Engine (MSBuild). Użycie agregacji umożliwia ponowne użycie zbiorczej części podstawowego systemu projektów zarządzanych zaimplementowanych w programie , ale nadal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostosowywać zachowanie dla konkretnego scenariusza.

 W poniższych tematach szczegółowo opisano podstawowy projekt i implementację podtypów projektów:

- Projekt podtypu projektu.

- Agregacja wielopoziomowa.

- Interfejsy obsługi.

## <a name="project-subtype-design"></a>Projekt podtypu projektu

Inicjowanie podtypu projektu jest osiągane przez agregowanie obiektów głównych <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> i . Ta agregacja umożliwia podtypowi projektu zastąpienie lub zwiększenie większości możliwości projektu podstawowego. Podtypy projektów mają pierwszą szansę na obsługę właściwości przy użyciu poleceń , przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> poleceń i oraz zarządzania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> elementami projektu przy użyciu polecenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Podtypy projektów można również rozszerzać:

- Obiekty konfiguracji projektu.

- Obiekty zależne od konfiguracji.

- Przeglądanie obiektów niezależnych od konfiguracji.

- Obiekty automatyzacji projektu.

- Kolekcje właściwości automatyzacji projektu.

Aby uzyskać więcej informacji na temat rozszerzalności według podtypów projektów, zobacz Properties and Methods Extended by Project Subtypes (Właściwości i metody [rozszerzone przez podtypy projektów).](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>Pliki zasad

Środowisko zawiera przykład rozszerzenia podstawowego systemu projektu o podtyp projektu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementacji plików zasad. Plik zasad umożliwia kształtowanie środowiska przez zarządzanie funkcjami, które obejmują Eksplorator rozwiązań, okno dialogowe Dodawanie projektu, okno dialogowe Dodawanie nowego elementu i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] okno **dialogowe** Właściwości.   Podtyp zasad zastępuje i rozszerza te funkcje za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementacji i .

### <a name="aggregation-mechanism"></a>Mechanizm agregacji

Mechanizm agregacji podtypu projektu środowiska obsługuje wiele poziomów agregacji, co umożliwia zaimplementowanie zaawansowanego podtypu przez dalsze łączenie projektu smakowego. Ponadto obiekty obsługi podtypu projektu, takie jak , są zaprojektowane tak, aby zezwalały na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> wiele poziomów warstw. Zgodnie z ograniczeniami reguł agregacji COM i COM podtypy projektów i projektów podstawowych muszą być wspólnie programowane, aby umożliwić wewnętrzny podtyp lub projekt podstawowy, aby prawidłowo uczestniczyć w delegowaniu wywołań metod i zarządzaniu liczbami odwoływań. Oznacza to, że projekt, który ma zostać zagregowany, musi być zaprogramowany w celu obsługi agregacji.

Na poniższej ilustracji przedstawiono schematową reprezentację agregacji wielopoziomowego podtypu projektu.

![Visual Studio wielopoziomowa grafika projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Agregacja wielopoziomowego podtypu projektu składa się z trzech poziomów, projektu podstawowego, który jest agregowany według podtypu projektu, a następnie dalej agregowany według zaawansowanego podtypu projektu. Na rysunku skupiono się na niektórych interfejsach obsługi, które są udostępniane w ramach architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanizmy wdrażania

Wiele podstawowych funkcji systemu projektu rozszerzonego o podtyp projektu to mechanizmy wdrażania. Podtyp projektu wpływa na mechanizmy wdrażania przez zaimplementowanie interfejsów konfiguracji (takich jak i ), które są pobierane przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> queryInterface w pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . W scenariuszu, w którym zarówno podtyp projektu, jak i zaawansowany podtyp projektu dodają różne implementacje konfiguracji, projekt podstawowy wywołuje zaawansowany `QueryInterface` podtyp projektu `IUnknown` . Jeśli podtyp projektu wewnętrznego zawiera implementację konfiguracji, o która prosi projekt podstawowy, zaawansowany podtyp projektu deleguje do implementacji dostarczonej przez podtyp projektu wewnętrznego. Jako mechanizm utrwalania stanu z jednego poziomu agregacji na inny, wszystkie poziomy podtypów projektu implementują się w celu utrwalania danych XML niezwiązanych z <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> kompilacją w plikach projektu. Aby uzyskać więcej informacji, zobacz [Persisting Data in the MSBuild Project File (Utrwalanie danych w pliku projektu MSBuild).](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md) <xref:EnvDTE80.IInternalExtenderProvider> Jest implementowane jako mechanizm pobierania rozszerzenia automatyzacji z podtypów projektu.

Na poniższej ilustracji skupiono się na implementacji rozszerzenia automatyzacji, w szczególności na obiekcie przeglądania konfiguracji projektu, używanym przez podtypy projektu do rozszerzania podstawowego systemu projektu.

![Grafika przedstawiająca automatyczne rozszerzenie VS Project Flavor](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektów mogą jeszcze bardziej rozszerzyć podstawowy system projektu, rozszerzając model obiektów automatyzacji. Są one definiowane jako część obiektu automatyzacji DTE i służą do rozszerzania obiektu Project, `ProjectItem` obiektu i `Configuration` obiektu . Aby uzyskać więcej informacji, [zobacz Rozszerzanie modelu obiektów projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregacja wielopoziomowa

Implementacja podtypu projektu, która opakowywuje podtyp projektu niższego poziomu, musi być wspólnie zaprogramowana, aby umożliwić prawidłowe działanie podtypu projektu wewnętrznego. Lista obowiązków programistycznych obejmuje:

- Implementacja podtypu projektu opakowującego podtyp wewnętrzny musi delegować do implementacji podtypu projektu wewnętrznego dla <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> metod i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- Implementacja podtypu projektu otoki musi delegować do podtypu projektu <xref:EnvDTE80.IInternalExtenderProvider> wewnętrznego. W szczególności implementacja musi pobrać ciąg nazw z podtypu projektu wewnętrznego, a następnie zsumować ciągi, które chce dodać <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> jako rozszerzenia.

- Implementacja podtypu projektu otoki musi utworzyć wystąpienia obiektu jego podtypu projektu wewnętrznego i przechowywać go jako prywatnego delegata, ponieważ tylko obiekt konfiguracji projektu podstawowego bezpośrednio wie, że istnieje obiekt konfiguracji podtypu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> otoki. Podtyp projektu zewnętrznego może początkowo wybrać interfejsy konfiguracji, które mają być obsługiwane bezpośrednio, a następnie delegować resztę do implementacji podtypu projektu wewnętrznego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfejsy obsługi

Projekt podstawowy deleguje wywołania do interfejsów obsługi dodanych przez podtyp projektu, aby rozszerzyć różne aspekty jego implementacji. Obejmuje to rozszerzanie obiektów konfiguracji projektu i różnych obiektów przeglądarki właściwości. Te interfejsy są pobierane przez wywołanie funkcji (wskaźnika do ) najbardziej zewnętrznego `QueryInterface` `punkOuter` `IUnknown` agregatora podtypu projektu.

|Interfejs|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umożliwia podtypowi projektu:<br /><br /> - Podaj implementację programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />- Kontroluj uruchamianie debugera, zezwalając podtypowi projektu na zapewnienie własnej implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />- Wyłącz ocenę wyrażeń czasu projektowania przez odpowiednią obsługę `DBGLAUNCH_DesignTimeExprEval` przypadku w jego implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umożliwia podtypowi projektu:<br /><br /> — Rozszerzenie <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> obiektu projektu w celu dodania lub usunięcia niezależnych właściwości konfiguracji projektu.<br />— Rozszerz obiekt automatyzacji projektu ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) projektu.<br /><br /> Powyższe wartości właściwości są brane z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wyliczenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umożliwia mapowanie podtypu projektu z powrotem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiektu, biorąc pod uwagę obiekt przeglądania konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umożliwia mapowanie podtypu projektu z powrotem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu lub , biorąc pod uwagę obiekt `VSITEMID` przeglądania konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umożliwia podtypowi projektu utrwalanie dowolnych danych strukturalnych XML w pliku projektu (vbproj lub csproj). Te dane nie są widoczne dla programu MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umożliwia podtypowi projektu:<br /><br /> — Dodaj nowe właściwości programu MSBuild, które mają zostać utrwalone.<br />— Usuń niepotrzebne właściwości z programu MSBuild.<br />- Zapytanie o bieżącą wartość właściwości MSBuild.<br />- Zmień bieżącą wartość właściwości MSBuild.|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
