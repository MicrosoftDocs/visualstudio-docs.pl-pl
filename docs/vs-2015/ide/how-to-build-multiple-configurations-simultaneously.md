---
title: 'Instrukcje: kompilowanie wielu konfiguracji jednocześnie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719b31e834b5410dd137a0c5b69cc07ae01651e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645470"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Poradnik: Równoczesne kompilowanie wielu konfiguracji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym samym czasie można kompilować większość typów projektów z wieloma lub nawet wszystkimi, z ich konfiguracjami kompilacji, korzystając z okna dialogowego **kompilacja wsadowa** . Nie można jednak skompilować następujących typów projektów w wielu konfiguracjach kompilacji w tym samym czasie:

1. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Aplikacje skompilowane dla systemu Windows przy użyciu języka JavaScript.

2. Wszystkie projekty Visual Basic.

   Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).

### <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby skompilować projekt w wielu konfiguracjach kompilacji

1. Na pasku menu wybierz **kompilacja**, **kompilacja wsadowa**.

2. W kolumnie **kompilacja** zaznacz pola wyboru dla konfiguracji, w których chcesz skompilować projekt.

    > [!TIP]
    > Aby edytować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz pozycję **kompilacja**, **Configuration Manager** na pasku menu, aby otworzyć okno dialogowe **Configuration Manager** . Po edytowaniu konfiguracji kompilacji dla rozwiązania wybierz przycisk **Skompiluj ponownie** w oknie dialogowym **kompilacja wsadowa** , aby zaktualizować wszystkie konfiguracje kompilacji dla projektów w rozwiązaniu.

3. Wybierz przyciski **Kompiluj** lub **Skompiluj ponownie** , aby skompilować projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md) [zrozumienie konfiguracji kompilacji](../ide/understanding-build-configurations.md) [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
