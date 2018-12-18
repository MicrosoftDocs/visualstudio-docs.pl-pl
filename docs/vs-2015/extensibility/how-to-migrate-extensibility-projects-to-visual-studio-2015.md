---
title: 'Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564e279d259cae879ca2925eed3309c30d7513db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785160"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniżej przedstawiono sposób uaktualnić Twoje rozszerzenie.  
  
> [!IMPORTANT]
>  Jeśli zamierzasz Obsługa wersji rozwiązania rozszerzenie dla starszej wersji programu Visual Studio, należy koniecznie Utwórz kopię przed przystąpieniem do uaktualniania. Może być trudne do zwrócenia uaktualnionej wersji do jego poprzedniego stanu.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Aby uaktualnić to rozwiązanie rozszerzalności  
  
1.  Przy użyciu kopii, które chcesz uaktualnić, otwórz go w nowej wersji. Książek uaktualnienia jest nieodwracalna.  
  
2.  Po zakończeniu uaktualniania, należy zmienić ścieżkę zewnętrzny program do nowej wersji devenv.exe. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, następnie wybierz **właściwości**. W **debugowania** znaleźć pola tekstowego, a **uruchomienia programu zewnętrznego** i zmień ścieżkę devenv.exe ścieżki programu Visual Studio 2015, która powinna wyglądać mniej więcej tak:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.14.0.dll. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** , a następnie wybierz **Dodaj / Reference**. Wybierz **rozszerzenia** kartę, a następnie sprawdź **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Skompiluj rozwiązanie. Tworzenie plików są wdrażane do:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nazwa autora\>\\< Nazwa projektu\>\\< wersja projektu\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aby zaktualizować projekt rozszerzenia NuGet zestawu SDK dla zestawów odwołań  
  
1.  Określ zestawy odwołań zestawu SDK, czego potrzebuje projektu.  W **Eksploratora rozwiązań**, rozwiń węzeł projektu **odwołania** węzła i przejrzyj listę odwołań do projektu.  Zestawy odwołań do zestawu SDK będzie mieć prefiks **Microsoft.VisualStudio** nazwę (na przykład: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Usuń zestawy odwołań zestawu SDK z projektu, wybierając je, kliknij prawym przyciskiem myszy i **Usuń**.  
  
3.  Dodawanie wersji NuGet zestawów odwołań zestawu SDK programu VS.  W **odwołania Eksploratora rozwiązań** otworzyć węzła **Zarządzaj pakietami NuGet...** okno dialogowe.  Jeśli chcesz dowiedzieć się więcej na temat tego okna dialogowego, zobacz [Zarządzanie NuGet pakietów przy użyciu okna dialogowego](http://docs.nuget.org/Consume/Package-Manager-Dialog). Zestawy odwołań zestawu SDK są publikowane w [nuget.org](http://www.nuget.org) przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Za pomocą **nuget.org** jako usługi **źródła pakietu**, wyszukaj nazwę pakietu NuGet, odpowiadającego zestawu żądane odwołanie (na przykład: Microsoft.VisualStudio.Shell.14.0) i zainstaluj go w Twojej Projekt.  NuGet może dodać wiele zestawów odwołań, aby spełnić wymagania zależności zestawów początkowej.  
  
     Jeśli wolisz, możesz dodać wszystkie zestawy odwołań zestawu SDK jednocześnie, Instalowanie zestawu SDK dla programu [pakiet Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Możesz również przełączyć się do korzystania z narzędzia do kompilacji zestawu SDK w wersji NuGet. Ten pakiet NuGet jest [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) i raz dodane do projektu spowoduje zawierają niezbędne narzędzia i pliki, co pozwala tworzyć projekty rozszerzalności na komputerze bez zainstalowany zestaw SDK programu VS docelowe.  
  
> [!NOTE]
>  Nie jest wymagane zaktualizowanie istniejących projektów rozszerzalności do użycia narzędzia i zestawy odwołań NuGet.  Może nadal tworzyć zawartość przy użyciu zestawy referencyjne i narzędzia są zainstalowane przy użyciu zestawu SDK programu VS.

