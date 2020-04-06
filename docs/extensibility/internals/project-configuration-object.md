---
title: Obiekt konfiguracji projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706654"
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlaniem informacji o konfiguracji do interfejsu użytkownika.

 ![Konfiguracja projektu programu Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Strony właściwości konfiguracji projektu

 Dostawca konfiguracji projektu zarządza konfiguracjami projektu. Środowisko i inne pakiety, aby uzyskać dostęp do i pobrać informacje o konfiguracjach projektu, wywołaj interfejsy dołączone do obiektu dostawca konfiguracji projektu.

> [!NOTE]
> Nie można programowo tworzyć ani edytować plików konfiguracyjnych rozwiązania. Należy użyć `DTE.SolutionBuilder`pliku . Aby uzyskać więcej informacji, zobacz [Konfiguracja rozwiązania.](../../extensibility/internals/solution-configuration.md)

 Aby opublikować nazwę wyświetlaną, która ma być używana <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>w interfejsie użytkownika konfiguracji, projekt powinien zaimplementować program . Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, który zwraca `IVsCfg` listę wskaźników, które można użyć, aby uzyskać nazwy wyświetlane dla konfiguracji i informacji platformy, które mają być wymienione w interfejsie użytkownika środowiska. Aktywna konfiguracja i platforma są określane przez konfigurację projektu przechowywaną w konfiguracji aktywnego rozwiązania. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> może służyć do pobierania aktywnej konfiguracji projektu.

 Obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> może być opcjonalnie zaimplementowany na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obiekcie z obiektem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` aby umożliwić pobranie obiektu na podstawie nazwy konfiguracji projektu kanonicznego.

 Innym sposobem zapewnienia środowiska i innych projektów z dostępem do konfiguracji projektu `IVsCfgProvider2::GetCfgs` jest dla projektów, aby zapewnić implementację metody zwracania jednego lub więcej obiektów konfiguracji. Projekty mogą również <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>realizować , `IVsProjectCfg` które dziedziczą, a tym samym z `IVsCfg`, w celu dostarczenia informacji specyficznych dla konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>obsługuje platformy i funkcje dodawania, usuwania i zmiany nazwy konfiguracji projektu.

> [!NOTE]
> Ponieważ visual studio nie jest już ograniczona do dwóch typów konfiguracji, kod, który przetwarza konfiguracje nie powinny być zapisywane z założeniami o liczbie konfiguracji, ani nie powinny być zapisywane przy założeniu, że projekt, który ma tylko jedną konfigurację jest koniecznie debugowania lub sieci sprzedaży detalicznej. To sprawia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> że <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> korzystanie z i przestarzałe.

 Wywołanie `QueryInterface` obiektu zwróconego z`IVsGetCfgProvider::GetCfgProvider` pobiera `IVsCfgProvider2`. Jeśli `IVsGetCfgProvider` nie zostanie `QueryInterface` znaleziony `IVsProject3` przez wywołanie obiektu projektu, można `QueryInterface` uzyskać dostęp do obiektu dostawcy konfiguracji, `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`wywołując obiekt głównej przeglądarki hierarchii `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`dla obiektu zwróconego dla obiektu lub za pomocą wskaźnika do dostawcy konfiguracji zwróconego dla .

 `IVsProjectCfg2`przede wszystkim zapewnia dostęp do obiektów zarządzania kompilacji, debugowania i wdrażania i umożliwia projektom swobodę grupowania wyjść. Metody `IVsProjectCfg` i `IVsProjectCfg2` mogą być używane <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> do zaimplementowania do zarządzania procesem kompilacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wskaźniki dla grup wyjściowych konfiguracji.

 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji, która obsługuje, nawet jeśli liczba wyjść zawartych w grupie może się różnić w zależności od konfiguracji. Grupy muszą mieć również te same informacje o identyfikatorze (nazwa kanoniczna, nazwa wyświetlana i informacje o grupach) od konfiguracji do konfiguracji w projekcie. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

 Aby włączyć debugowanie, konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>powinny implementować . `IVsDebuggableProjectCfg`jest opcjonalnym interfejsem implementowanym przez projekty, aby umożliwić debugerowi uruchomienie `IVsCfg` konfiguracji `IVsProjectCfg`i jest implementowany na obiekcie konfiguracyjnym z i . Środowisko wywołuje go, gdy użytkownik zdecyduje się uruchomić debuger, naciskając klawisz F5.

 `ISpecifyPropertyPages`i `IDispatch` są używane w połączeniu ze stronami właściwości do pobierania i wyświetlania informacji zależnych od konfiguracji dla użytkownika. Aby uzyskać więcej informacji, zobacz [Strony właściwości](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
- [Strony właściwości](../../extensibility/internals/property-pages.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
