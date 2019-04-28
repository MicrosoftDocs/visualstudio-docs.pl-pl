---
title: 'Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fc518281880923f92caf5c517254dc424b49b5c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415277"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015
Poniżej przedstawiono sposób uaktualnić Twoje rozszerzenie.

> [!IMPORTANT]
> Jeśli zamierzasz Obsługa wersji rozwiązania rozszerzenie dla starszej wersji programu Visual Studio, należy koniecznie Utwórz kopię przed przystąpieniem do uaktualniania. Może być trudne do zwrócenia uaktualnionej wersji do jego poprzedniego stanu.

### <a name="to-upgrade-an-extensibility-solution"></a>Aby uaktualnić to rozwiązanie rozszerzalności

1. Przy użyciu kopii, które chcesz uaktualnić, otwórz go w nowej wersji. Książek uaktualnienia jest nieodwracalna.

2. Po zakończeniu uaktualniania, należy zmienić ścieżkę zewnętrzny program do nowej wersji *devenv.exe*. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, następnie wybierz **właściwości**. W **debugowania** znaleźć pola tekstowego, a **uruchomienia programu zewnętrznego** i zmień ścieżkę *devenv.exe* do ścieżki programu Visual Studio 2015, która powinna wyglądać mniej więcej tak:

     *%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe*

3. Dodaj odwołanie do *Microsoft.VisualStudio.Shell.14.0.dll*. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** , a następnie wybierz **Dodaj** > **odwołania**. Wybierz **rozszerzenia** kartę, a następnie sprawdź **Microsoft.VisualStudio.Shell.14.0**.)

4. Skompiluj rozwiązanie. Tworzenie plików są wdrażane do:

     *%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\<Author Name\>\\<Project Name\>\\<Project Version\>\\*.

### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Aby zaktualizować projekt rozszerzenia NuGet zestawu SDK dla zestawów odwołań

1. Określ zestawy odwołań zestawu SDK, czego potrzebuje projektu.  W **Eksploratora rozwiązań**, rozwiń węzeł projektu **odwołania** węzła i przejrzyj listę odwołań do projektu.  Zestawy odwołań do zestawu SDK będzie mieć prefiks **Microsoft.VisualStudio** nazwę (na przykład: Microsoft.VisualStudio.Shell.14.0).

2. Usuń zestawy odwołań zestawu SDK z projektu, wybierając je, kliknij prawym przyciskiem myszy i wybierz pozycję **Usuń**.

3. Dodawanie wersji NuGet zestawów odwołań zestawu SDK programu VS.  W **odwołania Eksploratora rozwiązań** otworzyć węzła **Zarządzaj pakietami NuGet** okna dialogowego.  Jeśli chcesz dowiedzieć się więcej na temat tego okna dialogowego, zobacz [interfejs użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI). Zestawy odwołań zestawu SDK są publikowane w [nuget.org](http://www.nuget.org) przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).

4. Za pomocą **nuget.org** jako swojej **źródła pakietu**, wyszukaj nazwę pakietu NuGet, odpowiadającego zestawu żądane odwołanie (na przykład: Microsoft.VisualStudio.Shell.14.0) i zainstaluj go w projekcie.  NuGet może dodać wiele zestawów odwołań, aby spełnić wymagania zależności zestawów początkowej.

     Jeśli wolisz, możesz dodać wszystkie zestawy odwołań zestawu SDK jednocześnie, Instalowanie zestawu SDK dla programu [pakiet Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).

5. Możesz również przełączyć się do korzystania z narzędzia do kompilacji zestawu SDK w wersji NuGet. Ten pakiet NuGet jest [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) i raz dodane do projektu spowoduje zawierają niezbędne narzędzia i pliki, co pozwala tworzyć projekty rozszerzalności na komputerze bez zainstalowany zestaw SDK programu VS docelowe.

> [!NOTE]
> Nie jest wymagane zaktualizowanie istniejących projektów rozszerzalności do użycia narzędzia i zestawy odwołań NuGet.  Może nadal tworzyć zawartość przy użyciu zestawy referencyjne i narzędzia są zainstalowane przy użyciu zestawu SDK programu VS.