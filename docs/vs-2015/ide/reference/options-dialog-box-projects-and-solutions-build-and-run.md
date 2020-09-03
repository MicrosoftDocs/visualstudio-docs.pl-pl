---
title: Okno dialogowe Opcje, projekty i rozwiązania, kompilacja i uruchomienie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655188"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym oknie dialogowym można określić maksymalną liczbę projektów Visual C++ lub Visual C#, które mogą być kompilowane w tym samym czasie, niektóre domyślne zachowania kompilacji i niektóre ustawienia dziennika kompilacji. Aby otworzyć okno dialogowe **Opcje** , wybierz **Narzędzia**, **Opcje** na pasku menu. Aby uzyskać dostęp do tego zestawu opcji, rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz polecenie **Kompiluj i uruchom**.

## <a name="uielement-list"></a>Lista elementów UI
 **Maksymalna liczba równoległych kompilacji projektów** Określa maksymalną liczbę projektów Visual C++ i Visual C#, które mogą być kompilowane w tym samym czasie. Aby zoptymalizować proces kompilacji, Maksymalna liczba kompilacji projektów równoległych jest automatycznie ustawiana na liczbę procesorów danego komputera. Wartość maksymalna to 32.

 **Kompiluj tylko projekty startowe i zależności przy uruchomieniu** Tylko projekt startowy i jego zależności są kompilowane, jeśli to pole wyboru jest zaznaczone po wybraniu klawisza F5; Wybierz **Debuguj**, **Rozpocznij** na pasku menu; lub wybierz **kompilację**, **Kompiluj** na pasku menu. Wszystkie projekty, zależności i pliki rozwiązań są kompilowane, jeśli to pole wyboru jest wyczyszczone po naciśnięciu klawisza F5; Wybierz **Debuguj**, **Rozpocznij** na pasku menu; lub wybierz **kompilację**, **Kompiluj** na pasku menu. Domyślnie ta opcja jest wyczyszczona.

 **Przy uruchomieniu, gdy projekty są nieaktualne**
 > [!NOTE]
> Ta lista ma zastosowanie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tylko do projektów.

 Domyślnie komunikat jest wyświetlany, jeśli konfiguracja projektu jest nieaktualna po wybraniu klawisza F5 lub wybraniu opcji **Debuguj**, **Rozpocznij** na pasku menu. Możesz określić, czy chcesz skompilować projekt mimo to, czy komunikat zostanie wyświetlony. Użyj tej opcji, aby określić, czy komunikat ma być wyświetlany i jakie ma być zachowanie kompilacji, jeśli komunikat nie zostanie wyświetlony.

 **Zawsze Kompiluj** Okno komunikatu nie jest wyświetlane, a projekt jest kompilowany pomimo nieaktualnej konfiguracji. Ta opcja jest ustawiana po zaznaczeniu pola wyboru **nie wyświetlaj ponownie tego okna dialogowego** w komunikacie, a następnie wybierz przycisk **tak** .

 **Nigdy nie Kompiluj** Okno komunikatu nie jest wyświetlane i projekt nie został skompilowany. Ta opcja jest ustawiana po zaznaczeniu pola wyboru **nie wyświetlaj ponownie tego okna dialogowego** w komunikacie, a następnie wybierz przycisk **nie** .

 **Monituj o kompilację** Wyświetla okno komunikatu za każdym razem, gdy konfiguracja projektu jest nieaktualna.

 Przy **uruchomieniu, gdy wystąpią błędy kompilacji lub wdrożenia** Jeśli podczas uruchamiania kompilacji z menu **kompilacja** wystąpią błędy kompilacji, zostanie wyświetlony komunikat. Możesz określić, czy chcesz kontynuować, uruchamiając aplikację i czy komunikat pojawia się za każdym razem, gdy wystąpią błędy kompilacji. Użyj tej opcji, aby określić, czy komunikat ma być wyświetlany i jakie ma być zachowanie, jeśli komunikat nie zostanie wyświetlony.

> [!NOTE]
> Ta opcja ma zastosowanie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tylko do projektów.

 **Monituj o uruchomienie** Wyświetla okno komunikatu za każdym razem, gdy wystąpią błędy kompilacji.

 **Nie uruchamiaj** Okno komunikatu nie jest wyświetlane i aplikacja nie jest uruchomiona. Ta opcja jest ustawiana po zaznaczeniu pola wyboru nie **pokazuj tego okna dialogowego ponownie** w polu komunikat, a następnie wybierz przycisk **nie** .

 **Uruchom starą wersję** Okno komunikatu nie jest wyświetlane i nowo utworzona wersja aplikacji nie jest uruchomiona. Ta opcja jest ustawiana po zaznaczeniu pola wyboru **nie pokazuj tego okna dialogowego ponownie** w polu komunikat, a następnie wybierz przycisk **tak** .

 **W przypadku nowych rozwiązań Użyj obecnie wybranego projektu jako projektu startowego** Jeśli to pole wyboru jest zaznaczone, nowe rozwiązania użyją aktualnie wybranego projektu jako projektu startowego.

 **Poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** Określa, ile informacji pojawia się w oknie **danych wyjściowych** kompilacji.

 **Poziom szczegółowości pliku dziennika kompilacji projektu programu MSBuild**
 > [!NOTE]
> Ta opcja dotyczy tylko projektów Visual C++.

 Określa, ile informacji jest zapisywana w pliku dziennika kompilacji, który znajduje się w \\ ... \\ *ProjectName*\debug. \\ *ProjectName*. log.

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
