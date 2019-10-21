---
title: Tworzenie rozwiązań czystych projektów
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f2817b6fd0aee312ff41af218d01ad80bc785e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620559"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Kompilowanie oraz oczyszczanie projektów i rozwiązań w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z procedur opisanych w tym temacie, można tworzyć, odbudować lub czyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Aby zapoznać się z samouczkiem krok po kroku, zobacz [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Interfejs użytkownika w wydaniu programu Visual Studio może się różnić od tego, co opisano w tym temacie, w zależności od aktywnych ustawień. Aby zmienić ustawienia, otwórz menu **Narzędzia** , a następnie wybierz polecenie **Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby skompilować, skompilować lub wyczyścić całe rozwiązanie

1. W **Eksplorator rozwiązań**wybierz lub Otwórz rozwiązanie.

2. Na pasku menu wybierz **kompilacja**, a następnie wybierz jedno z następujących poleceń:

    - Wybierz **Kompiluj** lub **Kompiluj rozwiązanie** , aby skompilować tylko te pliki projektu i składniki, które uległy zmianie od czasu ostatniej kompilacji.

        > [!NOTE]
        > Polecenie **Build** zostaje **skompilowane rozwiązanie** , gdy rozwiązanie zawiera więcej niż jeden projekt.

    - Wybierz opcję **Kompiluj ponownie rozwiązanie** , aby usunąć rozwiązanie, a następnie Skompiluj wszystkie pliki i składniki projektu.

    - Wybierz pozycję **Wyczyść rozwiązanie** , aby usunąć wszystkie pliki pośrednie i wyjściowe. Tylko w przypadku pozostałych plików projektu i składników można skompilować nowe wystąpienia plików pośrednich i wyjściowych.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby skompilować lub skompilować pojedynczy projekt

1. W **Eksplorator rozwiązań**wybierz lub Otwórz projekt.

2. Na pasku menu wybierz **kompilacja**, a następnie wybierz opcję **Kompiluj** _ProjectName_ lub **Skompiluj ponownie** _ProjectName_.

    - Wybierz pozycję **Kompiluj** _ProjectName_ , aby skompilować tylko składniki projektu, które uległy zmianie od czasu ostatniej kompilacji.

    - Wybierz pozycję **Kompiluj ponownie** _ProjectName_ , aby usunąć "czysty" projekt, a następnie Skompiluj pliki projektu i wszystkie składniki projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Aby skompilować tylko projekt startowy i jego zależności

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania** , a następnie wybierz stronę **kompilacja i uruchomienie** .

    Zostanie otwarte okno dialogowe **kompilacja i uruchomienie, projekty i rozwiązania, opcje** .

3. Zaznacz pole wyboru **Kompiluj tylko projekty startowe i zależności przy uruchamianiu** .

    Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są kompilowane podczas wykonywania jednego z następujących kroków:

   - Na pasku menu wybierz **debuguj**  > **Rozpocznij debugowanie** (F5).

   - Na pasku menu wybierz **kompiluj**  > **Kompiluj rozwiązanie** (Ctrl + Shift + B).

     Gdy to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i pliki rozwiązań są kompilowane po uruchomieniu jednego z powyższych poleceń. To pole wyboru jest domyślnie wyczyszczone.

## <a name="to-build-only-the-selected-visual-c-project"></a>Aby skompilować tylko wybrany projekt wizualizacji C++

1. Wybierz projekt [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], a następnie na pasku menu wybierz **kompilacja**, **tylko projekt**i jedno z następujących poleceń:

   - **Tylko kompilacja** *ProjectName*

   - **Kompiluj tylko** *ProjectName*

   - **Wyczyść tylko** *ProjectName*

   - **Tylko link** *ProjectName*

     Te polecenia mają zastosowanie tylko do wybranego projektu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], bez kompilowania, ponownego kompilowania, czyszczenia lub łączenia jakichkolwiek zależności projektu lub plików rozwiązań. W zależności od używanej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **tylko projekt** podmenu może zawierać więcej poleceń.

## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować wiele C++ elementów projektu

1. W **Eksplorator rozwiązań**wybierz wiele plików, które mogą być skompilowanymi akcjami, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz polecenie **Kompiluj**.

     Jeśli pliki mają zależności, pliki zostaną skompilowane w kolejności zależności. Operacja kompilowania zakończy się niepowodzeniem, jeśli pliki wymagają prekompilowanego nagłówka, który nie jest dostępny podczas kompilowania. Operacja Kompiluj używa bieżącej aktywnej konfiguracji rozwiązania.

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

1. Wykonaj jedną z następujących czynności:

    - Na pasku menu wybierz **kompilacja**, **Anuluj**.

    - Naciśnij klawisze Ctrl + Break.

## <a name="see-also"></a>Zobacz także
 [Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md) [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) [Kompilowanie i kompilowanie](../ide/compiling-and-building-in-visual-studio.md) konfiguracji [kompilacji](../ide/understanding-build-configurations.md) [debugowanie i wydanie projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [informacje C/kompilacjaC++ ](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv przełącza](../ide/reference/devenv-command-line-switches.md) [rozwiązania i projekty z](../ide/solutions-and-projects-in-visual-studio.md) wiersza polecenia
