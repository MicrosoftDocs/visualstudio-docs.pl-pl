---
title: 'Instrukcje: Równoczesne kompilowanie wielu konfiguracji'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2edd27174964f1fbddf452a3cb468915d9fc93f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010275"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Instrukcje: Równoczesne kompilowanie wielu konfiguracji

Większość typów projektów z wieloma lub nawet wszystkich ich konfiguracje kompilacji, w tym samym czasie można tworzyć przy użyciu **tworzenie partii** okno dialogowe. Jednak nie można utworzyć następujące typy projektów w wielu konfiguracjach kompilacji, w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje są kompilowane dla Windows przy użyciu języka JavaScript.

2. Wszystkie projekty języka Visual Basic.

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz **kompilacji** > **tworzenie partii**.

2. W **kompilacji** kolumny, zaznacz pola wyboru dla konfiguracji, w których chcesz utworzyć projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz opcję **kompilacji** > **programu Configuration Manager** na pasku menu, aby otworzyć **programu Configuration Manager** okno dialogowe. Po zakończeniu edycji konfigurację kompilacji dla rozwiązania, wybierz **odbudować** znajdujący się w **tworzenie partii** okno dialogowe, aby zaktualizować wszystkie kompilowanie konfiguracji dla projektów w rozwiązaniu.

3. Wybierz **kompilacji** lub **odbudować** przycisków, aby skompilować projekt z konfiguracjami, które można określić.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Tworzenie wielu projektów wykonywane równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)