---
title: 'Jak: Tworzenie wielu konfiguracji jednocześnie'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904090"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Jak: Tworzenie wielu konfiguracji jednocześnie

Można tworzyć większość typów projektów z wielu lub nawet wszystkie ich konfiguracji kompilacji w tym samym czasie przy użyciu okna dialogowego **kompilacji wsadowej.** Jednak nie można utworzyć następujące typy projektów w wielu konfiguracjach kompilacji w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]aplikacje stworzone dla systemu Windows w języku JavaScript.

2. Wszystkie projekty języka Visual Basic.

Jeśli rozwiązanie zawiera dowolny projekt tych dwóch typów projektów, a następnie **kompilacji wsadowej** nie jest dostępna dla tego rozwiązania. W takim przypadku polecenie nie pojawia się w menu **Kompilacja.**

   Aby uzyskać więcej informacji na temat konfiguracji kompilacji, zobacz [Rozumienie konfiguracji kompilacji](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby utworzyć projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz pozycję **Buduj** > **kompilację wsadowa**. Możesz też **nacisnąć**+klawisz Ctrl**Q,** `Batch Build`aby otworzyć pole wyszukiwania, a następnie wyszukać .

2. W **build** kolumny zaznacz pola wyboru dla konfiguracji, w których chcesz utworzyć projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz pozycję **Build** > **Configuration Manager** na pasku menu, aby otworzyć okno dialogowe Programu Menedżer **konfiguracji.** Po edycji konfiguracji kompilacji dla rozwiązania, wybierz przycisk **Odbuduj** w oknie dialogowym **Kompilacja wsadowa,** aby zaktualizować wszystkie konfiguracje kompilacji dla projektów w rozwiązaniu.

3. Wybierz przyciski **Kompilacja** lub **Odbuduj,** aby utworzyć projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Twórz wiele projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)