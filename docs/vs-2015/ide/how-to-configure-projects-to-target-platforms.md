---
title: 'Instrukcje: Konfigurowanie projektów pod kątem platform docelowych | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4cba42203cb5d42e2518d2f1ead7fb998d9b6425
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680640"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Instrukcje: Konfigurowanie projektów pod kątem platform docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umożliwia ustawianie aplikacji przeznaczonych dla różnych platform, w tym platform 64-bitowych. Aby uzyskać więcej informacji na platformie 64-bitowej obsługi w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zobacz [aplikacji 64-bitowych](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Platformy za pomocą programu Configuration Manager  
 **Programu Configuration Manager** umożliwia szybko dodać nową platformę docelową z projektem. Po wybraniu jednej z platform dołączone [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], właściwości projektu są modyfikowane w celu utworzenia projektu dla wybranej platformy.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt przeznaczony dla platformy 64-bitowej  
  
1. Na pasku menu wybierz **kompilacji**, **programu Configuration Manager**.  
  
2. W **aktywną platformą rozwiązania** listy, wybierz platformę 64-bitowych dla rozwiązania do obiektu docelowego, a następnie wybierz **Zamknij** przycisku.  
  
   1. Jeśli nie ma platformy, która ma **aktywną platformą rozwiązania** wybierz **New**.  
  
        **Nowa platforma rozwiązania** pojawi się okno dialogowe.  
  
   2. W **wpisz lub wybierz nową platformę** wybierz **x64**.  
  
       > [!NOTE]
       > Jeśli nadasz konfiguracji nową nazwę, może być konieczne zmodyfikować ustawienia w **projektanta projektu** pod kątem odpowiedniej platformy.  
  
   3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz go, a następnie wybierz **OK** przycisku.  
  
   Właściwości dla wszystkich projektów przeznaczonych dla platformy 64-bitowe są aktualizowane i następnej kompilacji projektu będzie optymalizowany dla platform 64-bitowych.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Platformy w Projektancie projektu  
 W Projektancie projektu umożliwia także przeznaczonych dla różnych platform za pomocą projektu. W przypadku wybrania jednej z platform uwzględnione na liście w **nowa platforma rozwiązania** okno dialogowe nie działa w przypadku rozwiązania, można utworzyć nazwy niestandardowej konfiguracji i zmodyfikować ustawienia w **Projektant projektu**  pod kątem odpowiedniej platformy.  
  
 Wykonanie tego zadania zależy od języka programowania, którego używasz. Skorzystaj z następujących linków, aby uzyskać więcej informacji:  
  
- Aby uzyskać [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów, zobacz [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
- Aby uzyskać [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów, zobacz [Stroka kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
- Aby uzyskać [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektów, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne informacje o platformach kompilacji](../ide/understanding-build-platforms.md)   
 [/ platform (opcje kompilatora C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [Aplikacje 64-bitowe](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
