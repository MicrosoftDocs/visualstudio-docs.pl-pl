---
title: 'Jak: Debugowanie niestandardowego aparatu debugowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738586"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Jak: Debugowanie niestandardowego aparatu debugowania
Typ projektu uruchamia aparat debugowania (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. Oznacza to, że DE jest uruchamiany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pod kontrolą wystąpienia kontrolowania typu projektu. Jednak to wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie można debugować DE. Poniżej przedstawiono kroki, które umożliwiają debugowanie niestandardowego DE.

> [!NOTE]
> : W procedurze "Debugowanie niestandardowego aparatu debugowania" należy poczekać na uruchomienie de, zanim będzie można do niego dołączyć. Jeśli umieścisz okno komunikatu na początku de, który pojawia się po uruchomieniu DE, można dołączyć w tym momencie, a następnie wyczyścić okno komunikatu, aby kontynuować. W ten sposób można złapać wszystkie zdarzenia DE.

> [!WARNING]
> Przed podjęciem następującej próby należy zainstalować debugowanie zdalne. Zobacz [zdalne debugowanie, aby](../../debugger/remote-debugging.md) uzyskać szczegółowe informacje.

## <a name="debug-a-custom-debug-engine"></a>Debugowanie niestandardowego aparatu debugowania

1. Uruchom *program msvsmon.exe*, zdalny monitor debugowania.

2. Z menu **Narzędzia** w *pliku msvsmon.exe*wybierz pozycję **Opcje,** aby otworzyć okno dialogowe **Opcje.**

3. Wybierz opcję "bez uwierzytelniania" i kliknij **przycisk OK**.

4. Uruchom wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i otwórz swój niestandardowy projekt DE.

5. Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i otwórz projekt niestandardowy, który uruchamia DE (dla rozwoju jest to zazwyczaj w gałęzi rejestru eksperymentalnego, który jest skonfigurowany po zainstalowaniu programu VSIP).

6. W tym drugim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wystąpieniu , załadować plik źródłowy z projektu niestandardowego i uruchomić program do debugowania. Poczekaj kilka chwil, aby umożliwić DE załadować, lub poczekaj, aż punkt przerwania zostanie trafiony.

7. W pierwszym wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (z projektem DE) wybierz dołącz do **procesu** z menu **Debugowania.**

8. W oknie dialogowym **Dołączanie do procesu** zmień **transport** na **zdalny (natywny tylko bez uwierzytelniania)**.

9. Zmień **kwalifikator** na nazwę komputera (uwaga: istnieje historia wpisów, więc musisz wpisać tę nazwę tylko raz).

10. Na liście **Dostępne procesy** wybierz wystąpienie uruchomionego de i kliknij przycisk **Dołącz.**

11. Po załadowaniu symboli w de, miejsce punktów przerwania w kodzie DE.

12. Za każdym razem, gdy zatrzymasz, a następnie ponownie uruchomisz proces debugowania, powtórz kroki od 6 do 10.

## <a name="debug-a-custom-project-type"></a>Debugowanie niestandardowego typu projektu

1. Uruchom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w normalnej gałęzi rejestru i załadować projekt typu projektu (jest to źródło do typu projektu, a nie wystąpienia typu projektu).

2. Otwórz właściwości projektu i przejdź do strony **Debugowania.** W polu **Polecenie**wpisz ścieżkę do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (domyślnie jest to *[dysk]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. W przypadku **argumentów polecenia**wpisz `/rootsuffix exp` dla gałęzi rejestru eksperymentalnego (utworzonej po zainstalowaniu programu VSIP).

4. Kliknij **przycisk OK,** aby zaakceptować zmiany.

5. Rozpocznij swój typ projektu, naciskając klawisz **F5**. Spowoduje to uruchomienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]drugiego wystąpienia .

6. W tym momencie można umieścić punkty przerwania w kodzie źródłowym typu projektu.

7. W drugim wystąpieniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować lub utworzyć nowe wystąpienie typu projektu. Podczas ładowania lub tworzenia punkty przerwania mogą zostać trafione.

8. Debuguj typ projektu.

9. Jeśli zdecydujesz się debugować proces uruchamiania DE, można wykonać kroki w procedurze "Debug a custom debug engine", aby dołączyć do de po uruchomieniu. Daje to trzy wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamiania: jeden dla źródła typu projektu, drugi dla typu projektu wystąpienia i trzeci dołączony do de.

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
