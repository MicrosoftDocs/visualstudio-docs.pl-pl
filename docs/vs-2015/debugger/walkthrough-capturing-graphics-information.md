---
title: 'Przewodnik: Przechwytywanie informacji graficznych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebd0453347084d1662c6bc7837fc1e96f498fbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151471"
---
# <a name="walkthrough-capturing-graphics-information"></a>Przewodnik: Przechwytywanie informacji graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Diagnostyka grafiki do ręcznego przechwytywania informacji graficznych z aplikacji Direct3D.  
  
 Ten Instruktaż ilustruje następujące zadania:  
  
- Podłączanie Diagnostyka grafiki do aplikacji  
  
- Przechwytywanie informacji graficznych  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Aby skorzystać z narzędzi Diagnostyka grafiki, musisz najpierw przechwycić informacje o grafice, na których bazują. Aby włączyć funkcję przechwytywania, użyj polecenia **Uruchom diagnostykę** , aby podłączyć Diagnostyka grafiki do aplikacji podczas jej uruchamiania.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Aby włączyć Przechwytywanie informacji graficznych po załadowaniu projektu lub rozwiązania  
  
1. W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Załaduj plik projektu lub rozwiązania dla aplikacji, z której chcesz przechwytywać informacje graficzne.  
  
2. Na pasku narzędzi Diagnostyka grafiki wybierz pozycję **Rozpocznij diagnostykę**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Aby włączyć Przechwytywanie informacji graficznych bez ładowania projektu lub rozwiązania  
  
1. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**. Pojawi się okno dialogowe **Otwórz projekt** .  
  
2. Zamiast pliku projektu lub rozwiązania, określ plik wykonywalny dla aplikacji, z której chcesz przechwytywać informacje graficzne, a następnie wybierz **Otwórz**.  
  
3. Na pasku menu wybierz kolejno opcje **Debuguj**, **grafika**i **Uruchom diagnostykę**.  
  
   Po uruchomieniu aplikacji i wyrenderowaniu ramek można przechwytywać informacje o grafice.  
  
#### <a name="to-capture-graphics-information"></a>Aby przechwycić informacje graficzne  
  
- Na pasku narzędzi Diagnostyka grafiki wybierz przycisk **przechwytywania** . ![Ikona przycisku przechwytywania grafiki](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   -lub-  
  
   Korzystając z aplikacji na ostru, naciśnij przycisk **Print Screen**.  
  
  Za każdym razem, gdy przechwytujesz informacje o ramce, Diagnostyka grafiki rejestruje zdarzenia Direct3D i skojarzonego stanu i dodaje te dane do dziennika grafiki. Nowy dziennik grafiki jest tworzony dla każdej sesji Diagnostyka grafiki. Aby uzyskać informacje na temat dzienników grafiki, zobacz [Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu przedstawiono sposób ręcznego przechwytywania informacji graficznych. W następnym kroku należy wziąć pod uwagę tę opcję:  
  
- Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi Diagnostyka grafiki. Zobacz [Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)
