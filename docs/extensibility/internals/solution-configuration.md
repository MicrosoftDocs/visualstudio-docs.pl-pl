---
title: Konfiguracja rozwiązania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705375"
---
# <a name="solution-configuration"></a>Konfiguracja rozwiązania
Konfiguracje rozwiązań przechowują właściwości na poziomie rozwiązania. Kierują zachowanie klawisza **Start** (F5) i **poleceniami Kompilacja.** Domyślnie te polecenia kompilacji i uruchomienia konfiguracji debugowania. Oba polecenia są wykonywane w kontekście konfiguracji rozwiązania. Oznacza to, że użytkownik może oczekiwać, że F5, aby uruchomić i skompilować niezależnie od aktywnego rozwiązania jest skonfigurowany za pomocą ustawień. Środowisko jest przeznaczone do optymalizacji pod kątem rozwiązań, a nie projektów, jeśli chodzi o tworzenie i uruchamianie.

 Standardowy pasek narzędzi Programu Visual Studio zawiera przycisk Start i rozwijaną konfiguracji rozwiązania po prawej stronie przycisku Start. Ta lista umożliwia użytkownikom wybranie konfiguracji, która ma zostać uruchomiona po naciśnięciu klawisza F5, utworzenie własnych konfiguracji rozwiązania lub edytowanie istniejącej konfiguracji.

> [!NOTE]
> Nie ma interfejsów rozszerzalności do tworzenia lub edytowania konfiguracji rozwiązania. Należy użyć `DTE.SolutionBuild`pliku . Istnieją jednak interfejsy API rozszerzalności do zarządzania kompilacją rozwiązania. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Oto jak można zaimplementować konfiguracje rozwiązania obsługiwane przez typ projektu:

- Projekt

   Wyświetla nazwy projektów znalezionych w bieżącym rozwiązaniu.

- Konfigurowanie

   Aby podać listę konfiguracji obsługiwanych przez typ projektu i wyświetlanych <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>na stronach właściwości, należy zaimplementować program .

   Kolumna Konfiguracja wyświetla nazwę konfiguracji projektu do utworzenia w tej konfiguracji rozwiązania i wyświetla listę wszystkich konfiguracji projektu po kliknięciu przycisku strzałki. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodę, aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda wskazuje, że projekt obsługuje edycję konfiguracji, w nagłówku Konfiguracja są również wyświetlane opcje Nowe lub Edytuj. Każdy z tych wyborów uruchamia okna dialogowe, które wywołują metody `IVsCfgProvider2` interfejsu do edycji konfiguracji projektu.

   Jeśli projekt nie obsługuje konfiguracji, w kolumnie Konfiguracja jest wyświetlany brak i jest wyłączona.

- Platforma

   Wyświetla platformę, dla której tworzy się konfiguracja wybranego projektu, i wyświetla listę wszystkich dostępnych platform dla projektu po kliknięciu przycisku strzałki. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodę, aby wypełnić tę listę. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metoda wskazuje, że projekt obsługuje edycji platformy, Nowe lub Edytuj zaznaczenia są również wyświetlane w nagłówku Platformy. Każdy z tych wyborów uruchamia `IVsCfgProvider2` okna dialogowe, które wywołują metody edycji dostępnych platform projektu.

   Jeśli projekt nie obsługuje platform, kolumna platformy dla tego projektu wyświetla None i jest wyłączona.

- Kompilacja

   Określa, czy projekt jest zbudowany przez bieżącą konfigurację rozwiązania. Niezaznaczone projekty nie są tworzone, gdy polecenia kompilacji na poziomie rozwiązania są wywoływane pomimo wszelkich zależności projektu, które zawierają. Projekty, które nie zostały wybrane do zbudowannia, są nadal uwzględniane w debugowaniu, uruchamianiu, pakowaniu i wdrażaniu rozwiązania.

- Wdrażanie

   Określa, czy projekt zostanie wdrożony, gdy polecenia Start lub Deploy są używane z konfiguracją kompilacji wybranego rozwiązania. Pole wyboru dla tego pola będzie dostępne, jeśli projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> obsługuje wdrażanie przez implementowanie interfejsu na jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> obiekcie.

  Po dodaniu nowej konfiguracji rozwiązania użytkownik może wybrać ją z listy rozwijanej Konfiguracja rozwiązania na standardowym pasku narzędzi, aby zbudować i/lub uruchomić tę konfigurację.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
