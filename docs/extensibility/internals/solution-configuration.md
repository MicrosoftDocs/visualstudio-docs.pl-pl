---
title: Konfiguracja rozwiązania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243af2549862f1d29c44ba5bfc3060d87d5c6f85
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723835"
---
# <a name="solution-configuration"></a>Konfiguracja rozwiązania
Konfiguracje rozwiązań przechowują właściwości na poziomie rozwiązania. Kierują one zachowanie klawisza **Start** (F5) i poleceń **kompilacji** . Domyślnie te polecenia kompilują i uruchamiają konfigurację debugowania. Oba polecenia są wykonywane w kontekście konfiguracji rozwiązania. Oznacza to, że użytkownik może oczekiwać, że od F5 rozpocznie się i skompiluje dowolne aktywne rozwiązanie za pośrednictwem ustawień. Środowisko jest przeznaczone do optymalizowania rozwiązań, a nie projektów, gdy chodzi o Kompilowanie i uruchamianie.

 Standardowy pasek narzędzi programu Visual Studio zawiera przycisk Start i listę rozwijaną konfiguracji rozwiązania po prawej stronie przycisku Start. Ta lista umożliwia użytkownikom wybranie konfiguracji, która ma zostać uruchomiona po naciśnięciu klawisza F5, utworzenie własnych konfiguracji rozwiązań lub edytowanie istniejącej konfiguracji.

> [!NOTE]
> Brak interfejsów rozszerzalności do tworzenia lub edytowania konfiguracji rozwiązania. Musisz użyć `DTE.SolutionBuilder`. Istnieją jednak interfejsy API rozszerzalności do zarządzania kompilacją rozwiązania. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Oto jak można zaimplementować konfiguracje rozwiązań obsługiwane przez typ projektu:

- Projekt

   Wyświetla nazwy projektów znalezionych w bieżącym rozwiązaniu.

- Konfiguracja

   Aby zapewnić listę konfiguracji obsługiwanych przez typ projektu i wyświetlane na stronach właściwości, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.

   W kolumnie konfiguracja zostanie wyświetlona nazwa konfiguracji projektu do skompilowania w tej konfiguracji rozwiązania i zostanie wyświetlona lista wszystkich konfiguracji projektu po kliknięciu przycisku strzałki. Środowisko wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>, aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda wskazuje, że projekt obsługuje edycję konfiguracji, w nagłówku konfiguracji są również wyświetlane opcje nowe lub Edycja. Każdy z tych opcji uruchamia okna dialogowe, które wywołują metody interfejsu `IVsCfgProvider2`, aby edytować konfiguracje projektu.

   Jeśli projekt nie obsługuje konfiguracji, w kolumnie konfiguracja jest wyświetlana wartość Brak i jest ona wyłączona.

- Platforma

   Wyświetla platformę, dla której kompilacja wybranej konfiguracji projektu i wyświetla listę wszystkich dostępnych platform dla projektu po kliknięciu przycisku strzałki. Środowisko wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>, aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> Metoda wskazuje, że projekt obsługuje edycję platformy, w obszarze nagłówek platformy są również wyświetlane opcje nowe lub Edycja. Każdy z tych opcji uruchamia okna dialogowe, które wywołują `IVsCfgProvider2` metody, aby edytować dostępne platformy projektu.

   Jeśli projekt nie obsługuje platform, kolumna platformy dla tego projektu nie wyświetla i jest wyłączona.

- Kompilacja

   Określa, czy projekt został skompilowany przez bieżącą konfigurację rozwiązania. Niewybrane projekty nie są kompilowane, gdy polecenia kompilacji na poziomie rozwiązania są wywoływane pomimo wszelkich zawartych w nim zależności projektu. Projekty, które nie zostały wybrane do skompilowania, są nadal objęte debugowaniem, uruchamianiem, pakowaniem i wdrażaniem rozwiązania.

- Deploy

   Określa, czy projekt zostanie wdrożony, gdy polecenia Uruchom lub Wdróż zostaną użyte z wybraną konfiguracją kompilacji rozwiązania. Pole wyboru dla tego pola będzie dostępne, jeśli projekt obsługuje wdrażanie przez implementację interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> w obiekcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>.

  Po dodaniu nowej konfiguracji rozwiązania użytkownik może wybrać ją z listy rozwijanej Konfiguracja rozwiązania na pasku narzędzi Standardowy, aby skompilować i/lub uruchomić tę konfigurację.

## <a name="see-also"></a>Zobacz także
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)