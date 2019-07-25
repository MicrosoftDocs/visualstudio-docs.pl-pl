---
title: 'Instrukcje: Równoczesne kompilowanie wielu konfiguracji'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f4abd95c2a37366b4f6dfabe141e6418d23301d
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416761"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Instrukcje: Równoczesne kompilowanie wielu konfiguracji

W tym samym czasie można kompilować większość typów projektów z wieloma lub nawet wszystkimi, z ich konfiguracjami kompilacji, korzystając z okna dialogowego **kompilacja wsadowa** . Nie można jednak skompilować następujących typów projektów w wielu konfiguracjach kompilacji w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]Aplikacje skompilowane dla systemu Windows przy użyciu języka JavaScript.

2. Wszystkie projekty Visual Basic.

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz kolejno opcje **Kompiluj** > **kompilacje seryjne**.

2. W kolumnie **kompilacja** zaznacz pola wyboru dla konfiguracji, w których chcesz skompilować projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz opcję **Kompiluj** > **Configuration Manager** na pasku menu, aby otworzyć okno dialogowe **Configuration Manager** . Po edytowaniu konfiguracji kompilacji dla rozwiązania wybierz przycisk **Skompiluj ponownie** w oknie dialogowym **kompilacja wsadowa** , aby zaktualizować wszystkie konfiguracje kompilacji dla projektów w rozwiązaniu.

3. Wybierz przyciski **Kompiluj** lub **Skompiluj ponownie** , aby skompilować projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)