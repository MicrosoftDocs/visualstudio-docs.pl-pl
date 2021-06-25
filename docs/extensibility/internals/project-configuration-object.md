---
title: Projekt konfiguracji obiektu | Microsoft Docs
description: Dowiedz się, jak obiekt konfiguracji projektu zarządza wyświetlaniem informacji o konfiguracji w interfejsie użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 15a999f78d017c76ee021f86d81cb611310d079d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899865"
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlaniem informacji o konfiguracji w interfejsie użytkownika.

 ![Visual Studio konfiguracji projektu](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Strony właściwości konfiguracji projektu

 Dostawca konfiguracji projektu zarządza konfiguracjami projektu. Środowisko i inne pakiety, aby uzyskać dostęp do konfiguracji projektu i je pobrać, wywołaj interfejsy dołączone do obiektu Project Configuration Provider.

> [!NOTE]
> Nie można programowo tworzyć ani edytować plików konfiguracji rozwiązania. Należy użyć `DTE.SolutionBuilder` . Aby [uzyskać więcej informacji,](../../extensibility/internals/solution-configuration.md) zobacz Konfiguracja rozwiązania.

 Aby opublikować nazwę wyświetlaną, która ma być używana w interfejsie użytkownika konfiguracji, projekt powinien implementować element <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Środowisko wywołuje element , który zwraca listę wskaźników, których można użyć do uzyskania nazw wyświetlanych dla informacji o konfiguracji i platformie, które mają być wyświetlane w <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> `IVsCfg` interfejsie użytkownika środowiska. Aktywna konfiguracja i platforma są określane przez konfigurację projektu przechowywaną w aktywnej konfiguracji rozwiązania. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> może służyć do pobierania aktywnej konfiguracji projektu.

 Obiekt można opcjonalnie zaimplementować w obiekcie z obiektem , aby umożliwić pobranie obiektu na podstawie nazwy konfiguracji projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` kanonicznego.

 Innym sposobem zapewnienia środowisku i innym projektom dostępu do konfiguracji projektu jest zapewnienie implementacji metody zwracania jednego lub `IVsCfgProvider2::GetCfgs` większej liczby obiektów konfiguracji. Projekty mogą również implementować , który dziedziczy z , a tym samym z , w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> celu zapewnienia informacji specyficznych dla `IVsProjectCfg` `IVsCfg` konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> Obsługuje platformy oraz funkcje dodawania, usuwania i zmieniania nazw konfiguracji projektu.

> [!NOTE]
> Ponieważ Visual Studio nie jest już ograniczony do dwóch typów konfiguracji, kod, który przetwarza konfiguracje, nie powinien być pisany z założeniami co do liczby konfiguracji ani nie powinien być napisany z założeniem, że projekt, który ma tylko jedną konfigurację, musi być albo debugowanie, albo sprzedaż detaliczna. Powoduje to użycie i <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> przestarzałe.

 Wywołanie `QueryInterface` dla obiektu zwróconego z pobiera `IVsGetCfgProvider::GetCfgProvider` `IVsCfgProvider2` . Jeśli nie zostanie znaleziony przez wywołanie funkcji w obiekcie projektu, możesz uzyskać dostęp do obiektu dostawcy konfiguracji, wywołując obiekt przeglądarki głównej hierarchii dla obiektu zwróconego dla obiektu `IVsGetCfgProvider` `QueryInterface` `IVsProject3` `QueryInterface` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` lub `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` przez wskaźnik do dostawcy konfiguracji zwróconego dla .

 `IVsProjectCfg2` Przede wszystkim zapewnia dostęp do obiektów zarządzania kompilacją, debugowaniem i wdrażaniem oraz umożliwia projektom swobodę grupowania danych wyjściowych. Metody i mogą służyć do implementowania w celu zarządzania procesem kompilacji oraz wskaźników dla grup `IVsProjectCfg` `IVsProjectCfg2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wyjściowych konfiguracji.

 Projekt musi zwrócić taką samą liczbę grup dla każdej konfiguracji, która jest przez niego wspierana, mimo że liczba danych wyjściowych zawartych w grupie może się różnić w zależności od konfiguracji. Grupy muszą również mieć te same informacje o identyfikatorze (nazwa kanoniczna, nazwa wyświetlana i informacje o grupie) od konfiguracji do konfiguracji w projekcie. Aby uzyskać więcej informacji, zobacz [Project Configuration for Output (Konfiguracja projektu dla danych wyjściowych).](../../extensibility/internals/project-configuration-for-output.md)

 Aby włączyć debugowanie, konfiguracje powinny implementować . <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg` to opcjonalny interfejs implementowany przez projekty w celu umożliwienia debugerowi uruchamiania konfiguracji i zaimplementowany w obiekcie konfiguracji za pomocą funkcji `IVsCfg` i `IVsProjectCfg` . Środowisko wywołuje ją, gdy użytkownik zdecyduje się uruchomić debuger, naciskając klawisz F5.

 `ISpecifyPropertyPages` i `IDispatch` są używane w połączeniu ze stronami właściwości do pobierania i wyświetlania użytkownikowi informacji zależnych od konfiguracji. Aby uzyskać więcej informacji, zobacz [Strony właściwości](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
- [Strony właściwości](../../extensibility/internals/property-pages.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
