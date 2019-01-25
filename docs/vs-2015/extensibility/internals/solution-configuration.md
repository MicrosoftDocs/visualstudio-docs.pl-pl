---
title: Konfiguracja rozwiązania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb14a2031b89f2a7deeb7d98cc483e90125b1905
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781417"
---
# <a name="solution-configuration"></a>Konfiguracja rozwiązania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Konfiguracje rozwiązania przechowywania właściwości poziomie rozwiązania. Bezpośrednie ich zachowanie **Start** klucza (F5) i **kompilacji** poleceń. Domyślnie te polecenia kompilacji i uruchomić z konfiguracji debugowania. Oba polecenia są wykonywane w kontekście konfiguracji rozwiązania. Oznacza to, czy użytkownika można oczekiwać, że F5 do uruchamiania i kompilacji, niezależnie od aktywnego rozwiązania są konfigurowane za pomocą ustawień. Środowisko zaprojektowano pod kątem rozwiązań, a nie z projektów, jeśli chodzi o tworzenie i uruchamianie.  
  
 Standardowy pasek narzędzi programu Visual Studio zawiera przycisk Start i Konfiguracja rozwiązania listy rozwijanej z prawej strony przycisk Start. Ta lista pozwala użytkownikom wybrać konfigurację można uruchomić po naciśnięciu klawisza F5, tworzyć własne konfiguracje rozwiązań lub Edytuj istniejącą konfigurację.  
  
> [!NOTE]
>  Nie ma żadnych interfejsów rozszerzalności do tworzenia lub edytowania konfiguracje rozwiązania. Należy użyć `DTE.SolutionBuilder`. Istnieją jednak rozszerzalności interfejsów API do zarządzania budowanie rozwiązania. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Poniżej przedstawiono, jak można implementować konfiguracje rozwiązania obsługiwany przez użytkownika typ projektu:  
  
- Projekt  
  
   Wyświetla nazwy projektów w bieżącym rozwiązaniu.  
  
- Konfiguracja  
  
   Podaj listę konfiguracje obsługiwane przez danego typu projektu i wyświetlane na stronach właściwości wdrożenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
   Kolumna konfiguracji Wyświetla nazwę konfiguracji projektu do kompilacji w tej konfiguracji rozwiązania i wyświetla listę wszystkich konfiguracji projektu, po kliknięciu przycisk strzałki. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodę, aby wypełnić tej listy. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metody oznacza, że projekt obsługuje edycji konfiguracji, nowe lub Edytuj wybrane opcje są również wyświetlane w pozycji konfiguracji. Każda z tych opcji Uruchom okna dialogowe, które wywołują metody `IVsCfgProvider2` interfejsu do edycji konfiguracji projektu.  
  
   Jeśli projekt nie obsługuje konfiguracji, w kolumnie konfiguracji wyświetla Brak i jest wyłączone.  
  
- Platforma  
  
   Wyświetla platformę konfiguracji wybranego projektu kompilacji dla oraz listę wszystkich dostępnych platform dla projektu, po kliknięciu przycisk strzałki. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodę, aby wypełnić tej listy. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metody oznacza, że projekt obsługuje edytowania platform, nowe lub Edytuj wybrane opcje są również wyświetlane pod nagłówkiem platformy. Każda z tych opcji Uruchom okna dialogowe, które wywołują `IVsCfgProvider2` metody służące do edycji projektu dostępnych platform.  
  
   Jeśli projekt nie obsługuje platformy, w kolumnie platformy dla tego projektu Brak Wyświetla i jest wyłączone.  
  
- Kompilacja  
  
   Określa, czy projekt jest kompilowany za pomocą bieżącej konfiguracji rozwiązania. Niewybrane projekty są kompilowane podczas wywoływania poleceń kompilacji poziomie rozwiązania niezależnie od wszelkich zależności projektu, które zawierają. Nie wybrano projektów do zbudowania nadal będą uwzględniane w debugowanie, uruchamianie, pakowania i wdrażania rozwiązania.  
  
- Deploy  
  
   Określa, czy stosowania poleceń uruchamiania lub Wdróż przy użyciu wybranego rozwiązania konfiguracji kompilacji zostanie wdrożony projekt. Pole wyboru dla tego pola będą dostępne, jeśli projekt obsługuje wdrażania przez zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejs w jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> obiektu.  
  
  Po dodaniu nowej konfiguracji rozwiązania, użytkownik może wybrać go z konfiguracji rozwiązania pola listy rozwijanej na standardowym pasku narzędzi do kompilacji i/lub uruchom tę konfigurację.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)
