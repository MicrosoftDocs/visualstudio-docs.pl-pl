---
title: Obiekt konfiguracji projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e25e2f2359cabff9a4e95a7d64d2f0846df8f49f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631747"
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlanie informacji o konfiguracji w interfejsie użytkownika.

 ![Konfiguracja projektu usługi Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") stron właściwości konfiguracji projektu

 Dostawca konfiguracji projektu zarządza konfiguracje projektu. Środowisko i inne pakiety w celu uzyskania dostępu do i pobierania informacji o konfiguracji projektu, wywołania interfejsów dołączony do obiektu dostawcy konfiguracji projektu.

> [!NOTE]
>  Nie można utworzyć lub edytować pliki konfiguracji rozwiązania programowe. Należy użyć `DTE.SolutionBuilder`. Zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md) Aby uzyskać więcej informacji.

 Aby opublikować nazwę wyświetlaną, które zostaną użyte w interfejsie użytkownika konfiguracji, należy zaimplementować projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, które zwraca listę `IVsCfg` wskaźników, które służą do pobierania nazw wyświetlanych informacji Konfiguracja i platforma był wyświetlany w interfejsie użytkownika środowiska. Aktywna konfiguracja i platforma są określane przez konfigurację projektu w aktywnej konfiguracji rozwiązania. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Metoda może służyć do pobierania Konfiguracja aktywnego projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Obiektu opcjonalnie mogą zostać zaimplementowane na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obiekt z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> obiektu, aby możliwe było pobieranie `IVsProjectCfg2` obiektu na podstawie projektu canonical konfiguracji nazwy.

 Innym sposobem na zapewnienie dostępu do konfiguracji projektu środowiska i innych projektów jest dla projektów dostarczać implementację `IVsCfgProvider2::GetCfgs` metodę, aby zwrócić co najmniej jednego obiektu konfiguracji. Projekty mogą także implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, który dziedziczy z `IVsProjectCfg` i tym samym `IVsCfg`w celu zapewnienia informacji specyficznych dla konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obsługuje platformy i funkcje, dodawanie, usuwanie i zmienianie nazw konfiguracji projektu.

> [!NOTE]
>  Od programu Visual Studio nie jest już ograniczona do dwóch typów konfiguracji ani kodu, który przetwarza konfiguracje nie powinien być zapisywany z założenia dotyczące liczby konfiguracje nie powinien on być zapisywany przy założeniu, że projekt, który ma tylko jeden Konfiguracja jest zawsze debugowania lub wersji detalicznej. To sprawia, że użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> przestarzały.

 Wywoływanie `QueryInterface` na obiekt zwrócony z`IVsGetCfgProvider::GetCfgProvider` pobiera `IVsCfgProvider2`. Jeśli `IVsGetCfgProvider` nie zostanie znaleziony, wywołując `QueryInterface` na `IVsProject3` obiektu projektu, można uzyskać dostęp do obiektu dostawcy konfiguracji przez wywołanie metody `QueryInterface` obiektu przeglądarki głównego hierarchii dla obiektu zwróconego do `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, lub za pomocą wskaźnik do dostawcę konfiguracji, który został zwrócony dla `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` przede wszystkim zapewnia dostęp do kompilowania, debugowania i wdrażania obiektów zarządzania i umożliwia projektów swobody grupy danych wyjściowych. Metody `IVsProjectCfg` i `IVsProjectCfg2` może służyć do implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> do zarządzania procesem kompilacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wskaźniki dla grupy danych wyjściowych konfiguracji.

 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji obsługującego nawet, jeśli liczba wyjść zawarty w grupie będzie zależeć od konfiguracja. Grupy musi mieć również te same informacje identyfikatora (nazwy kanonicznej, nazwę wyświetlaną i informacje o grupie) z Konfiguracja w projekcie. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

 Aby włączyć debugowanie, powinny implementować konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` jest opcjonalny interfejs implementowany przez projektów, aby umożliwić debuger do uruchomienia konfiguracji i implementacji dla obiektu konfiguracji o `IVsCfg` i `IVsProjectCfg`. Środowisko wywołuje je, gdy użytkownik wybiera uruchomić debuger, naciskając klawisz F5.

 `ISpecifyPropertyPages` i `IDispatch` są używane w połączeniu z strony właściwości można pobierać i wyświetlać informacje zależne od konfiguracji do użytkownika. Aby uzyskać więcej informacji, zobacz [stron właściwości](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
- [Strony właściwości](../../extensibility/internals/property-pages.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)