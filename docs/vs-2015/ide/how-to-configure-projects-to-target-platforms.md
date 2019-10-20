---
title: 'Instrukcje: Konfigurowanie projektów na platformach docelowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668191"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Porady: konfigurowanie projektów do platform docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia skonfigurowanie aplikacji przeznaczonych dla różnych platform, w tym dla platform 64-bitowych. Aby uzyskać więcej informacji o obsłudze platformy 64-bitowego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zobacz [64-bitowe aplikacje](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Kierowanie platform przy użyciu Configuration Manager
 **Configuration Manager** umożliwia szybkie dodanie nowej platformy, która ma być docelowa do projektu. W przypadku wybrania jednej z platform zawartych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] właściwości projektu są modyfikowane w celu skompilowania projektu dla wybranej platformy.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt jako docelowy dla platformy 64-bitowej

1. Na pasku menu wybierz **kompilacja**, **Configuration Manager**.

2. Na liście **Active platformę rozwiązania** Wybierz platformę 64-bitową dla rozwiązania, które ma być celem, a następnie wybierz przycisk **Zamknij** .

   1. Jeśli żądaną platformę nie ma na liście **aktywnych platform rozwiązań** , wybierz pozycję **Nowy**.

        Zostanie wyświetlone okno dialogowe **Nowa platforma rozwiązania** .

   2. Na liście **Typ lub wybierz nową platformę** wybierz pozycję **x64**.

       > [!NOTE]
       > Jeśli podajesz konfigurację nową nazwę, może być konieczne zmodyfikowanie ustawień w **projektancie projektu** , aby wskazać odpowiednią platformę.

   3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz ją, a następnie wybierz przycisk **OK** .

   Wszystkie projekty przeznaczone dla platformy 64-bitowej są aktualizowane, a następna kompilacja projektu zostanie zoptymalizowana dla platform 64-bitowych.

## <a name="targeting-platforms-in-the-project-designer"></a>Kierowanie platform w projektancie projektu
 Projektant projektu umożliwia również ukierunkowanie na różne platformy dla projektu. W przypadku wybrania jednej z platform znajdujących się na liście w **nowej platformie rozwiązania** okno dialogowe nie działa w przypadku Twojego rozwiązania, można utworzyć niestandardową nazwę konfiguracji i zmodyfikować ustawienia w **projektancie projektu** , aby wskazać odpowiednią platformę. .

 Wykonywanie tego zadania różni się w zależności od języka programowania, którego używasz. Aby uzyskać więcej informacji, zobacz następujące linki:

- Aby uzyskać [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, zobacz [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- Aby uzyskać [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty, zobacz [stronę Kompilacja, Projektant projektuC#()](../ide/reference/build-page-project-designer-csharp.md).

- W przypadku projektów [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>Zobacz też
 [Informacje na temat platform kompilacji](../ide/understanding-build-platforms.md) [/platform (C# opcje kompilatora)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64-bitowe aplikacje](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Visual Studio IDE 64-bit support](../ide/visual-studio-ide-64-bit-support.md)
