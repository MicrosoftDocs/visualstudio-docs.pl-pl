---
title: Konfiguracja rozwiązania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705375"
---
# <a name="solution-configuration"></a>Konfiguracja rozwiązania
Konfiguracje rozwiązań przechowują właściwości na poziomie rozwiązania. Kierują one zachowanie klawisza **Start** (F5) i poleceń **kompilacji** . Domyślnie te polecenia kompilują i uruchamiają konfigurację debugowania. Oba polecenia są wykonywane w kontekście konfiguracji rozwiązania. Oznacza to, że użytkownik może oczekiwać, że od F5 rozpocznie się i skompiluje dowolne aktywne rozwiązanie za pośrednictwem ustawień. Środowisko jest przeznaczone do optymalizowania rozwiązań, a nie projektów, gdy chodzi o Kompilowanie i uruchamianie.

 Standardowy pasek narzędzi programu Visual Studio zawiera przycisk Start i listę rozwijaną konfiguracji rozwiązania po prawej stronie przycisku Start. Ta lista umożliwia użytkownikom wybranie konfiguracji, która ma zostać uruchomiona po naciśnięciu klawisza F5, utworzenie własnych konfiguracji rozwiązań lub edytowanie istniejącej konfiguracji.

> [!NOTE]
> Brak interfejsów rozszerzalności do tworzenia lub edytowania konfiguracji rozwiązania. Musisz użyć `DTE.SolutionBuild` . Istnieją jednak interfejsy API rozszerzalności do zarządzania kompilacją rozwiązania. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Oto jak można zaimplementować konfiguracje rozwiązań obsługiwane przez typ projektu:

- Projekt

   Wyświetla nazwy projektów znalezionych w bieżącym rozwiązaniu.

- Konfigurowanie

   Aby zapewnić listę konfiguracji obsługiwanych przez typ projektu i wyświetlane na stronach właściwości, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   W kolumnie konfiguracja zostanie wyświetlona nazwa konfiguracji projektu do skompilowania w tej konfiguracji rozwiązania i zostanie wyświetlona lista wszystkich konfiguracji projektu po kliknięciu przycisku strzałki. Środowisko wywołuje metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> Aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda wskazuje, że projekt obsługuje edycję konfiguracji, w nagłówku konfiguracji są również wyświetlane opcje nowe lub Edycja. Każdy z tych opcji uruchamia okna dialogowe, które wywołują metody `IVsCfgProvider2` interfejsu w celu edycji konfiguracji projektu.

   Jeśli projekt nie obsługuje konfiguracji, w kolumnie konfiguracja jest wyświetlana wartość Brak i jest ona wyłączona.

- Platforma

   Wyświetla platformę, dla której kompilacja wybranej konfiguracji projektu i wyświetla listę wszystkich dostępnych platform dla projektu po kliknięciu przycisku strzałki. Środowisko wywołuje metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> Aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda wskazuje, że projekt obsługuje edycję platformy, w obszarze nagłówek platformy są również wyświetlane opcje nowe lub Edycja. Każdy z tych opcji uruchamia okna dialogowe, które wywołują `IVsCfgProvider2` metody, aby edytować dostępne platformy projektu.

   Jeśli projekt nie obsługuje platform, kolumna platformy dla tego projektu nie wyświetla i jest wyłączona.

- Kompilacja

   Określa, czy projekt został skompilowany przez bieżącą konfigurację rozwiązania. Niewybrane projekty nie są kompilowane, gdy polecenia kompilacji na poziomie rozwiązania są wywoływane pomimo wszelkich zawartych w nim zależności projektu. Projekty, które nie zostały wybrane do skompilowania, są nadal objęte debugowaniem, uruchamianiem, pakowaniem i wdrażaniem rozwiązania.

- Wdrażanie

   Określa, czy projekt zostanie wdrożony, gdy polecenia Uruchom lub Wdróż zostaną użyte z wybraną konfiguracją kompilacji rozwiązania. Pole wyboru dla tego pola będzie dostępne, jeśli projekt obsługuje wdrażanie przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> obiekcie.

  Po dodaniu nowej konfiguracji rozwiązania użytkownik może wybrać ją z listy rozwijanej Konfiguracja rozwiązania na pasku narzędzi Standardowy, aby skompilować i/lub uruchomić tę konfigurację.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
