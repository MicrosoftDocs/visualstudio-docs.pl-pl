---
title: Obiekt konfiguracji projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725837"
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlaniem informacji konfiguracyjnych w interfejsie użytkownika.

 ![Konfiguracja projektu programu Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Strony właściwości konfiguracji projektu

 Dostawca konfiguracji projektu zarządza konfiguracją projektu. Środowisko i inne pakiety, aby uzyskać dostęp do i pobrać informacje o konfiguracjach projektu, wywołaj interfejsy dołączone do obiektu dostawcy konfiguracji projektu.

> [!NOTE]
> Nie można programowo tworzyć ani edytować plików konfiguracji rozwiązania. Musisz użyć `DTE.SolutionBuilder`. Aby uzyskać więcej informacji, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md) .

 Aby opublikować nazwę wyświetlaną, która ma być używana w interfejsie użytkownika konfiguracji, projekt powinien implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, które zwraca listę wskaźników `IVsCfg`, których można użyć w celu uzyskania nazw wyświetlanych informacji o konfiguracji i platformie, które mają być wyświetlane w interfejsie użytkownika środowiska. Aktywna konfiguracja i platforma są określane przez konfigurację projektu przechowywaną w aktywnej konfiguracji rozwiązania. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> może służyć do pobierania aktywnej konfiguracji projektu.

 Obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> można opcjonalnie zaimplementować na obiekcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> z obiektem <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>, aby umożliwić Pobieranie obiektu `IVsProjectCfg2` na podstawie nazwy konfiguracji projektu kanonicznego.

 Innym sposobem zapewnienia środowiska i innych projektów z dostępem do konfiguracji projektu jest projekty, aby zapewnić implementację metody `IVsCfgProvider2::GetCfgs` w celu zwrócenia co najmniej jednego obiektu konfiguracji. Projekty mogą również zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, które dziedziczą z `IVsProjectCfg` i w związku z tym z `IVsCfg`, aby zapewnić informacje specyficzne dla konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obsługuje platformy i możliwości dodawania, usuwania i zmieniania nazw konfiguracji projektu.

> [!NOTE]
> Ponieważ program Visual Studio nie jest już ograniczony do dwóch typów konfiguracji, kod, który przetwarza konfiguracje nie należy zapisywać z założeniami dotyczącymi liczby konfiguracji, ani nie powinien być zapisany z założeniem, że projekt ma tylko jeden Konfiguracja jest konieczna do debugowania lub sprzedaży detalicznej. Dzięki temu korzystanie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> przestarzałe.

 Wywołanie `QueryInterface` na obiekcie zwróconym przez `IVsGetCfgProvider::GetCfgProvider` pobiera `IVsCfgProvider2`. Jeśli `IVsGetCfgProvider` nie zostanie znaleziona przez wywołanie `QueryInterface` w obiekcie projektu `IVsProject3`, można uzyskać dostęp do obiektu dostawcy konfiguracji przez wywołanie `QueryInterface` obiektu przeglądarki głównej hierarchii dla obiektu zwróconego dla `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` lub przez wskaźnik do konfiguracji dostawca zwrócił `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` zapewnia dostęp do obiektów do kompilowania, debugowania i zarządzania wdrożenia, a także umożliwia projekty swobodne grupowanie danych wyjściowych. Metody `IVsProjectCfg` i `IVsProjectCfg2` mogą służyć do implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> do zarządzania procesem kompilacji oraz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wskaźników dla grup wyjściowych konfiguracji.

 Projekt musi zwracać tę samą liczbę grup dla każdej konfiguracji, która obsługuje, nawet jeśli liczba danych wyjściowych zawartych w grupie może się różnić od konfiguracji do konfiguracji. Grupy muszą mieć także takie same informacje o identyfikatorze (nazwa kanoniczna, nazwa wyświetlana i informacje o grupie) z konfiguracji do konfiguracji w ramach projektu. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

 Aby włączyć debugowanie, konfiguracje powinny implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` to opcjonalny interfejs zaimplementowany przez projekty umożliwiający debugerowi uruchomienie konfiguracji i jest zaimplementowany w obiekcie Configuration z `IVsCfg` i `IVsProjectCfg`. Środowisko wywołuje je, gdy użytkownik zdecyduje się na uruchomienie debugera, naciskając klawisz F5.

 `ISpecifyPropertyPages` i `IDispatch` są używane w połączeniu ze stronami właściwości do pobierania i wyświetlania informacji zależnych od konfiguracji użytkownikowi. Aby uzyskać więcej informacji, zobacz [strony właściwości](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Zobacz także
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
- [Strony właściwości](../../extensibility/internals/property-pages.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)