---
title: 'Instrukcje: debugowanie niestandardowego aparatu debugowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "64797397"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Instrukcje: debugowanie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typ projektu uruchamia aparat debugowania (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. Oznacza to, że DE jest uruchamiany pod kontrolą wystąpienia kontroli nad [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] typem projektu. Jednak to wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie może debugować elementu de. Poniżej przedstawiono kroki, które pozwalają debugować niestandardowe DE.  
  
> [!NOTE]
> : W procedurze "Debugowanie niestandardowego aparatu debugowania" przed dołączeniem do niego musisz poczekać na uruchomienie. Jeśli umieścisz okno komunikatu w najbliższym czasie, który pojawia się po rozpoczęciu, możesz dołączyć do tego punktu, a następnie wyczyścić pole komunikatu, aby kontynuować. Dzięki temu można wychwycić wszystkie zdarzenia.  
  
> [!WARNING]
> Aby wykonać poniższe procedury, musisz mieć zainstalowane zdalne debugowanie. Aby uzyskać szczegółowe informacje, zobacz [zdalne debugowanie](../../debugger/remote-debugging.md) .  
  
### <a name="debugging-a-custom-debug-engine"></a>Debugowanie niestandardowego aparatu debugowania  
  
1. Rozpocznij msvsmon.exe, Monitor zdalnego debugowania.  
  
2. W menu **Narzędzia** w msvsmon.exe wybierz pozycję **Opcje** , aby otworzyć okno dialogowe **Opcje** .  
  
3. Wybierz opcję "bez uwierzytelniania" i kliknij przycisk **OK**.  
  
4. Uruchom wystąpienie programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i Otwórz niestandardowy de Project.  
  
5. Uruchom drugie wystąpienie programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i Otwórz projekt niestandardowy, który uruchamia de (na potrzeby programowania, jest to zwykle w eksperymentalnej gałęzi rejestru, która jest skonfigurowana podczas instalacji programu VSIP).  
  
6. W drugim wystąpieniu programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Załaduj plik źródłowy z projektu niestandardowego i uruchom program w celu debugowania. Poczekaj chwilę na załadowanie, lub poczekaj na trafienie punktu przerwania.  
  
7. W pierwszym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (z projektem de Project) wybierz pozycję **Dołącz do procesu** z menu **Debuguj** .  
  
8. W oknie dialogowym **Dołącz do procesu** Zmień **transport** na **zdalny (tylko natywny bez uwierzytelniania)**.  
  
9. Zmień **kwalifikator** na nazwę komputera (Uwaga: istnieje historia wpisów, więc musisz wpisać tę nazwę tylko raz).  
  
10. Z listy **dostępne procesy** wybierz wystąpienie, które jest uruchomione, a następnie kliknij przycisk **Dołącz** .  
  
11. Po załadowaniu symboli w miejscu, umieść punkty przerwania w elemencie DE Code.  
  
12. Za każdym razem, gdy zatrzymasz, a następnie ponownie uruchomisz proces debugowania, powtórz kroki od 6 do 10.  
  
### <a name="debugging-a-custom-project-type"></a>Debugowanie niestandardowego typu projektu  
  
1. Rozpocznij [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w normalnej gałęzi rejestru i Załaduj projekt typu projektu (to jest źródło do typu projektu, a nie wystąpienia typu projektu).  
  
2. Otwórz właściwości projektu i przejdź do strony **debugowanie** . Dla **polecenia**wpisz ścieżkę do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (domyślnie jest to *[dysk]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Dla **argumentów polecenia**wpisz `/rootsuffix exp` dla eksperymentalnej gałęzi rejestru (utworzonej podczas instalowania VSIP).  
  
4. Kliknij przycisk **OK** , aby zaakceptować zmiany.  
  
5. Uruchom typ projektu, naciskając klawisz F5. Spowoduje to uruchomienie drugiego wystąpienia programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. W tym momencie można umieścić punkty przerwania w kodzie źródłowym typu projektu.  
  
7. W drugim wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , Załaduj lub Utwórz nowe wystąpienie typu projektu. Podczas ładowania lub tworzenia punkty przerwania mogą być trafień.  
  
8. Debuguj typ projektu.  
  
9. W przypadku wybrania debugowania procesu uruchamiania programu a można wykonać kroki opisane w procedurze "Debugowanie niestandardowego aparatu debugowania" w celu dołączenia do programu po jego uruchomieniu. Daje to trzy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchomione wystąpienia: jeden dla źródła typu projektu, drugi dla typu projektu wystąpienia i trzecią dołączoną do de.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
