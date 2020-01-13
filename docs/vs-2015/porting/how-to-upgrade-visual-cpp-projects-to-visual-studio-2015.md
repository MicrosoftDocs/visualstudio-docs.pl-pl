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
ms.openlocfilehash: 60ba1ad7f1ed467cb1a396f80228b8915bd62a31
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918801"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Instrukcje: uaktualnianie projektów w języku Visual C++ do programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dokumentacja Najpóźniejsza dla programu Visual Studio 2017, zobacz [przewodnik przenoszenia Visual C++ i uaktualniania](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Przy pierwszym otwarciu projektu Visual C++, który został utworzony we wcześniejszej wersji programu Visual Studio, może być monit o aktualizację projektu. Komunikat pyta, czy chcesz przeprowadzić uaktualnienie do najnowszej wersji kompilatora Visual C++ i bibliotek. Opcje uaktualniania zależą od wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użytą do utworzenia projektu.

 Można użyć [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] do otwierania, edytowania i tworzenia [!INCLUDE[win8](../includes/win8-md.md)] projektów, które zostały utworzone w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], aby utworzyć nową, ale [!INCLUDE[win8](../includes/win8-md.md)] projektu, należy użyć [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Aby utworzyć [!INCLUDE[win81](../includes/win81-md.md)] projektu, należy użyć [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Aby utworzyć projekt systemu Windows 10, należy użyć [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Jeśli zostanie wyświetlony monit, aby zaktualizować projekt, nie trzeba nic robić, aby uaktualnić projekt.

- Jeśli projekt (.vcproj) został utworzony w wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest starszy niż [!INCLUDE[vs2010](../includes/vs2010-md.md)], musisz zaktualizować projekt.

- Jeśli projekt (.vcxproj) został utworzony w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] dostępne są dwie opcje:

  - Można pominąć tę aktualizację. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] załaduje projekt bez wprowadzania żadnych zmian, jeśli ma on dostęp do narzędzi Visual C++ w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] z dodatkiem SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], lub [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Można otworzyć ten dostęp przez zainstalowanie wersji programu Visual Studio, którego projekt został utworzony za pomocą na tym samym komputerze, który ma [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Aby uzyskać więcej informacji, zobacz [zainstalowanie wersji programu Visual Studio Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

  - Można zaktualizować projekt, umożliwiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zmian, które są opisane w dalszej części tego tematu. Jeśli masz więcej niż jeden projekt języka Visual C++ w swoim rozwiązaniu, należy zaktualizować wszystkie z nich.

    > [!NOTE]
    > Jeśli aktualizacja zostanie odrzucona po wyświetleniu monitu, projekt można zaktualizować później, wybierając **Aktualizuj projekt VC ++** na **projektu** menu. Jeśli polecenie nie jest widoczna, następnie aktualizacja nie jest wymagana.

## <a name="upgrading-a-visual-c-project"></a>Uaktualnienie projektu Visual C++
 Jeśli zezwolisz programowi [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] automatycznie zaktualizować projekt, zmiany te są wykonywane:

- Zmienia projekt, tak aby używał [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] kompilatora i bibliotek (PlatformToolset = VisualStudio w wersji 140).

- Aby uzyskać [!INCLUDE[cppcli](../includes/cppcli-md.md)] projektów, zmienia wartość TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Kontynuowanie pracy z niestandardowym PlatformToolset
 Jeśli chcesz kontynuować pracę z niestandardowym PlatformToolset w [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], zestaw narzędzi musi znajdować się pod %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na x86 komputerze lub % ProgramFiles (x86)%\MSBuild\ Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ na x64 maszyny. Aby uzyskać informacje o sposobie tworzenia niestandardowego zestawu narzędzi platformy, zobacz [C++ natywna Wielowersyjność](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) na blogu zespołu Visual C++.

## <a name="see-also"></a>Zobacz też
 [Visual C++, przenoszenie i uaktualnianie przewodnik](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
