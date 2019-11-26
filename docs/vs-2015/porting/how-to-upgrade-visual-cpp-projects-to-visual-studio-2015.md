---
title: 'Porady: Aktualizacja projektów Visual C++ w Visual Studio 2015 | Dokumentacja firmy Microsoft'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: b33b1b47ad4c32aabe09aae5a66fe3f02aeb1487
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300383"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Instrukcje: uaktualnianie projektów w języku Visual C++ do programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać ostatnią dokumentację programu Visual Studio 2017, zobacz temat [przenoszenie C++ i uaktualnianie wizualne](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Przy pierwszym otwarciu projektu Visual C++, który został utworzony we wcześniejszej wersji programu Visual Studio, może być monit o aktualizację projektu. Komunikat pyta, czy chcesz przeprowadzić uaktualnienie do najnowszej wersji kompilatora Visual C++ i bibliotek. Opcje uaktualniania zależą od wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], która została użyta do utworzenia projektu.

 Za pomocą [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] można otwierać, edytować i kompilować [!INCLUDE[win8](../includes/win8-md.md)] projekty, które zostały utworzone w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ale aby utworzyć nowy projekt [!INCLUDE[win8](../includes/win8-md.md)], należy użyć [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Aby utworzyć projekt [!INCLUDE[win81](../includes/win81-md.md)], należy użyć [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Aby utworzyć projekt systemu Windows 10, należy użyć [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Jeśli zostanie wyświetlony monit, aby zaktualizować projekt, nie trzeba nic robić, aby uaktualnić projekt.

- Jeśli projekt (. vcproj) został utworzony w wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starszej niż [!INCLUDE[vs2010](../includes/vs2010-md.md)], należy zaktualizować projekt.

- Jeśli projekt (. vcxproj) został utworzony w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] masz dwie opcje:

  - Można pominąć tę aktualizację. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] załaduje projekt bez wprowadzania żadnych zmian, jeśli ma dostęp do narzędzi wizualnych C++ w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Ten dostęp można zapewnić przez zainstalowanie wersji programu Visual Studio, która została utworzona przez projekt na tym samym komputerze, który ma [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Aby uzyskać więcej informacji, zobacz [Instalowanie wersji programu Visual Studio obok](../install/install-visual-studio-versions-side-by-side.md)siebie.

  - Możesz zaktualizować projekt, umożliwiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wprowadzeniem zmian opisanych w dalszej części tego tematu. Jeśli masz więcej niż jeden projekt języka Visual C++ w swoim rozwiązaniu, należy zaktualizować wszystkie z nich.

    > [!NOTE]
    > Jeśli odrzucisz aktualizację po pierwszym wyświetleniu monitu, możesz zaktualizować projekt później, wybierając polecenie **Aktualizuj projekt VC + +** w menu **projekt** . Jeśli polecenie nie jest widoczna, następnie aktualizacja nie jest wymagana.

## <a name="upgrading-a-visual-c-project"></a>Uaktualnienie projektu Visual C++
 Jeśli zezwolisz [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] na automatyczne aktualizowanie projektu, te zmiany zostaną wprowadzone:

- Zmienia projekt, tak aby używał [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] kompilatora i bibliotek (PlatformToolset = VisualStudio wersji 140).

- W przypadku projektów [!INCLUDE[cppcli](../includes/cppcli-md.md)] zmienia TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Kontynuowanie pracy z niestandardowym PlatformToolset
 Jeśli chcesz kontynuować pracę z niestandardowym PlatformToolset w [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], zestaw narzędzi musi znajdować się w obszarze%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na komputerze z procesorem x86 lub w folderze% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na komputerze z procesorem x64. Aby uzyskać informacje o sposobach tworzenia niestandardowych PlatformToolset, zobacz [ C++ natywny cel wielowymiarowy](https://go.microsoft.com/fwlink/?LinkId=248587) na C++ blogu zespołu wizualnego.

## <a name="see-also"></a>Zobacz też
 [Wizualne C++ przenoszenie i uaktualnianie przewodnika](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
