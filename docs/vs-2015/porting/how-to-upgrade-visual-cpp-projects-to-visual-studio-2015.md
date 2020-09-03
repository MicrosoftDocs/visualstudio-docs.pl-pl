---
title: 'Instrukcje: uaktualnianie Visual C++ projektów do programu Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 23461fb1927cfcbf738d2dbcb82e3977b3be265a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278728"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Instrukcje: uaktualnianie projektów w języku Visual C++ do programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zapoznać się z ostatnią dokumentacją dla programu Visual Studio 2017, zobacz [Visual C++ przenoszenie i uaktualnianie przewodnika](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Po pierwszym otwarciu projektu Visual C++, który został utworzony we wcześniejszej wersji programu Visual Studio, może zostać wyświetlony monit o zaktualizowanie projektu. Zostanie wyświetlony komunikat z pytaniem, czy chcesz przeprowadzić uaktualnienie do najnowszej wersji kompilatora Visual C++ i bibliotek. Opcje uaktualniania zależą od wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , która została użyta do utworzenia projektu.

 Można użyć [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] do otwierania, edytowania i kompilowania [!INCLUDE[win8](../includes/win8-md.md)] projektów, które zostały utworzone w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , ale aby utworzyć nowy [!INCLUDE[win8](../includes/win8-md.md)] projekt, należy użyć [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] . (Aby utworzyć [!INCLUDE[win81](../includes/win81-md.md)] projekt, należy użyć [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] .)

 Aby utworzyć projekt systemu Windows 10, musisz użyć [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] .

 Jeśli nie zostanie wyświetlony monit o zaktualizowanie projektu, nie trzeba wykonywać żadnych czynności w celu uaktualnienia projektu.

- Jeśli projekt (. vcproj) został utworzony w wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starszej niż [!INCLUDE[vs2010](../includes/vs2010-md.md)] , należy zaktualizować projekt.

- Jeśli projekt (. vcxproj) został utworzony w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ,  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] masz dwie opcje:

  - Możesz pominąć aktualizację. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] program załaduje projekt bez wprowadzania żadnych zmian, jeśli ma dostęp do narzędzi Visual C++ w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1,  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Ten dostęp można zapewnić przez zainstalowanie wersji programu Visual Studio, która została utworzona przez projekt na tym samym komputerze, na którym znajduje się system [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] . Aby uzyskać więcej informacji, zobacz [Instalowanie wersji programu Visual Studio obok](../install/install-visual-studio-versions-side-by-side.md)siebie.

  - Aby zaktualizować projekt, możesz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wprowadzić zmiany opisane w dalszej części tego tematu. Jeśli masz więcej niż jeden projekt Visual C++ w rozwiązaniu, musisz zaktualizować wszystkie z nich.

    > [!NOTE]
    > Jeśli odrzucisz aktualizację po pierwszym wyświetleniu monitu, możesz zaktualizować projekt później, wybierając polecenie **Aktualizuj projekt VC + +** w menu **projekt** . Jeśli polecenie nie zostanie wyświetlone, aktualizacja nie jest wymagana.

## <a name="upgrading-a-visual-c-project"></a>Uaktualnianie projektu Visual C++
 Jeśli zezwolisz [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] na automatyczne aktualizowanie projektu, te zmiany zostaną wprowadzone:

- Zmienia projekt tak, aby korzystał z [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] kompilatora i bibliotek (PlatformToolset = VisualStudio wersji 140).

- W przypadku [!INCLUDE[cppcli](../includes/cppcli-md.md)] projektów program zmienia TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Kontynuowanie pracy z niestandardowym PlatformToolset
 Jeśli chcesz kontynuować pracę z niestandardowym PlatformToolset w programie [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] , zestaw narzędzi musi znajdować się w obszarze%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na komputerze z procesorem x86 lub w folderze% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na komputerze z procesorem x64. Aby uzyskać informacje o sposobach tworzenia niestandardowych PlatformToolset, zobacz [natywny cel](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) wielowymiarowy języka C++ na blogu zespołu Visual C++.

## <a name="see-also"></a>Zobacz też
 [Visual C++ przenoszenie i uaktualnianie przewodnika](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
