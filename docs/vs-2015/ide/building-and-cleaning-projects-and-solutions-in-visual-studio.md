---
title: Twórz projekty czystego rozwiązania
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d447d82815046aba6383c2467c2b44c5b7d0d0f0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685718"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Kompilowanie oraz oczyszczanie projektów i rozwiązań w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z procedur opisanych w tym temacie, można utworzyć, odbudować lub wyczyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Aby uzyskać samouczek krok po kroku, zobacz [instruktażu: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Interfejs użytkownika w Twojej wersji programu Visual Studio mogą różnić się od co w tym temacie opisano, w zależności od aktywnych ustawień. Aby zmienić swoje ustawienia, otwórz **narzędzia** menu, a następnie wybierz **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Do kompilacji, odbudować lub Wyczyść całe rozwiązanie

1. W **Eksploratora rozwiązań**, wybierz lub Otwórz rozwiązanie.

2. Na pasku menu wybierz **kompilacji**, a następnie wybierz jedno z następujących poleceń:

    - Wybierz **kompilacji** lub **Kompiluj rozwiązanie** skompilować tylko tych projektów, plików i składników, które zmieniły się od najnowszej kompilacji.

        > [!NOTE]
        > **Kompilacji** staje się polecenia **Kompiluj rozwiązanie** gdy rozwiązanie zawiera więcej niż jeden projekt.

    - Wybierz **Kompiluj rozwiązanie** do rozwiązania "Wyczyść", a następnie skompilowanie wszystkich plików projektu i składników.

    - Wybierz **czyste rozwiązanie** można usunąć wszystkich plików pośrednich i wynikowych. Za pomocą tylko projektu, jak i składnika pliki po lewej nowe wystąpienia pośrednich i pliki wyjściowe może następnie być skompilowana.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby skompilować lub ponownie skompilować pojedynczego projektu

1. W **Eksploratora rozwiązań**, wybrać lub otworzyć projektu.

2. Na pasku menu wybierz **kompilacji**, a następnie wybierz **kompilacji** _ProjectName_ lub **odbudować** _ProjectName_.

    - Wybierz **kompilacji** _ProjectName_ tworzenie tylko tych projektów składników, które zmieniły się od najnowszej kompilacji.

    - Wybierz **odbudować** _ProjectName_ do projektu "Wyczyść", a następnie skompiluj pliki projektu i wszystkich składników projektów.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Aby skompilować tylko projekt startowy i jego zależności

1. Na pasku menu wybierz **narzędzia**, **opcje**.

2. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania** węzła, a następnie wybierz **kompilowanie i uruchamianie** strony.

    **Kompiluj i uruchom, projekty i rozwiązania, opcje** zostanie otwarte okno dialogowe.

3. Wybierz **tylko tworzyć projekty startowe i zależności przy uruchomieniu** pole wyboru.

    Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są tworzone podczas wykonywania jednej z następujących czynności:

   - Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** (F5).

   - Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** (CTRL + SHIFT + B).

     Gdy to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i pliki rozwiązania są tworzone po uruchomieniu dowolnego z powyższych poleceń. Domyślnie to pole wyboru jest wyczyszczone.

## <a name="to-build-only-the-selected-visual-c-project"></a>Można tworzyć tylko dla wybranego projektu Visual C++

1. Wybierz [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu, a następnie na pasku menu wybierz **kompilacji**, **projektu tylko**i jeden z następujących poleceń:

   - **Tylko kompilacja** *ProjectName*

   - **Ponownie skompiluj tylko** *ProjectName*

   - **Czyszczenie tylko** *ProjectName*

   - **Połącz tylko** *ProjectName*

     Polecenia te dotyczą tylko programu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu, która została wybrana, bez tworzenia, ponownie skompilować, czyszczenia i łączenie wszystkie zależności projektu lub rozwiązania pliki. W zależności od używanej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **projektu tylko** podmenu może zawierać więcej poleceń.

## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować wiele elementów projektu C++

1. W **Eksploratora rozwiązań**, wybierz wiele plików, które mają może być skompilowany akcji, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz **skompilować**.

     Jeśli pliki mają zależności, pliki zostanie skompilowany w kolejności wg zależności. Operacja kompilacji zakończy się niepowodzeniem, jeśli pliki wymagają prekompilowanego nagłówka, który nie jest dostępny podczas kompilacji. Operacja kompilacji używa bieżącej aktywnej konfiguracji rozwiązania.

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

1. Wykonaj jedną z następujących czynności:

    - Na pasku menu wybierz **kompilacji**, **anulować**.

    - Wybierz kombinację klawiszy Ctrl + Break kluczy.

## <a name="see-also"></a>Zobacz także
 [Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md) [uzyskiwanie dzienniki kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) [kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md) [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md) [Debuguj i zwolnij konfiguracje projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [odwołanie kompilacji C/C++](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [przełączników wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md) [rozwiązań i projektów](../ide/solutions-and-projects-in-visual-studio.md)
