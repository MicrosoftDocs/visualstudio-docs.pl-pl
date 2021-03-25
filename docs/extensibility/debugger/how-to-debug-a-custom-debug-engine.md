---
title: 'Instrukcje: debugowanie niestandardowego aparatu debugowania | Microsoft Docs'
description: Dowiedz się więcej na temat kroków, które umożliwiają debugowanie niestandardowego aparatu debugowania lub niestandardowego typu projektu przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffd21fb08e920209d47ff66feb436f8a83aab53e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059928"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Instrukcje: debugowanie niestandardowego aparatu debugowania
Typ projektu uruchamia aparat debugowania (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. Oznacza to, że DE jest uruchamiany pod kontrolą wystąpienia kontroli nad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] typem projektu. Jednak to wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie może debugować elementu de. Poniżej przedstawiono kroki, które pozwalają debugować niestandardowe DE.

> [!NOTE]
> : W procedurze "Debugowanie niestandardowego aparatu debugowania" przed dołączeniem do niego musisz poczekać na uruchomienie. Jeśli umieścisz okno komunikatu w najbliższym czasie, który pojawia się po rozpoczęciu, możesz dołączyć do tego punktu, a następnie wyczyścić pole komunikatu, aby kontynuować. Dzięki temu można wychwycić wszystkie zdarzenia.

> [!WARNING]
> Aby wykonać poniższe procedury, musisz mieć zainstalowane zdalne debugowanie. Aby uzyskać szczegółowe informacje, zobacz [zdalne debugowanie](../../debugger/remote-debugging.md) .

## <a name="debug-a-custom-debug-engine"></a>Debugowanie niestandardowego aparatu debugowania

1. Rozpocznij *msvsmon.exe*, Monitor zdalnego debugowania.

2. W menu **Narzędzia** w *msvsmon.exe* wybierz pozycję **Opcje** , aby otworzyć okno dialogowe **Opcje** .

3. Wybierz opcję "bez uwierzytelniania" i kliknij przycisk **OK**.

4. Uruchom wystąpienie programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i Otwórz niestandardowy de Project.

5. Uruchom drugie wystąpienie programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i Otwórz projekt niestandardowy, który uruchamia de (na potrzeby programowania, jest to zwykle w eksperymentalnej gałęzi rejestru, która jest skonfigurowana podczas instalacji programu VSIP).

6. W drugim wystąpieniu programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Załaduj plik źródłowy z projektu niestandardowego i uruchom program w celu debugowania. Poczekaj chwilę na załadowanie, lub poczekaj na trafienie punktu przerwania.

7. W pierwszym wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (z projektem de Project) wybierz pozycję **Dołącz do procesu** z menu **Debuguj** .

8. W oknie dialogowym **Dołącz do procesu** Zmień **transport** na **zdalny (tylko natywny bez uwierzytelniania)**.

9. Zmień **kwalifikator** na nazwę komputera (Uwaga: istnieje historia wpisów, więc musisz wpisać tę nazwę tylko raz).

10. Z listy **dostępne procesy** wybierz wystąpienie, które jest uruchomione, a następnie kliknij przycisk **Dołącz** .

11. Po załadowaniu symboli w miejscu, umieść punkty przerwania w elemencie DE Code.

12. Za każdym razem, gdy zatrzymasz, a następnie ponownie uruchomisz proces debugowania, powtórz kroki od 6 do 10.

## <a name="debug-a-custom-project-type"></a>Debuguj niestandardowy typ projektu

1. Rozpocznij [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w normalnej gałęzi rejestru i Załaduj projekt typu projektu (to jest źródło do typu projektu, a nie wystąpienia typu projektu).

2. Otwórz właściwości projektu i przejdź do strony **debugowanie** . Dla **polecenia** wpisz ścieżkę do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (domyślnie jest to *[dysk]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Dla **argumentów polecenia** wpisz `/rootsuffix exp` dla eksperymentalnej gałęzi rejestru (utworzonej podczas instalowania VSIP).

4. Kliknij przycisk **OK** , aby zaakceptować zmiany.

5. Uruchom typ projektu, naciskając klawisz **F5**. Spowoduje to uruchomienie drugiego wystąpienia programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

6. W tym momencie można umieścić punkty przerwania w kodzie źródłowym typu projektu.

7. W drugim wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , Załaduj lub Utwórz nowe wystąpienie typu projektu. Podczas ładowania lub tworzenia punkty przerwania mogą być trafień.

8. Debuguj typ projektu.

9. W przypadku wybrania debugowania procesu uruchamiania programu a można wykonać kroki opisane w procedurze "Debugowanie niestandardowego aparatu debugowania" w celu dołączenia do programu po jego uruchomieniu. Zapewnia to trzy wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamiania: jeden dla źródła typu projektu, drugi dla typu projektu wystąpienia i trzecią dołączoną do de.

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
