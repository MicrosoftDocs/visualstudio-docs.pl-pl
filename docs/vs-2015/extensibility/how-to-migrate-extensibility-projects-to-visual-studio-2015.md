---
title: 'Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b48370847cbb2cf8b171342aff9baf38c40a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295558"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oto jak uaktualnić rozszerzenie.  
  
> [!IMPORTANT]
> Jeśli zamierzasz zachować wersję rozwiązania rozszerzenia dla starszej wersji programu Visual Studio, upewnij się, że utworzono kopię przed uaktualnieniem. Przywrócenie uaktualnionej wersji do poprzedniego stanu może być trudne.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Aby uaktualnić rozwiązanie rozszerzalności  
  
1. Za pomocą kopii, którą chcesz uaktualnić, otwórz ją w nowej wersji. Zaleca się, aby uaktualnienie nie było odwracalne.  
  
2. Po zakończeniu uaktualniania zmień ścieżkę programu zewnętrznego na nową wersję programu devenv. exe. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**. Na karcie **debugowanie** Znajdź pole tekstowe przez **uruchomienie programu zewnętrznego** i zmień ścieżkę devenv. exe na ścieżkę programu Visual Studio 2015, która powinna wyglądać następująco:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. Dodaj odwołanie do pliku Microsoft. VisualStudio. Shell. 14.0. dll. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** a następnie wybierz polecenie **Dodaj/odwołanie**. Wybierz kartę **rozszerzenia** , a następnie sprawdź **Microsoft. VisualStudio. Shell. 14.0**.)  
  
4. Skompiluj rozwiązanie. Skompilowane pliki są wdrażane w:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< autora\>\\< Project name\>\\< wersja projektu\>\\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aby zaktualizować projekt rozszerzalności do zestawów referencyjnych NuGet VS SDK  
  
1. Określ zestawy referencyjne zestawu SDK programu VS, których potrzebuje Twój projekt.  W **Eksplorator rozwiązań**rozwiń węzeł **odwołania** projektu i przejrzyj listę odwołań projektu.  Zestawy SDK programu VS zawierają prefiks **Microsoft. VisualStudio** w nazwie (na przykład: Microsoft. VisualStudio. Shell. 14.0).  
  
2. Usuń zestawy odwołań programu VS SDK z projektu, zaznaczając je, prawym przyciskiem myszy i **Usuń**.  
  
3. Dodaj wersje NuGet zestawów odwołań programu VS SDK.  Gdy nadal znajduje się w węźle **Eksplorator rozwiązań References** , Otwórz **pakiety NuGet...** okno dialogowe.  Jeśli chcesz dowiedzieć się więcej na temat tego okna dialogowego, zobacz [Zarządzanie pakietami NuGet przy użyciu okna dialogowego](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio). Zestawy odwołań programu VS SDK są publikowane w witrynie [NuGet.org](https://www.nuget.org/) przez [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Używając **NuGet.org** jako **źródła pakietu**, wyszukaj nazwę pakietu NuGet zgodną z żądanym zestawem odwołania (na przykład: Microsoft. VisualStudio. Shell. 14.0) i zainstaluj go w projekcie.  Pakiet NuGet może dodać wiele zestawów referencyjnych w celu spełnienia zależności zestawu początkowego.  
  
     Jeśli wolisz, możesz dodać wszystkie zestawy odwołań programu VS SDK jednocześnie, instalując [pakiet meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK programu vs.  
  
5. Możesz również przełączyć się do korzystania z wersji NuGet narzędzi do tworzenia zestawu SDK programu VS. Ten pakiet NuGet to [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) , a po dodaniu do projektu będzie zawierać niezbędne narzędzia i pliki docelowe, aby umożliwić skompilowanie projektu rozszerzalności na komputerze bez zainstalowanego zestawu SDK programu vs.  
  
> [!NOTE]
> Nie jest wymagane, aby aktualizować istniejące projekty rozszerzalności do korzystania z zestawów odwołań NuGet i narzędzi.  Mogą oni nadal tworzyć zestawy referencyjne i narzędzia zainstalowane przy użyciu zestawu SDK programu VS.
