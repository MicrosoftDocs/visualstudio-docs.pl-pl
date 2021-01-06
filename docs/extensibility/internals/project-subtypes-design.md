---
title: Projekt podtypów projektu | Microsoft Docs
description: Dowiedz się, jak podtypy projektu umożliwiają pakietów VSPackage poszerzanie projektów opartych na Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9342d8f9f045eec2036c65a3ed2d823dfb4a7e42
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877432"
---
# <a name="project-subtypes-design"></a>Projektowanie podtypów projektów

Podtypy projektu umożliwiają pakietów VSPackage poszerzanie projektów opartych na Microsoft Build Engine (MSBuild). Użycie agregacji pozwala na wielokrotne użycie zbiorczego zarządzanego systemu projektu, który w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dalszym ciągu nadal dostosowuje zachowanie dla konkretnego scenariusza.

 W poniższych tematach szczegółowo opisano podstawowe projektowanie i implementację podtypów projektu:

- Projekt podtypu projektu.

- Agregacja na wiele poziomów.

- Interfejsy pomocnicze.

## <a name="project-subtype-design"></a>Projekt podtypu projektu

Inicjowanie podtypu projektu jest osiągane poprzez agregowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektów głównych i <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Ta agregacja umożliwia podtype projektu przesłonięcie lub zwiększenie większości możliwości projektu podstawowego. Podtypy projektu uzyskują pierwszą szansę na obsługę właściwości przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> poleceń, a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> i i zarządzania elementami projektu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Podtypy projektu mogą również stanowić:

- Obiekty konfiguracji projektu.

- Obiekty zależne od konfiguracji.

- Obiekty przeglądania niezależne od konfiguracji.

- Obiekty automatyzacji projektu.

- Kolekcje właściwości automatyzacji projektu.

Aby uzyskać więcej informacji na temat rozszerzalności według podtypów projektów, zobacz [właściwości i metody rozszerzone według podtypów projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Pliki zasad

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Środowisko zawiera przykład rozszerzania podstawowego systemu projektu z podtypem projektu w jego implementacji. Plik zasad umożliwia kształtowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska przez Zarządzanie funkcjami, które zawierają Eksplorator rozwiązań, okno dialogowe **Dodawanie projektu** , okno dialogowe **Dodawanie nowego elementu** i okno dialogowe **Właściwości** . Podtyp zasad przesłania i rozszerza te funkcje za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementacji.

### <a name="aggregation-mechanism"></a>Mechanizm agregacji

Mechanizm agregacji typu projektu środowiska obsługuje wiele poziomów agregacji, co pozwala na implementację zaawansowanego podtypu przez dalsze podzbiorowanie projektu. Ponadto obiekty pomocnicze podtypu projektu, takie jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , są zaprojektowane tak, aby zezwalały na wiele poziomów warstw. W utrzymaniu z ograniczeniami reguł agregacji modelu COM i modelu COM, podtypy projektów i projekty podstawowe muszą być programowane wspólnie, aby umożliwić, że wewnętrzny podtyp lub projekt podstawowy prawidłowo uczestniczy w delegowaniu wywołań metod i zarządzaniu licznikami odwołań. Oznacza to, że projekt, który ma zostać zagregowany, musi być zaprogramowany do obsługi agregacji.

Poniższa ilustracja przedstawia schematyczną reprezentację agregacji wielopoziomowego typu projektu.

![Wieloprojectflavorowa grafika programu Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Agregacja podtypu projektu wielopoziomowego składa się z trzech poziomów, projektu podstawowego, który jest agregowany przez podtyp projektu, a następnie agregowany przez zaawansowany podtyp projektu. Rysunek koncentruje się na niektórych interfejsach pomocniczych, które są dostarczane jako część [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektury podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanizmy wdrażania

Między wieloma podstawowymi funkcjami systemu projektu rozszerzonymi przez podtyp projektu są mechanizmy wdrażania. Podtyp projektu ma wpływ na mechanizmy wdrażania przez implementację interfejsów konfiguracji (takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ), które są pobierane przez wywołanie polecenia QueryInterface w systemie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . W scenariuszu, w którym zarówno podtyp projektu, jak i zaawansowany podtyp projektu dodają różne implementacje konfiguracji, projekt podstawowy wywołuje `QueryInterface` dla zaawansowanego podtypu projektu `IUnknown` . Jeśli podtyp projektu wewnętrznego zawiera implementację konfiguracji, z którą żąda projekt podstawowy, do implementacji jest zaawansowany podtyp projektu, który został dostarczony przez wewnętrzny podtyp projektu. Jako mechanizm utrwalania stanu z jednego poziomu agregacji na inny, wszystkie poziomy podtypów projektu implementują <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> w celu utrwalenia niezwiązanych z nimi danych XML w plikach projektu. Aby uzyskać więcej informacji, zobacz [utrwalanie danych w pliku projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> jest zaimplementowany jako mechanizm do pobierania rozszerzeń automatyzacji z podtypów projektu.

Na poniższej ilustracji przedstawiono implementację usługi Automation Extender, obiekt przeglądania konfiguracji projektu w szczególności używany przez podtypy projektu w celu rozszerzenia podstawowego systemu projektu.

![Grafika przedstawiająca rozszerzenie Autorozszerzanie projektu programu VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektu mogą rozszerzać podstawowy system projektu, rozszerzając model obiektów automatyzacji. Są one definiowane jako część obiektu automatyzacji DTE i służą do rozbudowywania obiektu projektu, `ProjectItem` obiektu i `Configuration` obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie modelu obiektów projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregacja na wiele poziomów

Implementacja podtypu projektu, która otacza podtyp projektu niższego poziomu, musi być programowana wspólnie, aby umożliwić prawidłowe działanie podtypu projektu wewnętrznego. Lista obowiązków związanych z programowaniem obejmuje:

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Implementacja podtypu projektu, który otacza podtyp wewnętrzny, musi delegować do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementacji wewnętrznego podtypu projektu dla obu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metod i.

- <xref:EnvDTE80.IInternalExtenderProvider>Implementacja podtypu projektu otoki musi być delegatem do tego wewnętrznego podtypu projektu. W szczególności implementacja programu <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> wymaga pobrania ciągu nazw z wewnętrznego podtypu projektu, a następnie łączenia ciągów, które chce dodać jako rozszerzeń.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Implementacja podtypu projektu otoki musi utworzyć wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> obiektu wewnętrznego podtypu projektu i przechowywać go jako delegat prywatny, ponieważ tylko obiekt konfiguracji projektu bazowego projektu, że istnieje obiekt konfiguracji podtypu projektu otoki. Podtyp projektu zewnętrznego może początkowo wybrać interfejsy konfiguracji, które chcą obsłużyć bezpośrednio, a następnie delegować resztę do implementacji wewnętrznego podtypu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfejsy pomocnicze

Projekt podstawowy deleguje wywołania do obsługi interfejsów dodanych przez podtyp projektu, aby zwiększyć różne aspekty jego implementacji. Obejmuje to rozszerzanie obiektów konfiguracji projektu i różnych obiektów przeglądarki właściwości. Te interfejsy są pobierane przez wywoływanie `QueryInterface` `punkOuter` (wskaźnik do `IUnknown` ) najbardziej zewnętrznego agregatora podtypu projektu.

|Interfejs|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umożliwia podtype projektu:<br /><br /> -Podaj implementację programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />— Kontrolowanie uruchamiania debugera przez umożliwienie podtypu projektu w celu zapewnienia własnej implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />— Wyłącz obliczanie wyrażeń czasu projektowania, odpowiednio obsługując `DBGLAUNCH_DesignTimeExprEval` przypadek w jego implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umożliwia podtype projektu:<br /><br /> -Rozwiń <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> projekt, aby dodać lub usunąć niezależne właściwości konfiguracji projektu.<br />-Rozwiń obiekt automatyzacji projektu ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) projektu.<br /><br /> Powyższe wartości właściwości są pobierane z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wyliczenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umożliwia podtype projektu zamapowanie z powrotem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiektu, w którym znajduje się obiekt przeglądania konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umożliwia podtype projektu odwzorowanie z powrotem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu lub `VSITEMID` obiekt, w którym znajduje się obiekt przeglądania konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umożliwia podtype projektu utrwalanie dowolnych danych strukturalnych XML do pliku projektu (. vbproj lub. csproj). Te dane nie są widoczne dla programu MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umożliwia podtype projektu:<br /><br /> -Dodaj nowe właściwości programu MSBuild, które mają zostać utrwalone.<br />-Usuń niepotrzebne właściwości z programu MSBuild.<br />-Zapytanie dla bieżącej wartości właściwości programu MSBuild.<br />— Zmień bieżącą wartość właściwości programu MSBuild.|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
