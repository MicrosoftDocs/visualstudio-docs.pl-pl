---
title: Obiekt konfiguracji projektu | Microsoft Docs
description: Dowiedz się, jak obiekt konfiguracji projektu zarządza wyświetlaniem informacji konfiguracyjnych w interfejsie użytkownika.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4d91f640abc4fd91b68341e825b312b8bfb0d6f6
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875495"
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlaniem informacji konfiguracyjnych w interfejsie użytkownika.

 ![Konfiguracja projektu programu Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Strony właściwości konfiguracji projektu

 Dostawca konfiguracji projektu zarządza konfiguracją projektu. Środowisko i inne pakiety, aby uzyskać dostęp do i pobrać informacje o konfiguracjach projektu, wywołaj interfejsy dołączone do obiektu dostawcy konfiguracji projektu.

> [!NOTE]
> Nie można programowo tworzyć ani edytować plików konfiguracji rozwiązania. Musisz użyć `DTE.SolutionBuilder` . Aby uzyskać więcej informacji, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md) .

 Aby opublikować nazwę wyświetlaną, która ma być używana w interfejsie użytkownika konfiguracji, należy wdrożyć projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , które zwraca listę wskaźników, których `IVsCfg` można użyć w celu uzyskania nazw wyświetlanych informacji o konfiguracji i platformie, które mają być wyświetlane w interfejsie użytkownika środowiska. Aktywna konfiguracja i platforma są określane przez konfigurację projektu przechowywaną w aktywnej konfiguracji rozwiązania. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>Metoda może służyć do pobierania aktywnej konfiguracji projektu.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Obiekt można opcjonalnie zaimplementować na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obiekcie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> obiektem, aby umożliwić pobieranie `IVsProjectCfg2` obiektu na podstawie nazwy konfiguracji projektu kanonicznego.

 Innym sposobem zapewnienia środowiska i innych projektów z dostępem do konfiguracji projektu jest projekty, aby zapewnić implementację `IVsCfgProvider2::GetCfgs` metody w celu zwrócenia co najmniej jednego obiektu konfiguracji. Projekty mogą również zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , które dziedziczą z `IVsProjectCfg` , a tym samym z `IVsCfg` , aby zapewnić informacje specyficzne dla konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obsługuje platformy i funkcje umożliwiające dodawanie, usuwanie i zmienianie nazw konfiguracji projektu.

> [!NOTE]
> Ponieważ program Visual Studio nie jest już ograniczony do dwóch typów konfiguracji, kod, który przetwarza konfiguracje nie powinien być zapisany z założeniami dotyczącymi liczby konfiguracji, ani nie powinien być zapisany z założeniem, że projekt, który ma tylko jedną konfigurację, musi być zarówno debugowaniem, jak i detalicznym. Dzięki temu korzystanie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> przestarzałe.

 Wywoływanie `QueryInterface` obiektu zwróconego z `IVsGetCfgProvider::GetCfgProvider` pobierania `IVsCfgProvider2` . Jeśli `IVsGetCfgProvider` nie można go znaleźć przez wywołanie `QueryInterface` `IVsProject3` obiektu projektu, można uzyskać dostęp do obiektu dostawcy konfiguracji, wywołując `QueryInterface` obiekt głównej przeglądarki hierarchii dla obiektu zwróconego przez `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` lub przez wskaźnik do dostawcy konfiguracji zwróconego przez `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` przede wszystkim zapewnia dostęp do obiektów do kompilowania, debugowania i zarządzania wdrożenia oraz umożliwia projekty swobodne grupowanie danych wyjściowych. Metody `IVsProjectCfg` i `IVsProjectCfg2` mogą być używane do wdrożenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> w celu zarządzania procesem kompilacji oraz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wskaźniki dla grup wyjściowych konfiguracji.

 Projekt musi zwracać tę samą liczbę grup dla każdej konfiguracji, która obsługuje, nawet jeśli liczba danych wyjściowych zawartych w grupie może się różnić od konfiguracji do konfiguracji. Grupy muszą mieć także takie same informacje o identyfikatorze (nazwa kanoniczna, nazwa wyświetlana i informacje o grupie) z konfiguracji do konfiguracji w ramach projektu. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).

 Aby włączyć debugowanie, należy zaimplementować konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` jest interfejsem opcjonalnym zaimplementowanym przez projekty, aby umożliwić debugerowi uruchomienie konfiguracji i jest zaimplementowany w obiekcie Configuration z `IVsCfg` i `IVsProjectCfg` . Środowisko wywołuje je, gdy użytkownik zdecyduje się na uruchomienie debugera, naciskając klawisz F5.

 `ISpecifyPropertyPages` i `IDispatch` są używane w połączeniu ze stronami właściwości do pobierania i wyświetlania informacji zależnych od konfiguracji użytkownikowi. Aby uzyskać więcej informacji, zobacz [strony właściwości](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
- [Strony właściwości](../../extensibility/internals/property-pages.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
