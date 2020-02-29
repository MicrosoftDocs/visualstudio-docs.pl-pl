---
title: 'Instrukcje: kompilowanie wielu konfiguracji jednocześnie'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904090"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Instrukcje: kompilowanie wielu konfiguracji jednocześnie

W tym samym czasie można kompilować większość typów projektów z wieloma lub nawet wszystkimi, z ich konfiguracjami kompilacji, korzystając z okna dialogowego **kompilacja wsadowa** . Nie można jednak skompilować następujących typów projektów w wielu konfiguracjach kompilacji w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Aplikacje skompilowane dla systemu Windows przy użyciu języka JavaScript.

2. Wszystkie projekty Visual Basic.

Jeśli rozwiązanie zawiera dowolny projekt tych dwóch typów projektów, **kompilacja wsadowa** nie jest dostępna dla tego rozwiązania. W takim przypadku polecenie nie pojawia się w menu **kompilacja** .

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz **kompilacja** > **Batch Build**. Lub naciśnij **klawisze Ctrl**+**Q** , aby otworzyć pole wyszukiwania, a następnie wyszukaj ciąg `Batch Build`.

2. W kolumnie **kompilacja** zaznacz pola wyboru dla konfiguracji, w których chcesz skompilować projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz opcję **kompiluj** > **Configuration Manager** na pasku menu, aby otworzyć okno dialogowe **Configuration Manager** . Po edytowaniu konfiguracji kompilacji dla rozwiązania wybierz przycisk **Skompiluj ponownie** w oknie dialogowym **kompilacja wsadowa** , aby zaktualizować wszystkie konfiguracje kompilacji dla projektów w rozwiązaniu.

3. Wybierz przyciski **Kompiluj** lub **Skompiluj ponownie** , aby skompilować projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)