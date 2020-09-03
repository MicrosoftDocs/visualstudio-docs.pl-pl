---
title: 'Instrukcje: kompilowanie wielu konfiguracji'
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7820d56bcb266e8361f36cb5350475f31445800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284765"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Instrukcje: kompilowanie wielu konfiguracji w ramach pojedynczego żądania kompilacji

Można utworzyć większość typów projektów z wieloma lub nawet wszystkimi, ich konfiguracjami kompilacji z jedną akcją IDE przy użyciu okna dialogowego **kompilacja wsadowa** . Nie można jednak skompilować następujących typów projektów w wielu konfiguracjach kompilacji w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Aplikacje skompilowane dla systemu Windows przy użyciu języka JavaScript.

2. Wszystkie projekty Visual Basic.

3. CMake projekty.

Jeśli rozwiązanie zawiera dowolny projekt tych dwóch typów projektów, **kompilacja wsadowa** nie jest dostępna dla tego rozwiązania. W takim przypadku polecenie nie pojawia się w menu **kompilacja** .

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **kompilacje seryjne**. Lub naciśnij **klawisze CTRL** + **Q** , aby otworzyć pole wyszukiwania, a następnie wyszukaj ciąg `Batch Build` .

2. W kolumnie **kompilacja** zaznacz pola wyboru dla konfiguracji, w których chcesz skompilować projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz opcję **Kompiluj**  >  **Configuration Manager** na pasku menu, aby otworzyć okno dialogowe **Configuration Manager** . Po edytowaniu konfiguracji kompilacji dla rozwiązania wybierz przycisk **Skompiluj ponownie** w oknie dialogowym **kompilacja wsadowa** , aby zaktualizować wszystkie konfiguracje kompilacji dla projektów w rozwiązaniu.

3. Wybierz przyciski **Kompiluj** lub **Skompiluj ponownie** , aby skompilować projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)